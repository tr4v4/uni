---
tags:
  - category/note
  - status/finished
  - topic/programmazione
date: 17-11-2023 10:01:59
links:
  - "[[Lecture 15112023091814]]"
---
# Memory leak
---
## Introduzione
> Il **memory leak** è un evento che avviene nel momento in cui _vengono persi [[Puntatori|puntatori]] a locazioni dell'[[Heap|heap]]_, che perciò _non sono più recuperabili e quindi liberabili_. Queste locazioni occupano memoria, e se accumulate _portano al totale riempimento dello spazio disponibile per l'allocazione dinamica_.

In particolare, per linguaggi come [[C]] e [[C++]], la liberazione della memoria dinamica non avviene automaticamente, attraverso un _meccanismo di [[Garbage collector|garbage collection]]_[^1], ma dev'essere attuata manualmente dal programmatore al fine di non evitare il memory leak, attraverso istruzioni come:
```cpp
delete pointer;    // C++
free(pointer)      // C
```

## Referenze
[^1]: come invece è presente in [[Java]]