---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 04-05-2025 18:33:37
links:
  - "[[Lecture 04042025092728]]"
---
# Disk scheduling
---
## Introduzione
> Il **disk scheduling** e' una classe di [[Algoritmo|algoritmi]] di [[Scheduling|scheduling]] utilizzati per gestire le richieste pendenti di un [[HD]] in modo da minimizzare le _seek_, ossia le operazioni che richiedono piu' tempo.

## Algoritmi
Gli algoritmi di disk scheduling piu' comuni sono:
- [[FCFS]], non minimizza il numero di seek ma non puo' mai generare [[Starvation|starvation]] (e' una politica di gestione fair);
- [[SSTF]];
- [[LOOK]];
- [[C-LOOK]].

## Referenze