---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
  - topic/logica-per-informatica
date: 24-09-2023 13:57:57
links:
  - "[[Lecture 22092023133316]]"
  - "[[Lecture 11102023131154]]"
  - "[[Lecture 12102023091734]]"
---
# Suriettività di una funzione
---
## Definizione
> Una [[Funzione matematica|funzione]] si dice **suriettiva** se _ogni elemento del codominio è [[Immagine di funzione|immagine]] di almeno un elemento del dominio_. Deve rispettare allora la seguente legge:
> $$Im f = C$$
> dove $Im f$ è l'_immagine_ della funzione, definita come
> $$Im f = \{c \in C | \exists d \in D : f(d) = c\}, \, Imf \subseteq C$$
> Si può anche scrivere che una funzione è suriettiva quando
> $$\forall c \in C | \exists d \in D : f(d) = c$$

Una funzione suriettiva viene indicata con $su$.
![[funzione-suriettiva.png]]

### Esempi
- $f(\mathbb{R}, \mathbb{R}, x^{2}) \neq su$ (infatti in questo caso $Im f = R_{+} \subsetneqq R$)
- $f(\mathbb{R}, \mathbb{R}, x^{3}) = su$
- $f(\mathbb{R}, \mathbb{R}_{+}, x^{2}) = su$ (attenzione, _dipende anche sempre dal codominio_, e non solo dalla legge)

## Intuizione
Se ogni elemento del codominio dev'essere associato ad almeno un elemento del dominio, _il dominio non può avere meno elementi del codominio_.

## Referenze