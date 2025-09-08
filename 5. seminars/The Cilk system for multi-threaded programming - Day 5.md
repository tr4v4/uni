---
tags:
  - category/seminar
date: 05-09-2025 09:23:53
lecturer: Matteo Frigo
---
# The Cilk system for multi-threaded programming - Day 5
## Concetti
- paralleliziamo programmi sequenziali
- partiamo da il search di un valore in un array
- _parallelismo speculativo_ - avviene quando viene spawnato un del lavoro parallelo che non sarebbe eseguito nella versione sequenziale (con serial-elision)
- esempi
	- **min-max search**
		- non vogliamo generare tutto l'albero (troppa memoria)
		- applichiamo una _static evaluation function_
		- il vecchio consiglio era: mantiena la funzione di valutazione statica semplice, e concentra la computazione nella ricerca più profonda dell'albero
		- ottimizziamolo con branch & bound --> _beta cutoff_
	- **alpha-beta seach** (pruning)
		- è un'estensione del branch & bound sul min-max
		- manteniamo una finestra di upperbound $\beta$ e lowerbound $\alpha$
		- funzionamento
		- il numero di nodi è circa $b^{d}$
		- teorema (KM75): questo ci dice che in realtà con alpha-beta search se si assume di cercare i nodi nel modo migliore possibile, allora questi sono circa $2b^\frac{d}{2}$
		- altro teorema (KM75): sempre in caso di nodi ordinati nel miglior modo possibile, su ogni nodo alpha-beta analizza 1 solo figlio, oppure tutti i $b$ figli
			- allora paralleliziamo!
			- spawno il figlio e aspetto che ritorni (`sync`)
				- se fa cutoff --> basta
				- altrimenti --> spawno gli altri $b-1$ figli in parallelo, poi faccio `sync`
			- conseguenze sul numero di work e span
		- tuttavia _non possiamo sapere l'ordine migliore del game tree in anticipo_!
			- quindi alla fine finisci per sprecare del lavoro
			- 2 tecniche per risolvere il problema
				1. _`abort`_ - se un nodo viene cutoffato, fai `abort` di tutti i tuoi $b-1$ siblings interrompendo di fatto la loro ricerca!
					- il problema è che questo ha a che fare con lo scheduler, l'efficienza dipende da esso
				2. _null-window search_ - fare una ricerca sulla finestra $[\alpha, \alpha+1]$ (quindi in realtà solo su $\alpha$, finestra di grandezza $1$)
					- è una predizione che ti dice se un child sarà utile o no
					- l'algoritmo è detto _scout search_

## Domande

## Referenze