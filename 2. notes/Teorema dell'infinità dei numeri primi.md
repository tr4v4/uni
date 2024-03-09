---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 29-09-2023 10:03:28
links:
  - "[[Lecture 25092023093433]]"
---
# Teorema dell'infinità dei numeri primi
---
## Introduzione
Dimostriamo [[Dimostrazione per assurdo|per assurdo]] che i _numeri primi_ siano finiti, per cui
$$p_{1}, p_{2}, p_{3}, ... , p_{n}$$
Ora creo un numero $m$ tale che
$$m := (p_{1} \cdot p_{2} \cdot p_{3} \cdot ... \cdot p_{n}) + 1$$
per cui
$$m > p_{n}$$
e quindi **$m$ non è primo**.
Provando ora a dividere $m$ per $p_{1}$
$$\frac{m}{p_{1}} = (p_{2} \cdot p_{3} \cdot ... \cdot p_{n}) + 1$$
otteniamo come resto 1.
Se facciamo la stessa cosa per $p_{2}$
$$\frac{m}{p_{2}} = (p_{1} \cdot p_{3} \cdot ... \cdot p_{n}) + 1$$
otteniamo sempre come resto 1.
E così per ogni numero primo esistente. Ciò significa che **$m$ non è divisibile per nessun numero primo**, e che perciò **$m$ è primo**. Assurdo, perché abbiamo supposto che $m$ non potesse esserlo.

## Referenze