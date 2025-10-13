---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 05-10-2025 19:57:59
links:
  - "[[Lecture 30042025110449]]"
---
# Mark and sweep
---
## Introduzione
> Per **mark and sweep** si intende una tecnica implementata dai [[Garbage collector|garbage collector]].

## Funzionamento
Funziona in 2 fasi: _mark_ e _sweep_.

### Mark
Questa prima fase di detection utilizza contrassegni per identificare il garbage, in 2 fasi:
1. contrassegna come garbage tutti gli oggetti dell'[[Heap|heap]];
2. percorre lo stack e segna come non garbage tutto cio' che e' raggiungibile da esso, compresi i riferimenti interni all'heap (quindi anche i casi ricorsivi).

### Sweep
E' una visita piatta dell'heap: elimina tutti gli oggetti marcati come garbage.

### Comportamento complessivo
![[mark-and-sweep.png]]

### Osservazioni
E' importante notare che non libera la memoria nel momento stesso in cui diventa garbage, come avviene per la tecnica [[Reference count|reference count]]: viene **invocata dal runtime quando pensa sia necessario**! Per esempio quando l'heap sta esaurendo la memoria disponibile.

Di fatto, viene implementato un meccanismo detto di _stop-the-world_: il garbage collector deve arrestare completamente l'esecuzione del programma prima di fare _mark and sweep_... non e' adatto a programmi che richiedono reattivita' o interattivita'.

## Problemi
La marcatura avviene [[Ricorsione|ricorsivamente]], ovviamente. Ma **se stiamo terminando l'heap, automaticamente significa che stiamo terminando anche lo [[Stack|stack]]**[^1]! Come gestiamo i livelli di ricorsione?

Per fare cio', possiamo usare una tecnica di **inversione dei puntatori**.

### Inversione dei puntatori
Consiste nella codifica dello stack all'interno dei campi gia' esistenti dell'heap. In particolare, sono necessari solo due puntatori: `prev` e `curr`. Specie:
1. `curr` punta all'oggetto in analisi in questo momento;
2. `prev` indica l'oggetto puntato in precedenza;

Quando il garbage collector passa da un'oggetto `A` a uno `B` puntato da `A`:
1. aggiorna `curr` con `&B`;
2. mette il puntatore di `A` verso `B` a `prev`;

Quando invece passa da `B` ad `A`, suo genitore:
1. aggiorna `curr` con `prev`;
2. aggiorna `prev` con il puntatore di `A` verso `B` (che sara' il successivo `prev`);

Inoltre, per evitare loop nelle visite, il raccoglitore marca tutti i puntatori visitati.
![[inversione-puntatori.png]]

## Referenze

[^1]: stack e heap crescono dalle estremita' opposte!
