---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 28-09-2024 13:33:12
links:
  - "[[Lecture 23092024132935]]"
---
# Algoritmi per il calcolo delle radici di una funzione
---
## Introduzione
Per calcolare le radici di una funzione (_non lineare_) del tipo
$$f(x) = 0$$
sono necessarie due cose:
1. _ci si deve chiedere l'esistenza (e unicità) della soluzione_;
2. _si deve applicare un algoritmo per il calcolo della soluzione_.

### Esistenza e unicità
Per risolvere la questione dell'esistenza e unicità della radice, è sufficiente il [[Teorema degli zeri|teorema degli zeri]], tale per cui presa una $f: [a, b] \to \mathbb{R}$ [[Funzioni continue|continua]] in $[a, b]$ e con $f(a) \cdot f(b) < 0$, allora $\exists x \in [a, b] : f(x) = 0$.

Ci basta quindi _selezionare un intervallo $[a, b]$ tale per cui $f$ sappiamo essere continua e $f(a) \cdot f(b) < 0$_: questo ci garantisce l'esistenza (non l'unicità) di una radice nell'intervallo.

### Algoritmi per calcolo
Esistono una serie di algoritmi per ciò:
- [[Algoritmo di bisezione]]
- [[Algoritmo iterativo]]
	- [[Algoritmo dell'iterazione di punto fisso]]
	- [[Algoritmo di Newton]]

La differenza tra questi algoritmi sta fondamentalmente nel [[Complessità computazionale|costo computazionale]], e nella **dicotomia tra accuratezza e tempo di calcolo**. In particolare, per gli algoritmi iterativi, si stabilisce un fattore matematicamente formalizzato che ne indica l'efficienza: la [[Velocità di convergenza|velocità di convergenza]].

## Referenze