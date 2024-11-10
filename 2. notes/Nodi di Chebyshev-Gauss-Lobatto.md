---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 10-11-2024 15:10:14
links:
  - "[[Lecture 21102024132104]]"
---
# Nodi di Chebyshev-Gauss-Lobatto
---
## Introduzione
> Per **nodi di Chebyshev-Gauss-Lobatto** si intende una distribuzione di punti in un certo intervallo $[a, b]$ tale per cui per il numero di nodi $n \to +\infty$ si verifica una convergenza dell'errore $E(x)$ a 0 del polinomio [[Interpolazione|interpolatore]] $p(x)$ rispetto alla funzione originaria $f(x)$.

## Distribuzione
La distribuzione dei nodi segue la seguente formula:
$$x_{i} = \frac{a+b}{2} - \frac{b-a}{2} \cos\left(\frac{\pi i}{n}\right) \ \ \ i = 0, \cdots, n$$

## Referenze