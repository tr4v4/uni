---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
  - topic/algebra-e-geometria
date: 17-03-2024 22:12:39
links:
  - "[[Lecture 11032024131300]]"
  - "[[Lecture 14032024140617]]"
---
# Ortogonalità
---
## Introduzione
> Due [[Vettore|vettori]] $x, y \in \mathbb{R}^{n}$ si dicono **ortogonali** (o **perpendicolari**) sse
> $$<x, y> = 0$$
> ovvero se il loro [[Prodotto scalare|prodotto scalare]] fa 0, e in tal caso si scrive
> $$x \bot y$$

Per esempio si ha che:
- $\underline{0}$ è ortogonale a ogni vettore;
- se $x = (a, b)$ e $y = (-b, a)$ entrambi in $\mathbb{R}^{2}$ si ha $x \cdot y = a(-b) + ba = 0$
- se $x \in \mathbb{R}^{n}$ e $y = \left(\frac{1}{n}, \cdots, \frac{1}{n}\right) \in \mathbb{R}^{n}$ allora $x \cdot y$ è la media di $x$
- i vettori [[Coordinate rispetto a una base|coordinati]] (le [[Base|basi]] canoniche) $e_{1}, \cdots, e_{n}$ sono ortogonali a coppie, infatti $j \neq k \implies e_{j} \cdot e_{k} = 0$ è una famiglia ortogonale

## Proprietà
### Punto di minima distanza
Si ha che dati $v \neq \underline{0}$ e $x \in \mathbb{R}^{n}$, il [[Distanza tra punti#Punto di minima distanza da una retta|punto di minima distanza]] $\frac{xv}{|v|^{2}}v$ soddisfa
$$\left(x - \frac{xv}{|v|^{2}}v\right)v = xv - \frac{xv}{|v|^{2}}v \cdot v = xv - xv = 0$$

per cui è ortogonale a $x$.

### Vettore nullo
> L'unico vettore di $\mathbb{R}^{n}$ perpendicolare a tutti gli altri è il vettore nullo $\underline{0}$, ovvero
> $$<v, w> = 0 \ \ \forall w \in \mathbb{R}^{n} \iff v = \underline{0}$$

## Referenze