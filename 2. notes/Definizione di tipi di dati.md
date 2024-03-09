---
tags:
  - category/note
  - status/finished
  - topic/programmazione
date: 10-11-2023 18:32:14
links:
  - "[[Lecture 07112023104204]]"
---
# Definizione di tipi di dati
---
## Introduzione
In [[C++]], attraverso la _keyword_ `typedef` è possibile ridefinire nuovi [[Tipi di dati|tipi di dati]], o meglio _alias_ con cui chiamare specifici tipi.

### Esempi
```cpp
typdef int *p_int;
p_int pointer;
```
crea il tipo di dato `*p_int` che corrisponde al puntatore a un intero.

```cpp
typdef int array_int[50];
array_int v;
```
crea il tipo di dato `array_int` che corrisponde a un array di 50 interi.

## Referenze