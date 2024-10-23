---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 23-10-2024 23:52:13
links:
  - "[[Lecture 17102024091631]]"
---
# Azione atomica
---
## Introduzione
> Un'**azione atomica** sono _istruzioni che vengono eseguite in modo indivisibile_.

Nel caso del _parallelismo reale_ ([[Multiprocessing|multiprocessing]] e [[Distributed processing|distributed processing]]) viene garantito che l'azione non interferisca con altri processi durante la sua esecuzione.

Nel _parallelismo apparente_ ([[Multiprogramming|multiprogramming]]) l'avvicendamento dei processi avviene prima o dopo l'azione, che quindi non può interferire con essa.

## Linguaggio macchina
Le singole istruzioni del [[Assembly|linguaggio macchina]] sono azioni atomiche:
- nel _parallelismo reale_ la _politica di arbitraggio del bus_ garantisce che una delle due venga servita per prima e l'altra successivamente;
- nel _parallelismo apparente_ l'[[Interrupt|interrupt]] viene eseguito prima o dopo un'istruzione, mai durante;

### In C
In genere _sequenze di singole istruzioni del linguaggio macchina non sono considerate atomiche_. Mentre per istruzioni di linguaggi di più alto livello può dipendere.

Per esempio in [[C]] vale che:
- `a = 0`, con `a` di tipo `int`, è normalmente un'azione atomica;
- `a = 0`, con `a` di tipo `long long`, invece non è atomico --> nei processori [[CISC e RISC|RISC]] bisogna assegnare 0 nella parte alta e nella parte bassa del registro, si tratta quindi di due istruzioni;

## Referenze