---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 18-03-2024 20:12:57
links:
  - "[[Lecture 11032024131300]]"
  - "[[Lecture 14032024140617]]"
---
# Disuguaglianza triangolare
---
## Introduzione
> La **disuguaglianza triangolare** è un'importante risultato geometrico usato in molte dimostrazioni, e si formulizza in
> $$||x + y|| \leq ||x|| + ||y|| \ \ \ \forall x, y, \in \mathbb{R}^{n}$$
> dove $||x||$ è la [[Norma euclidea|norma]].

## Dimostrazione
Per dimostrare $||x + y|| \leq ||x|| + ||y|| \ \ \ \forall x, y, \in \mathbb{R}^{n}$ possiamo elevare entrambi i membri al quadrato, per sfruttare la formula del [[Quadrato di un binomio|quadrato di un binomio]] generalizzato a vettori. Per cui dimostriamo
$$||x + y||^{2} \leq (||x|| + ||y||)^{2}$$

Calcoliamo quindi $||x+y||^{2}$, allora si ha
$$||x + y||^{2} = ||x||^{2} + 2xy + ||y||^{2} \leq ||x||^{2} + ||y||^{2} + 2||xy||$$

Ora, per la [[Disuguaglianza di Cauchy-Schwarz|disuguaglianza di Cauchy-Schwarz]], ho che l'ultimo termine $2||xy||$ posso scriverlo come
$$2||xy|| \leq 2 ||x|| \cdot ||y||$$

Per cui mi riduco ad avere che
$$||x + y||^{2} \leq ||x||^{2} + ||y||^{2} + 2||xy|| = ||x||^{2} + ||y||^{2} + 2 ||x|| \cdot ||y||$$

L'ultima forma è un quadrato di binomio, per cui ottengo
$$||x + y||^{2} \leq (||x|| + ||y||)^{2}$$

da cui, togliendo i quadrati ottengo proprio il teorema.

**Qed**.

## Referenze