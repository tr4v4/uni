---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 19-10-2023 20:40:17
links:
  - "[[Lecture 16102023093744]]"
---
# Tipologie di limite di funzione
---
## Introduzione
I [[Limite di funzione|limiti di funzione]] si dividono in **15 casi totali**, a seconda delle possibili combinazioni di _tendenze_ e di (appunto) _limiti_ delle funzioni.

In particolare, un qualunque limite si definisce
$$\stackrel{\lim}{\stackrel{x \to x_{0}}{\stackrel{x \to x_{0}^{+}}{\stackrel{x \to x_{0}^{-}}{\stackrel{x \to +\infty}{\stackrel{x \to -\infty}{}}}}}} f(x) = \begin{cases} l \in \mathbb{R} \\ +\infty \\ -\infty \end{cases}$$
se e solo se
$$\forall \epsilon > 0, \exists \delta > 0 : \forall x \in D:
\begin{cases}
0 < |x - x_{0}| < \delta \\
x_{0} < x < x_{0} + \delta \\
x_{0} - \delta < x < x_{0} \\
x > \delta \\
x < -\delta
\end{cases}
\implies
\begin{cases}
|f(x) - l| < \epsilon \\
f(x) > \epsilon \\
f(x) < -\epsilon
\end{cases}
$$

Questa definizione generale comprende quindi:
- [[Limite al finito di funzione]]
- [[Limite all'infinito di funzione]]

## Referenze