---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 24-10-2024 00:17:37
links:
  - "[[Lecture 17102024091631]]"
---
# Problema della sezione critica
---
## Introduzione
> Il **problema della [[Sezione critica|sezione critica]]** (o **CSP**) consiste nel realizzare $N$ [[Processo|processi]] della forma
> ```R
> process P_i {
> 	while (true) {
> 		[enter cs]
> 		# critical section
> 		[exit cs]
> 		# non-critical section
> 	}
> }
> ```
> tale che valga:
> 1. _[[Mutua esclusione|mutua esclusione]]_ - solo un processo alla volta dev'essere dentro la CS fra tutti quelli che hanno una CS per la stessa risorsa condivisa;
> 2. _assenza di [[Deadlock|deadlock]]_;
> 3. _assenza di [[Starvation|starvation]]_ - ogni processo che lo richiede, prima o poi entra nella CS;
> 4. _assenza di delay non necessari_ - un processo fuori dalla CS non deve ritardare l'ingresso della CS da parte di un altro processo.

## Soluzioni
Esistono diversi [[Algoritmo|algoritmi]] in grado di risolvere il problema:
- [[Algoritmo di Dekker|algoritmo di Dekker]]
- [[Algoritmo di Peterson|algoritmo di Peterson]]

## Referenze