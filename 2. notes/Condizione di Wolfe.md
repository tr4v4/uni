---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 10-11-2024 17:00:14
links:
  - "[[Lecture 22102024092339]]"
---
# Condizione di Wolfe
---
## Introduzione
> Le **condizioni di Wolfe** sono un teorema del [[Metodo di discesa del gradiente|metodo di discesa del gradiente]] che ci dice che questo converge a un punto stazionario $x^{*}$ se per ogni $k \in \mathbb{N}$, il _learning-rate_ $\alpha_{k}$ soddisfa le seguenti condizioni (appunto di Wolfe):
> $$\begin{cases} f(x_{k} - \alpha_{k} \nabla f(x_{k})) \leq f(x_{k}) - c_{1}\alpha_{k} {\|\nabla f(x_{k})\|_{2}}^{2} \\ \nabla f(x_{k})^{T} \nabla f(x_{k} - \alpha_{k} \nabla f(x_{k})) \leq c_{2} {\|\nabla f(x_{k})\|_{2}}^{2} \end{cases}$$
> dove $0 < c_{1} < c_{2} < 1$ sono due costanti. La prima condizione è nota come [[Condizione di Armijo|condizione di Armijo]], e richiede che $f(x_{k+1})$ comporti una decrescita sufficientemente alta di $f(x_{k})$.

## Referenze