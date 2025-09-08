---
tags:
  - category/seminar
date: 01-09-2025 17:52:33
lecturer: Andrea Lodi
---
# Mixed-Integer Linear Programming
## Concetti
- Branch and Bound (B&B)
	- ma per interi e reali!
	- idea dell'algoritmo
		- risolve il rilassamento sul duale, e non appena coincide con il primale (costruito sugli interi) allora la soluzione è trovata ([[Teorema debole di dualita']])
	- vogliamo però limitare il numero di nodi (esplorazioni) da risolvere in LP (usando il simplesso)
		- ogni nodo è una risoluzione fissata per un certo valore intero di $x$ (primo elemento della coppia è intero, secondo è reale) della sua parte reale, usando la programmazione lineare "standard"
		- il problema non è il numero di nodi, ma l'estensione dell'albero di esplorazione --> rischia di far esplodere i casi di LP
	- grande compromesso: la soluzione dev'essere sofisticata, ma non troppo per far esplodere i casi e quindi spendere tanto tempo nella computazione
	- ogni algoritmo B&B è raggruppabile in 4 blocchi:
		- configuration
			- l'algoritmo prova a restringere il bound delle variabili per trovare delle "zone" che sembrerebbero avere una migliore performance nella ricerca della soluzione
		- cutting plane generation
			- modifichiamo $Ax \leq b$, le disequazioni lineari che delineano lo spazio delle soluzioni, in modo da farle coincidere con il minimo insieme di punti interi che appartengono all'insieme originale di soluzioni
			- lo facciamo aggiungendo altre disequazioni lineari
				- si fa arrotondando per difetto in un modo detto da Gomory
				- per $Ax \leq b$ posso trovare $u$ tale che $uAx \leq \lfloor xb \rfloor$
		- sophisticated branching strategies
			- solito branching...
		- primal heuristic
			- l'euristica considerata migliore si chiama _strong branching_
- e adesso "aumentiamo" il problema con il ML
	- perché
		- perché gli algoritmi usati sono troppo lenti
			- la precisione si paga in tempo
			- le applicazioni richiedono velocità
		- perché gli algoritmi richiedono troppa euristica
			- strong branching sì, ma se vogliamo precisione ci mette tantissimo tempo perché per tanti reali deve fare il simplesso e poi scegliere il migliore
	- l'unione tra ML e CO ha creato una nuova letteratura
		- noi guardiamo una classe di argomenti in particolare
		- metodi di apprendimento
			- _demonstration_/_imitation_
				- vogliamo minimizzare la distanza tra l'azione dell'esperto e del modello
			- _experience_
				- non abbiamo un esperto
				- dall'azione presa dal modello calcoliamo un reward e alleniamo il modello
				- generalmente più complesso da allenare
		- rappresentazione
			- come traduciamo il problema in una rete neurale, per esempio?
			- rete neurale poco usabile
			- la rappresentazione dovrebbe avere 4 proprietà:
				- permutation invariance --> impossibile! se scambi l'ordine delle righe il simplesso cambia origine e tempo di esecuzione
				- scale invariance
				- size invariance
				- low computational cost
			- nella letteratura moderna
				- vettori di grandezza fissata
				- grafo bipartito --> si può facilmente passare alle GNN (Graph Neural Networks)
				- collezione di dati run-time sul B&B tree per capire cosa fare
			- noi guardiamo grafo bipartito
				- modo per passare dalla formulazione matematica del problema al grafo bipartito
				- vogliamo passare ora dal grafo bipartito al GNN
					- metodo...
		- per la prima volta nel 2019 un paper ha mostrato che un metodo di ottimizzazione basato su ML (GNN) ha battuto strong branching
			- tanta roba anche che le GNN possono runnare su GPU, invece i metodi standard sono interamente in CPU

## Domande

## Referenze