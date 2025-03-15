---
tags:
  - category/note
  - status/finished
  - topic/programmazione
  - topic/linguaggi-di-programmazione
date: 05-11-2023 19:17:42
links:
  - "[[Lecture 03112023110813]]"
  - "[[Lecture 20022025131602]]"
---
# Allocazione dinamica della memoria
---
## Introduzione
> Per **allocazione dinamica della memoria** si intende il meccanismo di allocazione della [[Memorie|memoria]] per il quale questa viene allocata a _run-time_.

In modo particolare, comprende [[Stack|stack]] e [[Heap|heap]].
Ricordiamo, infatti che la [[RAM]] alloca a ogni [[Processo|processo]] in esecuzione un certo spazio diviso in 4 principali sezioni:
- _stack_
- _heap_
- _data_
- _text_/_code_

come in figura
![[memory-layout-c-program.png]]

## Referenze