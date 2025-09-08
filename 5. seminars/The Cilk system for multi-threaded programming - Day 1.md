---
tags:
  - category/seminar
date: 01-09-2025 09:04:53
lecturer: Matteo Frigo
---
# The Cilk system for multi-threaded programming - Day 1
## Concetti
- ancora non si possono parallelizzare funzioni ricorsive
- keywords:
	- `spawn` --> spawna la procedura chiamata in parallelo;
	- `sync` --> aspetta che tutte le procedure spawnate siano terminate;
		- bisogna tenere conto dello scope
		- non si può fare `return` senza un `sync` dopo aver fatto `spawn`
			- il `sync` è implicito - _strictness_
- OpenCilk scaricabile
- domande sul parallelismo
	- l'esecuzione di `fib()` genera un DAG
		- tutto ciò tra uno `spawn` e un `sync` è un nodo
		- il top della funzione fino al primo `spawn` è un nodo
		- `fib(3)`
			- ogni `spawn` genera un altro DAG
			- fino a `fib(1)` o `fib(0)` --> ritorna 1 o 0, singolo nodo
		- alla fine si ottiene proprio un _DAG che rappresenta il parallelismo dell'esecuzione del programma_
		- a questo punto possiamo definire sul DAG:
			- ogni nodo è un'unità di lavoro
			- **Work $T_{1}$** - numero totale di nodi nel DAG
			- **Span $T_{\infty}$** - lunghezza del più lungo cammino nel DAG --> cammino critico
			- **Parallelismo** - $\bar{P} = \frac{T_{1}}{T_{\infty}}$ --> il lavoro sullo span!
		- definizioni sull'esecuzione (non DAG, dipende dallo scheduling!):
			- $P$ numero processori
			- $T_{P}$ tempo di esecuzione su $P$ processori
			- ovviamente $T_{P} \geq \frac{T_{1}}{P}$, e anche $T_{P} \geq T_{\infty}$
		- definizione importante
			- massimo possibile speedup!
			- **Speedup** - $\frac{T_{1}}{T_{P}}$
			- si ha che $$\frac{T_{1}}{T_{P}} \leq \frac{T_{1}}{T_{\infty}} = \bar{P}$$
				- il parallelismo è il massimo possibile speedup che si può ottenere su $P$ processori
	- teoria dello scheduling
		- greedy scheduling
			- _ready notes_ - un nodo del DAG è _ready_ se tutti i suoi predecessori sono stati eseguiti
			- greedy: se ci sono almeno $P$ nodi ready, eseguine qualunque $P$, altrimenti esegui tutti i nodi ready
				- è stupido perché non guarda il futuro, ma fa eseguire tutti i $P$ processori se c'è qualcosa da fare
			- Teorema di Graham (dimostrato da Brent)
				- per ogni greedy schedule si ha $$T_{P} \leq \frac{T_{1}}{P} + T_{\infty}$$
				- $\frac{T_{1}}{P}$ è l'upperbound del numero di step completi, ossia in cui si eseguono esattamente $P$ nodi
				- $T_{\infty}$ è l'upperbound del numero di step incompleto, ossia in cui si eseguono tutti i nodi ready (che sono meno di $P$)
				- quindi l'upperbound del tempo di esecuzione (come il numero totale di step, perché ogni nodo è un'unità di lavoro) sarà la loro somma
			- dal teorema si ottiene che l'_algoritmo greedy ha un fattori di ottimalità pari a 2_
			- nota bene: abbiamo l'upperbound degli algoritmi greedy MA dobbiamo conoscere $T_{1}$ e $T_{\infty}$!
	- analisi di algoritmo paralleli
		- prendiamo in esempio il mergesort
			- sappiamo che $T_{1} = O(n\log{n})$
			- ci manca da calcolare lo span $T_{\infty}$
			- è complicato calcolare il critical path...
				- se in CILK si chiamano due funzioni dentro una funzione `cilk` (senza spawnarle) allora si fa composizione di DAG --> $T_{1} = T_{1}(A) + T_{1}(B)$ e $T_{\infty} = T_{\infty}(A) + T_{\infty}(B)$
				- se invece si fa `spawn` di $A$ e $B$ e poi `sync` allora si parallelizzano i DAG --> $T_{1} = T_{1}(A) + T_{1}(B)$ (ovvio, è sempre additivo), mentre $T_{\infty} = \max(T_{\infty}(A), T_{\infty}(B))$
				- DAG di questo tipo sono chiamati _series-parallel DAGs_ o _fork/join DAGs_
				- CILK consente di fare sono DAG series-parallel
			- esempio con moltiplicazione di matrici
				- alla fine calcoliamo $T_{1}$ e $T_{\infty}$ come equazione di ricorrenza, e quindi usando il master theorem
	- processori super-scalari
		- chiaramente vogliamo cercare di scrivere programmi che cerchino di minimizzare il critical-path, per massimizzare il parallelismo (con $P > 1$ processori)
- domande
	- algoritmi migliori di greedy per massimizzare il numero di step completi?
		- sì ma non generali, dipendono dal DAG e da $P$

## Domande

## Referenze