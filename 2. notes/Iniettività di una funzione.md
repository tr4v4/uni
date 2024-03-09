---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
  - topic/logica-per-informatica
date: 24-09-2023 13:53:35
links:
  - "[[Lecture 18092023093106]]"
  - "[[Lecture 22092023133316]]"
  - "[[Lecture 11102023131154]]"
  - "[[Lecture 12102023091734]]"
---
# Iniettività di una funzione
---
## Definizione
> Una [[Funzione matematica|funzione]] si dice **iniettiva** se _a diversi punti del dominio corrispondono diversi punti del codominio_. Deve rispettare quindi la suddetta legge:
> $$\forall d, d' \in D : d \neq d' \land f(d) \neq f(d')$$
> oppure
> $$\forall x, y \in D, (f(x) = f(y) \implies x = y)$$

Se, quindi, "invertendo il verso delle frecce" tra _dominio_ e _codominio_ la funzione risultante rimane valida, allora la funzione è iniettiva. Per poterlo essere, quindi, significa che elementi del dominio differenti non possono corrispondere ad uno stesso elemento del codominio: altrimenti, invertendo i due insiemi, **non verrebbe più rispettata la regola fondamentale**.

Una funzione iniettiva viene indicata con la notazione $1-1$.
![[funzione-iniettiva.png]]

### Esempi
- $f(\mathbb{R}, \mathbb{R}, x^2) \neq 1-1$
- $f(\mathbb{R}, \mathbb{R}, x^3) = 1-1$
- $f(\mathbb{R_+}, \mathbb{R}, x^2) = 1-1$ (attenzione, _dipende sempre anche da dominio_, e non solo dalla legge)

## Intuizione
Se per ogni elemento del dominio ci dev'essere un elemento distinto del codominio, allora _il codominio non può avere meno elementi del dominio_.

## Referenze