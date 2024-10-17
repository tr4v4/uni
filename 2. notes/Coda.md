---
tags:
  - category/note
  - status/finished
  - topic/algoritmi-e-strutture-dati
date: 12-03-2024 18:13:46
links:
  - "[[Lecture 11032024094827]]"
---
# Coda
---
## Introduzione
> La **coda** è una [[Strutture dati|struttura dati]] [[Strutture dati elementari|elementare]] basata sul modello [[FIFO]] che supporta due operazioni: `ENQUEUE` e `DEQUEUE`. Viene utilizzata per esempio nello [[Scheduling|scheduling]] dei processi nei [[Sistema operativo|sistemi operativi]], o nella visita [[BFS|breadth-first-search]] su [[Grafo|grafi]].

## Implementazioni
### [[Lista|Liste]] concatenate circolari
Si può implementare una coda attraverso liste concatenate circolari, e ciò comporta i seguenti vantaggi e svantaggi:
- _pro_: dimensione illimitata
- _con_: overhead di memoria (addirittura 2 [[Puntatori|puntatori]])

### Liste concatenate semplici con puntatore a testa e a coda
Anche in questo casi i vantaggi e gli svantaggi sono simili a quelli delle liste circolari, con l'unica differenza che non c'è overhead.

### [[Array]] circolari
L'opzione che andiamo ad analizzare però è con gli array circolari. Bisogna stare attenti ad una serie di aspetti, tra cui l'operatore `%`[^1] per permettere la visita circolare dell'array.
![[enqueue-array.png]]
![[dequeue-array.png]]

E' addirittura possibile implementare questa soluzione con un array circolare dinamico. Ma bisogna fare particolare _attenzione durante la fase di ridimensionamento dell'array per mantenere l'ordine degli elementi_: _bisogna prima copiare a partire da head, e poi da tail_.

## Referenze
[^1]: il modulo