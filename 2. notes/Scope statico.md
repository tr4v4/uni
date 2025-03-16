---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 25-02-2025 10:34:40
links:
  - "[[Lecture 20022025131602]]"
  - "[[Lecture 26022025111603]]"
---
# Scope statico
---
## Introduzione
> Per **scope statico** si intende la valutazione dello [[Scope|scope]] degli [[Identificatore|identificatori]] basata sul programma "statico" (a _compile-time_), e dice che _un [[Nome|nome]] non locale e' risolto nella prima occorrenza del [[Blocco|blocco]] che testualmente lo racchiude_ (nell'[[Ambiente|ambiente]] non locale o globale).
> Come caratteristica fondamentale si ha che quindi lo scope statico e' _indipendente dalla posizione_.

![[scope-statico.png]]

Si tratta dello scope piu' diffuso, ma e' il piu' difficile da implementare nei [[Compilatore|compilatori]].

## Implementazione
Il problema del trovare il primo blocco "contenitore" che racchiude il nome ricercato, e' _equivalente al trovare il [[Record di attivazione|record di attivazione]] nello [[Stack|stack]] di cui si e' "figli"_ (si e' stati invocati) _che contiene la variabile cercata_.

Per fare questo, all'interno di ogni record di attivazione e' presente il campo **link statico**: questo **puntera' al record di attivazione del blocco che contiene il blocco corrente**. L'insieme dei link statici viene detta [[Catena statica|catena statica]].

<u>Nota bene</u>: quindi, _il link statico dipende dalla struttura del programma_, dall'annidamento dei blocchi.

## Referenze