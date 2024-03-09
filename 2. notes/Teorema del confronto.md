---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 15-10-2023 15:14:58
links:
  - "[[Lecture 13102023133536]]"
---
# Teorema del confronto
---
## Introduzione
$$
\begin{align}
f, g, h: A \to \mathbb{R}, \ x_{0} \in D(A) \text{ (punto di accumulazione del dominio)} \\
\lim_{x \to x_{0}} g(x) = \lim_{x \to x_{0}} h(x) = l \in \mathbb{R} \\
\exists \delta > 0 : g(x) \leq f(x) \leq h(x), \ \forall x \in [A \cap I_{\delta}(x_{0})] \setminus \{x_{0}\} \\
\implies \\
\lim_{x \to x_{0}} f(x) = l
\end{align}
$$

> Il **teorema del confronto**, anche chiamato _teorema dei due carabinieri_, ci dice che se una funzione $f(x)$ si trova in mezzo tra due funzioni $g(x)$ e $h(x)$, e per un punto $x_{0}$ queste due funzioni hanno lo stesso limite $l$, allora anche $f(x)$ per $x_{0}$ avrà lo stesso limite $l$.

![[teorema-dei-due-carabinieri.jpg]]

## Referenze