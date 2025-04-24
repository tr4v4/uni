---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 21-04-2025 14:01:42
links:
  - "[[Lecture 09042025091244]]"
---
# Problema di accoppiamento di massima cardinalita'
---
## Introduzione
> Il **problema di accoppiamento di massima cardinalita'** consiste nel [[Problema di accoppiamento|problema di accoppiamento]] di cui si vuole _massimizzare la [[Cardinalità|cardinalita']] di $M$ mantenendo il vincolo degli archi sul fatto che non devono avere nodi in comune_.

## Idea
Possiamo vedere questo problema come un caso particolare del [[Problema del flusso massimo|flusso massimo]] in cui:
- le sorgenti sono i nodi in $O$ e i pozzi i nodi i $D$;
- le capacita' sono tutte pari a 1;
- i flussi sono interi.

Sappiamo intanto di poter sempre passare a un problema con una sola sorgente e un solo pozzo aggiungendo archi fittizi.

La _corrispondenza biunivoca con i problemi del flusso massimo_ si ha nella seguente interpretazione: il flusso su ogni arco puo' essere 0 o 1; se e' 0 allora quell'arco non apparterra' ad $M$, altrimenti si'.

Possiamo allora usare gli algoritmi studiati per risolvere il problema!

## Proprieta'
Tuttavia, per costruzione, questi problemi sono piu' semplici dei generali problemi del flusso massimo. Infatti e' possibile notare che:
- i cammini aumentanti saranno alternanti, ossia costituiti da un arco interno, poi uno esterno, di nuovo interno, e cosi' via;
- i cammini aumentanti partiranno sempre da un nodo esposto e arriveranno sempre in un nodo esposto.

In altre parole, se $P_{E} = P \setminus M$ e $P_{I} = P \cap M$ sono rispettivamente gli archi esterni e interni di un cammino aumentante $P$, allora $$|P_{E}| - |P_{I}| = 1$$
Infatti, partendo da un nodo esposto, per arrivare al pozzo $t$ sara' necessario sempre attraversare un arco esterno in piu'!

Inoltre, si osserva come la capacita' residua $\theta(M, P)$ di ogni cammino aumentante, sara' sempre 1. Di conseguenza
$$M \oplus \theta(M, P)P = (M \setminus P_{I}) \cup P_{E}$$

Questo e' ovvio: in un cammino $P$ si attraversano archi concordi e discordi, ma essendo la capacita' residua sempre 1 (e la capacita' di ogni arco 1), allora gli archi attraversati concordi assumeranno valore 1, mentre quelli discordi torneranno a 0. Gli archi concordi corrispondono con quelli esterni $P_{E}$, mentre quelli discordi sono quelli interni ad $M$, e quindi $P_{I}$. In altre parole _gli archi attraversati che gia' facevano parte di $M$ non ne faranno piu' parte, mentre quelli nuovi ci entreranno_.

### Complessita'
Possiamo usare quindi direttamente [[Algoritmo di Ford-Fulkerson|Ford-Fulkerson]], ma riducendo la ricerca del cammino a una semplice visita.

La [[Complessità computazionale|complessita' computazionale]] di $FF$ sarebbe $O(mnU)$ dove
$$U = \max \{u_{ij} | (i, j) \in A\}$$

ma avendo $u_{ij} = 1 \ \ \ \forall (i, j) \in A$, allora la complessita' dell'algoritmo applicato a questo problema diventa
$$O(mn)$$

## Referenze
