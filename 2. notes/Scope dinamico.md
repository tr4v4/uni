---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 25-02-2025 10:46:31
links:
  - "[[Lecture 20022025131602]]"
---
# Scope dinamico
---
## Introduzione
> Per **scope dinamico** si intende la valutazione dello [[Scope|scope]] degli [[Identificatore|identificatori]] basata sul programma "dinamico" (a _run-time_), e dice che _un [[Nome|nome]] non locale e' risolto nella prima occorrenza del [[Blocco|blocco]] attivato piu' di recente_ (in senso temporale) _e non ancora disattivato_.

![[scope-dinamico.png]]

E' il meno usato, ma piu' semplice da implementare nel [[Compilatore|compilatore]].

## Referenze