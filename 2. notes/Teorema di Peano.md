---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 16-11-2023 22:03:06
links:
  - "[[Lecture 13112023094129]]"
  - "[[Lecture 17112023134446]]"
---
# Teorema di Peano
---
## Introduzione
> Se si ha una [[Funzione matematica|funzione]] [[Funzioni derivabili|derivabile]] $n$-volte[^1] in $x_{0} = 0$, si definisce **[[Polinomi di Taylor|polinomio di Taylor]]** di $f$ in $x_{0} = 0$ di grado ($\leq$) $n$
> $$T_{n}(x) = \sum\limits_{j = 0}^{n} \frac{f^{(j)}(0)}{j!} x^{j}$$
> e si ha che $T_{n}(x)$ è l'_unico_ polinomio t.c.
> $$f(x) = T_{n}(x) + o(x^{n})$$

La variante per $x_{0} \neq 0$ è
$$T_{n}(x) = \sum\limits_{j = 0}^{n} \frac{f^{(j)}(x_{0})}{j!} (x - x_{0})^{j}$$

## Referenze
- [[Sviluppo in serie di Taylor]]

[^1]: quindi di [[Classe C]] di tipo almeno $C^{n}$