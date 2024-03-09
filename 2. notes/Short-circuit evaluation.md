---
tags:
  - category/note
  - status/finished
  - topic/programmazione
date: 26-09-2023 09:19:16
links:
  - "[[Lecture 25092023151613]]"
---
# Short-circuit evaluation
---
## Funzionamento
Un'[[Espressione|espressione]], per valutare l'esecuzione degli operatori `&&` ([[AND]]) e `||` ([[OR]]) usa il seguente "algoritmo":
- in `&&` se il primo argomento è `false` il secondo non si valuta --> l'espressione varrà `false`
- in `||` se il primo argomento è `true` il secondo non si valuta --> l'espressione varrà `true`

## Referenze