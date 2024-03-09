---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 09-11-2023 21:41:00
links:
  - "[[Lecture 06112023094954]]"
---
# Limite formulato per successione
---
## Definizione
> Definita una [[Funzione matematica|funzione]] $f: A \to \mathbb{R}$, e un punto $\bar{x} \in \mathcal{D}(A)$ ([[Punto di accumulazione|punto di accumulazione]] di $A$), allora si ha che
> $$\lim_{x \to \bar{x}} h(x) = l \iff \forall x_{n} \subseteq A, \ \ x_{n} \neq \bar{x} \ \ \forall n : \ \ x_{n} \stackrel{n}{\to} \bar{x} \implies h(x_{n}) \stackrel{n}{\to} l$$
> per $l \in \bar{\mathbb{R}} = \mathbb{R} \cup \{+\infty, -\infty\}$
> derivata da
> $$\lim_{x \to \bar{x}^{-}} h(x) = l \iff \forall x_{n} \subseteq A, \ \ x_{n} < \bar{x} \ \ \forall n : \ \ x_{n} \stackrel{n}{\to} \bar{x} \implies h(x_{n}) \stackrel{n}{\to} l$$
> $$\lim_{x \to \bar{x}^{+}} h(x) = l \iff \forall x_{n} \subseteq A, \ \ x_{n} > \bar{x} \ \ \forall n : \ \ x_{n} \stackrel{n}{\to} \bar{x} \implies h(x_{n}) \stackrel{n}{\to} l$$
> ovvero, **il [[Limite|limite]] di una funzione per un punto $\bar{x}$ esiste se e solo se per ogni [[Successione numerica|successione]] sottoinsieme del dominio della funzione, se la successione per $n \to +\infty$ tende a $\bar{x}$ allora anche la funzione per ogni elemento della successione tende al valore del limite $l$**.

## Utilizzi
Questo teorema viene usato nella sua forma _negata_: **per dimostrare che non esiste il limite di una funzione basta infatti trovare due successioni che tendono a $\bar{x}$ e per cui la funzione, per le due successioni, produce limiti diversi**.

O meglio:
$$\nexists \lim_{x \to \bar{x}} h(x) : \begin{cases} x_{n} \to \bar{x} \implies h(x_{n}) \to l_{1} \\ y_{n} \to \bar{x} \implies h(y_{n}) \to l_{2} \end{cases} \ \ \land \ \ l_{1} \neq l_{2}$$

## Referenze
