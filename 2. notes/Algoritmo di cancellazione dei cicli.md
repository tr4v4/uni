---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 21-04-2025 13:23:28
links:
  - "[[Lecture 20032025131726]]"
---
# Algoritmo di cancellazione dei cicli
---
## Introduzione
> L'**algoritmo di cancellazione dei cicli** e' un [[Algoritmo|algoritmo]] per risolvere il [[Problema del flusso di costo minimo|problema del flusso di costo minimo]] che consiste nel partire da un flusso ammissibile, e poi di cancellare cicli di costo negativo di volta in volta per ottenere il flusso minimo.

## Algoritmo
1. se `FlussoAmmissibile(G)` restituisce un flusso ammissibile, allora mettilo in $x$, altrimenti termina: il problema e' vuoto;
2. cerca un ciclo di costo negativo  in $G_{x}$; se non lo trovi allora termina e restituisci $x$, altrimenti metti il ciclo in $C$;
3. $x = x(C, \theta(C, x))$;
4. torna al punto 2.

### Funzionamento
Per trovare un flusso ammissibile iniziale, a partire da un generico grafo
![[cancellazione-cicli-1.png]]

e' sufficiente risolvere il [[Problema del flusso massimo|problema del flusso massimo]] sul grafo ottenuto aggiungendo due archi fittizzi $s$ e $t$ nel seguente modo:
![[cancellazione-cicli-2.png]]

Infatti, se il problema non e' vuoto, gli archi fittizzi saranno sicuramente saturati, e il flusso massimo trovato corrispondera' a un flusso ammissibile della rete di partenza.

A questo punto, l'algoritmo si concentra sul trovare cicli di costo negativo e nell'aggiornare di conseguenza il flusso mantenendo l'ammissibilita' ma diminuendone il costo. Infatti, per [[Problema del flusso di costo minimo#Lemma|questo lemma]], il flusso non sara' minimale finche' ci saranno cicli aumentanti di costo negativo.

## Correttezza
La correttezza e' triviale: eliminando cicli di costo negativo, si giungera' a un flusso minimale.

## Terminazione
Se si assume che le capacita' $u$ siano intere, allora il costo diminuira' di almeno 1 ad ogni iterazione. Ci e' sufficiente allora trovare un upperbound al costo di qualunque flusso ammissibile.

Si ha in particolare che
$$-A\bar{u}\bar{c} \leq \text{costo flusso ammissibile} \leq A \bar{u} \bar{c}$$
dove:
- $\bar{u} = \max\{u_{ij} | (i, j) \in A\}$
- $\bar{c} = \max\{c_{ij} | (i, j) \in A\}$

Di conseguenza, la [[Complessità computazionale|complessita' computazionale]] dell'algoritmo sara'
$$O(NA) \cdot O(A\bar{u}\bar{c}) = O(NA^{2} \bar{u} \bar{c})$$

## Referenze
- notare come nell'[[Algoritmo dei cammini minimi successivi|algoritmo dei cammini minimi successivi]] ad ogni iterazione diminuiva lo sbilanciamento $g(x)$, mentre in questo caso e' il costo a diminuire!