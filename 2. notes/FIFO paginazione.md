---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
  - topic/sistemi-operativi
date: 24-11-2023 15:27:54
links:
  - "[[Lecture 16112023133640]]"
  - "[[Lecture 21032025091929]]"
---
# FIFO paginazione
---
## Introduzione
> Il **FIFO paginazione** è un [[Algoritmi di paginazione|algoritmo di paginazione]] basato sul paradigma [[FIFO]] (_First-In First-Out_), che _privilegia quindi la rimozione della [[Paginazione|pagina]] inserita nel working set da più tempo_ (la più vecchia).

Si implementa attraverso una semplice [[Lista|lista]] ([[coda|coda]]) o con un _counter di page fault_ associato a ogni pagina: ad ogni page fault il counter di ogni blocco in RAM viene incrementato, e quando c'è da scegliere il blocco "vittima" _viene preso quello con il counter più alto_.

## Osservazioni
E' semplice, ma il fatto che una pagina sia in memoria da piu' tempo non significa che non sia piu' utile. "I vecchi talvolta servono".

## Referenze