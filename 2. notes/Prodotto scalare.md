---
tags:
  - category/note
  - status/finished
  - topic/algebra-e-geometria
  - topic/analisi-I
date: 21-02-2024 09:05:50
links:
  - "[[Lecture 20022024091619]]"
  - "[[Lecture 11032024131300]]"
---
# Prodotto scalare
---
## Introduzione
> Data una riga $1 \times n$ e una colonna $m \times 1$, ovvero due [[Vettore|vettori]], aventi la stessa lunghezza ($n = m$)
> $$A = (a_{1}, a_{2}, ..., a_{n})$$
> $$B = (b_{1}, b_{2}, ..., b_{m})$$
> si definisce **prodotto scalare** (o **dot-product**) la somma dei prodotti di ogni coefficiente di $A$ con il corrispondente coefficiente di $B$, ovvero:
> $$A \cdot B = \sum\limits_{k=1}^{n} a_{k}b_{k} = a_{1} \cdot b_{1} + \cdots + a_{n} \cdot b_{m} \in \mathbb{R}$$
> <u>Attenzione</u>: _il risultato è un numero_!

## Proprietà
### Simmetria
$$x \cdot y = y \cdot x \ \ \ \forall x, y \in \mathbb{R}^{n}$$

### Linearità
$$(\lambda x + \mu y) \cdot z = \lambda(x \cdot z) + \mu(y \cdot z) \ \ \ \forall x, y, z \in \mathbb{R}^{n}, \ \forall \lambda, \mu \in \mathbb{R}$$

<u>Nota bene</u>: il primo membro è una [[Combinazione lineare|combinazione lineare]]!

### Positività
$$x \cdot x \geq 0, \ \ x \cdot x = 0 \iff x = \underline{0} \ \ \ \forall x \in \mathbb{R}^{n}$$

Questo è vero perché $x \cdot x = \sum\limits_{k=1}^{n} x_{k}^{2} \geq 0$ perché somma di termini positivi.

## Referenze