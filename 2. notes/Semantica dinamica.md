---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 05-10-2024 19:35:43
links:
  - "[[Lecture 26092024120454]]"
  - "[[Lecture 01102024110253]]"
---
# Semantica dinamica
---
## Introduzione
> Per **semantica dinamica**, si intende una rappresentazione formale dell'esecuzione del programma, la quale può mostrare _errori dinamici_ (a _runtime_).

In particolare, questa, consiste nel fornire un _modello matematico che descriva il comportamento del programma_: **la semantica dinamica, infatti, è semplicemente la [[Semantica|semantica]]**.

E' in grado di catturare vincoli semantici dinamici (appunto, errori dinamici), ossia quei vincoli che la [[Semantica statica|semantica statica]] (sintassi contestuale), non è in grado di catturare.

## Utilità
La semantica dinamica serve:
- _al programmatore_
	- per sapere esattamente cosa deve fare il suo programma
	- deve poter dimostrare proprietà del suo programma (es. la terminazione per ogni possibile input)
- _al progettista del linguaggio_
	- strumento di specifica del linguaggio
	- deve poter dimostrare proprietà del linguaggio (es. se è [[Turing-completezza|Turing-completo]])
- _all'implementatore del linguaggio_
	- riferimento per dimostrare la correttezza dell'[[Implementazione|implementazione]]

## Tecniche
Per definire la semantica (dinamica) ci sono due tecniche principali:
- **operazionale** - si costruisce una _specie di automa_, che passo dopo passo mostra l'effetto dell'esecuzione delle varie istruzioni (enfasi sul _come si calcola_);
- **denotazionale** - si associa ad ogni programma sequenziale una funzione da input ad output (enfasi sul _cosa si calcola_);

## Referenze
- [[Semantica operazionale strutturata]]