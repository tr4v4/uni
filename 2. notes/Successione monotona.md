---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 05-10-2023 20:01:15
links:
  - "[[Lecture 02102023093041]]"
---
# Successione monotona
---
## Introduzione
> Si definisce una [[Successione numerica|successione]] **monotona** se è _crescente_ o _decrescente_.

### Successione crescente
> $a_{n}$ si dice **crescente** se
> $$\forall n \in \mathbb{N} : a_{n} \leq a_{n+1}$$
> e si indica con
> $$a_{n} \uparrow$$

### Successione decrescente
> $a_{n}$ si dice **decrescente** se
> $$\forall n \in \mathbb{N} : a_{n} \geq a_{n+1}$$
> e si indica con
> $$a_{n} \downarrow$$

### Esempi
- $a_{n} = \frac{1}{n}$ --> _decrescente_
- $a_{n} = n^{2}$ --> _crescente_

## Proprietà
> Se una successione è monotona allora ha sempre [[Limite di successione|limite]]. Vale a dire che è per forza _convergente_ o _divergente_.

Per cui, è [[Dimostrazione successioni monotone hanno limite|dimostrabile]] che
> Se $a_{n}$ è crescente, allora
> $$\lim_{n \to +\infty} a_{n} = \sup\{a_{n} | n \in \mathbb{N}\}$$
> e viceversa, se $a_{n}$ è decrescente, allora si avrà
> $$\lim_{n \to +\infty} a_{n} = \inf\{a_{n} | n \in \mathbb{N}\}$$

## Referenze