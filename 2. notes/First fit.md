---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
  - topic/linguaggi-di-programmazione
  - topic/sistemi-operativi
date: 24-11-2023 17:27:59
links:
  - "[[Lecture 20112023130829]]"
  - "[[Lecture 26022025111603]]"
  - "[[Lecture 20032025151643]]"
---
# First fit
---
## Introduzione
> Il **first fit** e' un [[Algoritmo|algoritmo]] usato sia per l'[[Allocazione dinamica|allocazione dinamica]] della memoria, sia come _tecnica di swapping_ per limitare il problema della [[Frammentazione esterna|frammentazione esterna]] della [[Segmentazione|segmentazione]]. Consiste nel _scegliere il primo spazio libero sufficientemente grande da contenere il [[Processo|processo]]/[[Segmento|segmento]] da allocare_.
> Di solito le lacune sono scorse circolarmente, per velocizzare il processo di ricerca.

Per quanto possa sembrare controproducente, si è dimostrato[^1] che questa tecnica riesce a limitare molto di più il problema di quanto lo faccia il [[Best fit|best fit]]. Inoltre il "first fit" è estremamente veloce, ed evita di creare i piccoli _gap_ tipici del "best fit".

## Referenze
[^1]: [[Donald Knuth]]