---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 25-02-2025 10:34:40
links:
  - "[[Lecture 20022025131602]]"
---
# Scope statico
---
## Introduzione
> Per **scope statico** si intende la valutazione dello [[Scope|scope]] degli [[Identificatore|identificatori]] basata sul programma "statico" (a _compile-time_), e dice che _un [[Nome|nome]] non locale e' risolto nella prima occorrenza del [[Blocco|blocco]] che testualmente lo racchiude_ (nell'[[Ambiente|ambiente]] non locale o globale).
> Come caratteristica fondamentale si ha che quindi lo scope statico e' _indipendente dalla posizione_.

![[scope-statico.png]]

Si tratta dello scope piu' diffuso, ma e' il piu' difficile da implementare nei [[Compilatore|compilatori]].

## Referenze