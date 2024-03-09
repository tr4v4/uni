---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 02-12-2023 13:35:06
links:
  - "[[Lecture 29112023131955]]"
---
# Left unital magma
---
## Introduzione
> Un **left unital magma** è un [[Magma|magma]] che ha un _[[Elemento neutro|elemento neutro]] $e$ a sinistra per $\circ$_, della forma
> $$(\mathbb{A}, \circ, e)$$

## Prodotto cartesiano
Presi due left unital magma $(\mathbb{A}, \circ, a)$ e $(\mathbb{B}, \bullet, b)$, il loro [[Prodotto cartesiano|prodotto cartesiano]] è
$$(\mathbb{A} \times \mathbb{B}, \oplus, \langle a, b \rangle)$$
che è sua volta un left unital magma, dove
$$\langle x_{a_{1}}, y_{b_{1}} \rangle \oplus \langle x_{a_{2}}, y_{b_{2}} \rangle ::= \langle x_{a_{1}} \circ x_{a_{2}}, y_{b_{1}} \bullet y_{b_{2}} \rangle$$

### Dimostrazione
Preso $c \in \mathbb{A} \times \mathbb{B}$, ovvero $c = \langle x, y \rangle$, dobbiamo dimostrare che
$$\langle a, b \rangle \oplus \langle x, y \rangle = \langle x, y \rangle$$
ovvero
$$\langle a \circ x, b \bullet y \rangle = \langle x, y \rangle$$
ovvio.

**Qed**.

## Referenze