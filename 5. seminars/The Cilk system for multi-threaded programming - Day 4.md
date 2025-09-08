---
tags:
  - category/seminar
date: 04-09-2025 09:17:26
lecturer: Matteo Frigo
---
# The Cilk system for multi-threaded programming - Day 4
## Concetti
- cache
	- da CPU a RAM sono circa 200/300 cicli (si potrebbero fare 200/300 addizioni!)
	- ca CPU a cache sono 1/2 cicli
	- idealmente
		- two-level hierarchy
		- grandezza cache $\mathbb{Z}$
		- ogni linea di cache è grande $\mathbb{B}$
		- quindi ci sono $\frac{\mathbb{Z}}{\mathbb{B}}$ linee di cache
		- la cache la pensiamo nel caso migliore, perfetta, in cui contiene sempre ciò che ti serve
	- misure
		- work - $T_{1}$ (solito)
		- cache misses - $Q$
	- assunzioni
		- assumiamo che $\mathbb{B} = 1$, ossia ogni linea è una cella sola
	- policy di rimpiazzamento
		- **optimal replacement policy**[^1] - Belady
			- funzionamento
				- il processore vuole accedere alla locazione $a$
				- se $a$ non è nella cache (_cache miss_)
					- se la cache è piena, togli l'elemento che _verrà acceduto più lontano nel futuro_
					- ora la cache ha lo spazio sufficiente, quindi salva $a$ nella cache
				- se $a$ è nella cache (_cache hit_)
					- restituiscilo
			- problema: come conosco il futuro?[^2]
				- offline vs. online!
		- **[[LRU]]**
			- funzionamento
				- il processore vuole accedere alla locazione $a$
				- se $a$ non è nella cache (_cache miss_)
					- se la cache è piena, togli l'elemento che _è stato acceduto meno recentemente_ (più lontano nel passato, il contrario di Belady!)
					- ora la cache ha lo spazio sufficiente, quindi salva $a$ nella cache
				- se $a$ è nella cache (_cache hit_)
					- restituiscilo
			- implementazioni
				- move-to-front (naive, usando uno stack doppiamente concatenato)
			- teoremi:
				- Sleator-Tarjan: se abbiamo una cache LRU di grandezza $\mathbb{Z}$ e una cache ottimale di grandezza $\frac{\mathbb{Z}}{2}$, allora $$Q(LRU) \leq 2 Q(OPT) + \mathbb{Z}$$
					- notare la grandezza di OPT! ammettiamo che la grandezza della cache di LRU sia 2 volte quella di OPT perché altrimenti non si otterrebbe una competizione effettiva (OPT sarebbe molto meglio)
					- quindi LRU cache è 2-competitive contro optimal cache della metà della grandezza
						- dimostrazione
							- lemma (proprietà fondamentale tra LRU): tra 2 cache misses di una stessa locazione devono esserci almeno $\mathbb{Z}$ accessi a diverse locazioni
								- ovvio, basta guardare l'implementazione move-to-front
							- corollario: in ogni epoca ($\mathbb{Z}$ accessi) LRU fa cache-miss di una locazione al massimo 1 volta; quindi per costruzione le epoche accedono al più a $\mathbb{Z}$ locazioni, quindi $Q(LRU) \leq \mathbb{Z}$
							- lemma: in ogni epoca al tranne l'ultima, $Q(OPT) \geq \frac{\mathbb{Z}}{2}$
							- a questo punto si mettono i due bound insieme e si ottiene il teorema
			- ma in CILK?
				- teorema pazzurdo: le cache si allineano dopo $\mathbb{Z}$ accessi se una parte vuota (usando LRU)
	- cache ideale parallela multiprocessore
		- quando un processore ruba un frame, assumendo che abbia cache vuota, ci metterà al più $\mathbb{Z}$ misses per ottenere la cache del processore da cui ha rubato il frame
			- stessa cosa quando si fa `sync`
		- quindi $Q_{P} \leq Q_{1} + 2L_{P}\mathbb{Z}$, ovvio perché ai cache misses sequenziali ($Q_{1}$) devi aggiungere $2\mathbb{Z}$ cache-misses per ogni steal (uno per steal e uno per sync)
			- inoltre $Q_{P} \leq Q_{1} + O(PT_{\infty}\mathbb{Z})$ vale con alta probabilità, ma bisogna stare attenti: introducendo la cache le cache misses cambiano il numero di steal
	- analisi di cache nella moltiplicazione di matrici
		- è cache oblivious! è ottimale sulla grandezza della cache anche se non la conosce --> è nata un'intera classe di algoritmi di questo tipo

## Domande

## Referenze

[^1]: io lo conosco come [[MIN paginazione]]

[^2]: come [[Algorithms in the Dark]]!
