---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 05-10-2025 19:39:15
links:
  - "[[Lecture 30042025110449]]"
---
# Reference count
---
## Introduzione
> Il **reference count** e' il modo piu' elementare per realizzare un [[Garbage collector|garbage collector]].

## Funzionamento
Quando si alloca un oggetto nell'[[Heap|heap]], il runtime inizializza un _contatore di riferimenti_ di quell'oggetto, mantenendolo sincronizzato con il numero di puntatori attivi a quell'oggetto.

Quindi, al momento della creazione dell'oggetto, il contatore e' a `1`. Ogni volta che a un puntatore viene assegnato il suo puntatore, il contatore viene incrementato; e diminuisce ogni volta che perde una variabile puntatore (uscita dallo scope oppure riassegnamento).

Quando il contatore arriva a `0` --> _il suo oggetto diventa garbage e viene deallocato dalla memoria_.

### Deallocazione a catena
La deallocazione, in realta', **potrebbe a catena andare a deallocare altri oggetti**, se sono puntati dall'oggetto deallocato!

Pertanto, prima di deallocare l'oggetto, e' necessario **prima visitare l'oggetto e decrementare tutti i contatori a cui fa riferimento, [[Ricorsione|ricorsivamente]]**!

Di conseguenza, questa tecnica _non permette di gestire strutture ricorsive_.

## Referenze