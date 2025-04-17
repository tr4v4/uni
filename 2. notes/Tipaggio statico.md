---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 05-04-2025 20:09:46
links:
  - "[[Lecture 02042025112213]]"
  - "[[Lecture 03042025131202]]"
---
# Tipaggio statico
---
## Introduzione
> Il **tipaggio statico** è un tipo di tipaggio in cui _il controllo dei tipi viene effettuato in fase di compilazione, prima dell'esecuzione del programma_.

E' importante notare che nel tipaggio statico _si deve fare una sovrapprossimazione del programma_, andando a considerare tutti i possibili rami del programma[^1].

Risulta pero' molto comodo: _una volta fatto il type-checking statico, si e' dimostrato un teorema che assicura che il programma controllato non avra' errori di tipi_.

Tuttavia, ci sono casi in cui il tipaggio statico non e' sufficiente: _quando si fa un accesso a un array con un indice non determinabile a compile-time, devo necessariamente fare [[Tipaggio dinamico|tipaggio dinamico]]_.

## Referenze

[^1]: per il [[Problema della fermata|problema della fermata]] non sappiamo in che ramo andra'