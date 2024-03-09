---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 06-03-2024 19:03:56
links:
  - "[[Lecture 28022024141133]]"
---
# Integrazione di derivate di funzioni composte
---
## Introduzione
Prese due [[Funzione matematica|funzioni]] reali $g, f$ con domini t.c. $\exists (g \circ f)$, dove $(g \circ f)(x) = g(f(x))$[^1]. La [[Algebra delle derivate#Funzioni composte|regola della catena]] vuole che
$$(g \circ f)'(x) = g'(f(x)) \cdot f'(x) \ \ \ \forall x$$

Sfrutto la [[Integrale#Linearità[ 2]|linearità degli integrali]] per integrare ambo i membri dell'uguaglianza e ottenere
$$\int (g \circ f)'(x) \ dx = \int g'(f(x)) \cdot f'(x) \ dx$$

che per il [[Teorema fondamentale del calcolo integrale|teorema fondamentale del calcolo integrale]] si semplifica in
$$\int g'(f(x)) \cdot f'(x) \ dx = (g \circ f)(x) = g(f(x))$$

## Referenze
[^1]: ovvero la _composizione di funzioni_