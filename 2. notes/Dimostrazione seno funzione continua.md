---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 21-10-2023 14:48:50
links:
  - "[[Lecture 20102023135306]]"
---
# Dimostrazione seno funzione continua
---
## Dimostrazione
Per dimostrare che $\sin(x)$ è continua in ogni suo punto $x_{0}$, vogliamo dimostrare
$$\lim_{x \to x_{0}} \sin(x) = \sin(x_{0})$$

Possiamo scrivere $\sin(x)$ come $\sin(x_{0} + (x - x_{0}))$, in quanto equivalenti: calcoliamo il valore di $x_{0}$ a una distanza $h = (x-x_{0})$.

Ora, se $x \to x_{0}$, allora si può dire che $h \to 0$. Riscriviamo allora il limite come
$$\lim_{h \to 0} \sin(x_{0} + h) = \sin(x_{0})$$

Dalle [[Formule trigonometriche|formule trigonometriche]] sappiamo che
$$\sin(x_{0} + h) = \sin(x_{0})\cdot\cos(h) + \cos(x_{0})\cdot\sin(h)$$

Per $h \to 0$ avremo allora:
- $\cos(h) = 1$
- $\sin(h) = 0$

per il quale rimarrà quindi solo
$$\lim_{h \to 0} \sin(x_{0} + h) = \sin(x_{0})$$

**Qed**.

## Referenze