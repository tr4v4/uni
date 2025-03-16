---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 16-03-2025 15:41:47
links:
  - "[[Lecture 27022025131944]]"
---
# CRT
---
## Introduzione
> La **CRT** (**Central Reference Table**) e' una [[Strutture dati|struttura dati]] usata per implementare lo [[Scope dinamico|scope dinamico]] in modo efficiente.

## Funzionamento
E' il contrario delle [[A-list]]: e' una tabella di variabili, a ognuna delle quali e' associata una pila di blocchi contenenti le sue istanze in ordine di apparizione, tale che _la prima istanza e' la piu' recente_ e _tutte le altre sono nascoste_ (per implementare lo scope dinamico).
![[crt.png]]

<u>Nota bene</u>: l'accesso alla tabella e' costante!

## Miglioramento
Si puo' migliorare la performance usando la **CRT con pila nascosta**.
![[crt-pila-nascosta.png]]

## Referenze