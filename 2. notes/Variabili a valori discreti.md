---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 02-03-2025 17:28:07
links:
  - "[[Lecture 26022025091753]]"
---
# Variabili a valori discreti
---
## Introduzione
> Per **variabili a valori discreti** intendiamo nell'ambito della [[Programmazione lineare|programmazione lineare]] delle variabili che non sono ne' logiche, ne' intere, ne' appartenenti a un intervallo, ma sono appartenenti a un insieme estremamente specifico $\{v_{1}, \cdots, v_{n}\}$ di $n$ valori.
> Per modellizzare tali variabili, introduciamo $n$ variabili logiche (booleane) $y_{1}, \cdots, y_{n}$ vincolate come segue
> - $y_{i} \in \{0, 1\}$
> - $\sum\limits_{i=1}^{n} y_{i} = 1$
> - $x = \sum\limits_{i=1}^{n}v_{i}y_{i}$
> 
> che quindi fungono da _selettore_, indicando se il valore preso da $x$ e' $v_{i}$.

## Referenze