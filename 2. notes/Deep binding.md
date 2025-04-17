---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 05-04-2025 18:25:15
links:
  - "[[Lecture 12032025111631]]"
  - "[[Lecture 19032025113725]]"
---
# Deep binding
---
## Introduzione
> Il **deep binding** e' una delle due regole di valutazione dell'[[Ambiente|ambiente]] delle [[Funzione di ordine superiore|funzioni di ordine superiore]] passate come parametro ad altri funzioni, che _risolve le variabili non locali nell'ambiente al momento del passaggio della funzione alla funzione come parametro attuale_.

In definitiva:
- in caso di [[Scope statico|scope statico]] --> il deep binding si risolve mettendo il puntatore di [[Catena statica|catena statica]] nella [[Chiusura|chiusura]];
- in caso di [[Scope dinamico|scope dinamico]] --> il deep binding si risolve mettendo il puntatore all'ambiente al momento del passaggio della funzione come parametro attuale nella chiusura.

Fondamentalmente il deep binding si implementa nello stesso modo con cui si fa il [[Passaggio per nome|passaggio per nome]].

Fatto sta che di solito il deep binding viene associato allo scope statico.

## Referenze