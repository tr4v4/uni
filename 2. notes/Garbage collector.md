---
tags:
  - category/note
  - status/finished
  - topic/algoritmi-e-strutture-dati
  - topic/linguaggi-di-programmazione
date: 10-03-2024 22:53:40
links:
  - "[[Lecture 07032024091439]]"
  - "[[Lecture 30042025110449]]"
---
# Garbage collector
---
## Introduzione
> Il **garbage collector** è un [[Thread|thread]] che viene automaticamente avviato al momento dell'esecuzione di un programma [[Java]] che _si occupa periodicamente di deallocare tutte le celle in [[Heap|heap]] che non sono puntate da alcun puntatore_.

## Operazioni
Le operazioni di un garbage collector sono:
- garbage detection - rilevare se gli oggetti in memoria sono in uso o meno;
- [[Garbage collection|garbage collection]] - rilasciare la memoria occupata dagli oggetti inutilizzati.

Sono spesso eseguite in stretta successione temporale.

## Metodologie
Tra le piu' comuni metodologie adottate dai garbage collector ritroviamo:
- [[Reference count|reference count]];
- [[Mark and sweep|mark and sweep]];
- [[Stop and copy|stop and copy]];

## Referenze