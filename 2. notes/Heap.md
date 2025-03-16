---
tags:
  - category/note
  - status/finished
  - topic/programmazione
  - topic/linguaggi-di-programmazione
date: 05-11-2023 19:20:43
links:
  - "[[Lecture 03112023110813]]"
  - "[[Lecture 26022025111603]]"
---
# Heap
---
## Definizione
> L'**heap** è quella parte di [[Allocazione dinamica della memoria|memoria]] riservata a un [[Processo|processo]] in esecuzione in cui vengono _allocati nuovi blocchi di memoria_, solitamente quindi [[Strutture dati dinamiche|dati dinamici]].

Lo [[Stack|stack]] non e' sufficiente come meccanismo di [[Allocazione dinamica della memoria|allocazione dinamica della memoria]]: non vogliamo limitarci alla sola politica [[LIFO]], ma essere liberi di allocare memoria dinamica in modo "disordinato". Per esempio, vogliamo poter fare `malloc(A)`, `malloc(B)` e poi `free(A)`, `free(B)`. I blocchi dell'heap devono poter essere allocati e deallocati in momenti arbitrari.

## Implementazione
Le caratteristiche dell'heap devono essere:
- supporto alla [[Frammentazione|deframmentazione]];
- velocita' di accesso.

Il tutto si implementa mediante la cosiddetta [[Lista libera|lista libera]].

## Referenze