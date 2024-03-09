---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 13-10-2023 10:47:30
links:
  - "[[Lecture 02102023093041]]"
---
# Limite infinito di successione
---
## Definizione
> Presa una [[Successione numerica|successione]] $(a_{n})_{n}$, si dice
> $$\lim_{n \to +\infty} a_{n} = +\infty$$
> se
> $$\forall k \in \mathbb{R}, \exists \delta = \delta(k) > 0 : \forall n > d : a_{n} \geq k$$
> Il che significa: **preso un qualunque valore k, esiste sempre una soglia delta tale per cui la successione oltre quella soglia produce valori sempre più grandi di k**.
> <u>Nota</u>: ci si può anche solo limitare a $\forall k > 0$ dato che cerchiamo valori tendenti a $+\infty$.
> 
> oppure
> $$\lim_{n \to +\infty} a_{n} = -\infty$$
> se
> $$\forall k \in \mathbb{R}, \exists \delta = \delta(k) > 0 : \forall n > d : a_{n} \leq k$$
> Il che significa: **preso un qualunque valore k, esiste sempre una soglia delta tale per cui la successione oltre quella soglia produce valori sempre più piccoli di k**.
> <u>Nota</u>: ci si può anche solo limitare a $\forall k < 0$ dato che cerchiamo valori tendenti a $-\infty$.

Quindi vale rispettivamente
![[definizione-limite-infinito-maggiore.png]]
e
![[definizione-limite-infinito-minore.png]]

Ad ogni modo in entrambi i casi si dice che $a_{n}$ è **divergente**.

## Referenze