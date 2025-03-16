---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 16-03-2025 13:10:26
links:
  - "[[Lecture 26022025111603]]"
---
# Fibonacci system
---
## Introduzione
> Il **Fibonacci system** e' un'implementazione delle [[Liste libere multiple|liste libere multiple]] dinamiche che prevede che la lista $k$ contenga blocchi di dimensione $F(k)$, dove $F(k)$ e' l'$k$-esimo numero di Fibonacci.

La differenza fondamentale con il [[Buddy system|buddy system]], quindi, sta nella _crescita delle dimensioni dei blocchi delle liste libere_: nel buddy system, la dimensione di un blocco e' $2^{k}$, mentre nel Fibonacci system e' $F(k)$. Questa tecnica _potrebbe essere considerata migliore perche' il buddy system puo' peggiorare il problema della frammentazione interna_.

## Referenze