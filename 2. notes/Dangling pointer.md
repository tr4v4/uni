---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 05-10-2025 18:45:09
links:
  - "[[Lecture 30042025110449]]"
---
# Dangling pointer
---
## Introduzione
Sappiamo che i _puntatori dangling_, o anche _wild_, possono portare a comportamenti inaspettati del programma. Vogliamo cercare di risolvere questo problema.

Notiamo che i puntatori wild sono facili da individuare: basta osservare gli accessi a variabili non inizializzate. I dangling invece no! Bisogna per loro _ragionare su tutte le possibili combinazioni di codice in cui passano i valori dei puntatori_.

## Tecniche
Tra le tecniche per la gestione dei riferimenti dangling ci sono:
- [[Tombstones|tombstones]];
- [[Lock and keys|lock and keys]];

## Referenze