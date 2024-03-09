---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 27-02-2024 20:16:53
links:
  - "[[Lecture 26022024130925]]"
---
# Funzione integrale
---
## Introduzione
> Sia $f: ]a, b[ \to \mathbb{R}$ una [[Funzione matematica|funzione]] [[Funzioni continue|continua]], e $c \in ]a, b[$, allora si introduce la **funzione integrale** $I_{c} : ]a, b[ \to \mathbb{R}$ come
> $$I_{c}(x) = \int_{c}^{x} f(t) \ dt$$
> che è _ben definita_ perché $f$ è continua.

### Interpretazione
La funzione integrale di una funzione $f$ ci dice, fissato un punto $c$ del dominio, _come cambia il valore dell'area di $f$ al variare di $x$_. A tutti gli effetti, se consideriamo $f(x) \geq 0 \ \ \ \forall x \in ]a, b[$ stiamo definendo come varia l'[[Integrale|integrale]] del suo [[Sottografico di funzione|sottografico]] al variare di $x$.

## Osservazioni
Notare che
$$I_{c}(c) = \int_{c}^{c} f(t) \ dt = 0$$

Inoltre, considerati due punti $c, c' \in ]a, b[$, vale che
$$I_{c}(x) - I_{c'}(x) = k \ \ \ \forall x \in ]a, b[$$
ovvio, perché
$$I_{c}(x) - I_{c'}(x) = \int_{c}^{x} f - \int_{c'}^{x} f = \int_{c}^{x} f + \int_{x}^{c'} f = \int_{c}^{c'} f$$[^1]
ovvero un valore costante, che non dipende da $x$.

## Referenze
[^1]: per l'[[Integrale#Additività|additività degli integrali]]