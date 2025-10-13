---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 24-09-2025 23:26:05
links:
  - "[[Lecture 10042025131105]]"
  - "[[Lecture 16042025110927]]"
---
# Tipo funzione
---
## Introduzione
Nei [[Linguaggio di programmazione|linguaggi di programmazione]] ad alto livello, spesso c'e' il supporto alla definizione di [[Funzione informatica|funzioni]]. Alcuni di loro denotano il loro tipo; per esempio:
```C
R f(P p) { ... }
```
denota una funzione del tipo $P \to R$.

Nella realta' sono solo i [[Linguaggio di programmazione funzionale|linguaggi funzionali]] a rendere i tipi di funzione esprimibili.

L'unica operazione supportata dalle funzioni e' la loro applicazione: ossia l'[[Invocazione di procedura|invocazione]].

<u>Nota bene</u>: le funzioni in realta' non devono confondersi con quelle matematiche; potrebbero infatti esserci dei **side effects**! Se per esempio, pero', sappiamo che la funzione non ha side effect, allora possiamo usare tecniche come la [[Memoization|memoization]] per velocizzare la sua computazione!

## Referenze