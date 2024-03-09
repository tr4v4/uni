---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 15-10-2023 15:03:06
links:
  - "[[Lecture 13102023133536]]"
---
# Teorema di permanenza del segno
---
## Introduzione
$$
\begin{align}
f: A \to \mathbb{R}, \ \bar{x} \in D(A) \text{ (insieme dei punti di accumulazione)} \\
\lim_{x \to \bar{x}} f(x) = l \in \mathbb{R}, \ l > 0 \\
\implies \\
\exists \delta > 0 : \forall x \in A, \ 0 < |x - \bar{x}| < \delta \implies f(x)>0
\end{align}
$$

Il **teorema di permanenza del segno** ci dice che se il [[Limite finito al finito di funzione|limite di una funzione per un punto]] tende a $l > 0$ e il punto $\bar{x}$ è un [[Punto di accumulazione|punto di accumulazione]] del dominio, allora per ogni punto nell'intervallo $\delta$ di $\bar{x}$ diverso da $\bar{x}$ anche $f(x) > 0$. Viceversa per $l < 0$.

Questo è logico: se una funzione tende a un valore positivo, allora anche tutti i punti vicini a quel valore lo dovranno essere.

## Referenze