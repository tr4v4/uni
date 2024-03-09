---
tags:
  - "#category/note"
  - "#status/finished"
  - topic/programmazione
  - topic/architettura-degli-elaboratori
date: 19-09-2023 09:43:09
links:
  - "[[Lecture 18092023150410]]"
  - "[[Lecture 25102023150405]]"
  - "[[Lecture 22112023151203]]"
---
# Workflow di compilazione
---
## Processi
I processi consistono in:
1. il [[Compilatore|compilatore]] traduce il linguaggio ad alto livello in linguaggio oggetto (_source code_ --> _object code_), ovvero [[Assembly|assembly]]
2. il [[Linker|linker]] unisce al codice compilato il codice oggetto delle librerie importate
3. il computer (e in particolare l'[[Assemblatore|assemblatore]]) traduce il codice oggetto in codice macchina (in [[Codice binario|binario]]) e lo esegue (con il [[Loader|loader]])

### Schema
![[compilazione-ed-esecuzione-programma.png]]

![[traduzione.png]]

## Tipologie
- [[Compilazione diretta]]
- [[Compilazione a 2 livelli]]

## Referenze