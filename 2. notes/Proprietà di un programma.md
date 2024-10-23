---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 23-10-2024 23:24:40
links:
  - "[[Lecture 17102024091631]]"
---
# Proprietà di un programma
---
## Introduzione
> Una **proprietà** di un [[Programma|programma]] ([[Concorrenza|concorrente]]) è un _attributo che rimane vero per ogni possibile esecuzione del programma stesso_.

## Tipologie
Le proprietà di un programma (sempre concorrente) si raccolgono in queste due macro-proprietò fondamentali:
- [[Proprietà safety|safety]]
- [[Proprietà liveness|liveness]]

Se nei programmi sequenziali le due proprietà si possono riassumere in:
- safety = correttezza dello stato finale,
- liveness = terminazione del programma,

nella programmazione concorrente, invece, significano:
- _safety_ = _i [[Processo|processi]] non devono interferire tra di loro nell'accesso alle risorse condivise_ (per quelli che le condividono) --> servono meccanismi di sincronizzazione per eliminare le [[Race condition|race condition]];
- _liveness_ = _i meccanismi di sincronizzazione usati non devono prevenire l'avanzamento del programma_ --> un processo non può attendere un tempo indefinito prima di poter accedere ad una risorsa condivisa.

## Referenze