---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 09-03-2025 17:20:21
links:
  - "[[Lecture 03032025091200]]"
---
# Minima quantita' positiva prefissata
---
## Introduzione
> La **minima quantita' positiva prefissata** e' una tecnica con la quale si modellizza una variabile $x$ (che solitamente rappresenta un certo livello di produzione) che varia nei valori rappresentati da un insieme della forma
> $$\{0\} \cup [l, u]$$
> dove $0$ rappresenta l'assenza di produzione, mentre l'intervallo $[l, u]$ rappresenta i possibili livelli di produzione quando il meccanismo è attivo.

## Modellizzazione
Per poter modellizzare questa situazione si introduce una variabile logica $y \in \{0, 1\}$ che indica la presenza o meno di produzione, e poi si importano dei vincoli usando $y$:
$$ly \leq x \leq uy$$
Infatti
$$y = 0 \implies x = 0$$
$$y = 1 \implies l \leq x \leq u$$

## Referenze