---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
date: 14-10-2023 15:26:12
links:
  - "[[Lecture 11102023151203]]"
---
# Half-adder
---
## Introduzione
Se vogliamo fare la somma tra 2 bit ci basta prendere l'eventuale tabella di verità per scoprire che si tratta in realtà di una combinazione di [[Porte logiche|porte logiche]] base.

| A   | B   | sum | carry |
| --- | --- | --- | ----- |
| 0   | 0   | 0   | 0     |
| 0   | 1   | 1   | 0     |
| 1   | 0   | 1   | 0     |
| 1   | 1   | 0   | 1     |

Notiamo infatti come `sum` corrisponda a uno [[XOR]], mentre `carry` a un [[AND]]. Da questa osservazione nasce l'**half-adder**.

## Implementazione
![[half-adder.png]]

## Referenze