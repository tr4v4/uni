---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 03-05-2025 17:13:10
links:
  - "[[Lecture 20032025151643]]"
---
# Worst fit
---
## Introduzione
> Il _worst fit_ e' un [[Algoritmo|algoritmo]] di [[Allocazione|allocazione]] della memoria che _assegna il blocco di memoria piu' grande disponibile a un [[Processo|processo]]_. In questo modo, si spera di lasciare spazio sufficiente per processi futuri.

Genera problemi per l'allocazione di processi di grosse dimensioni: se tutti i blocchi sufficientemente grandi sono stati spezzati per processi piccoli, _non si avranno piu' porzioni di memoria contigue sufficientemente grandi per allocare processi di grosse dimensioni_ ([[Frammentazione esterna|frammentazione esterna]]).

## Referenze