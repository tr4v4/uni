---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 15-03-2025 19:52:14
links:
  - "[[Lecture 06032025151956]]"
---
# FCFS
---
## Introduzione
> L'[[FCFS]] (**First Come, First Served**) e' un [[Algoritmo|algoritmo]] di [[Scheduling|scheduling]] _non-preemptive_, _semplice_, _implementato tramite una [[Coda|coda]]_ ([[FIFO]]). Prevede che _il [[Processo|processo]] che arrivi per primo venga servito per primo_.

Per sua natura, questo algoritmo prevede:
- _elevati tempi medi di attesa_;
- _elevati tempi di turnaround_;
- _i processi CPU bound ritardano i processi I/O bound_ --> [[Convoy effect|convoy effect]];

![[convoy-effect.png]]

## Referenze