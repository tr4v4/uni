---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 16-03-2025 15:31:58
links:
  - "[[Lecture 27022025131944]]"
---
# A-list
---
## Introduzione
> L'**A-list** e' una [[Lista|lista]] usata per implementare lo [[Scope dinamico|scope dinamico]].

## Funzionamento
Consiste in una pila che astrae i record di attivazione, in cui ogni elemento e' costituito dalla variabile e da alcune sue informazioni. Quindi, le variabili messe a pila implementano automaticamente lo shadowing sulla base dello scope dinamico.
![[a-list.png]]

E' molto semplice da implementare, ma i _costi di accesso sono lineari rispetto al numeri di variabili_. Per questo di solito e' preferibile usare la [[CRT]].

## Referenze