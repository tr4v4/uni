---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 27-04-2025 17:40:11
links:
  - "[[Lecture 16042025091309]]"
---
# Direzione di crescita
---
## Introduzione
> Una direzione $\xi \in \mathbb{R}^{n}$ e' detta **direzione di crescita** per $\bar{x}$ se per uno spostamento $\lambda$ lungo $\xi$ si ha che la funzione obiettivo cresce, ossia
> $$cx(\lambda) = c\bar{x} + \lambda c \xi > c\bar{x}$$
> e quindi questo avviene $\iff$
> $$c\xi > 0$$
> <u>Nota bene</u>: la _direzione di crescita non dipende dal punto $\bar{x}$_, ma solo dalla funzione obiettivo $c$ e dalla direzione $\xi$. Questo _avviene in quanto ci troviamo in un contesto di linearita'_!

Osserviamo che:
- $c = \underline{0} \implies$ ogni soluzione ammissibile e' ottima, caso triviale;
- $c \neq 0 \implies$ **se esiste una direzione ammissibile per $\bar{x}$ che sia anche di crescita, allora $\bar{x}$ non puo' essere ottimo**!

## Referenze