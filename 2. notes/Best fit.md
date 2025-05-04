---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
  - topic/linguaggi-di-programmazione
  - topic/sistemi-operativi
date: 24-11-2023 17:25:14
links:
  - "[[Lecture 20112023130829]]"
  - "[[Lecture 26022025111603]]"
  - "[[Lecture 20032025151643]]"
---
# Best fit
---
## Introduzione
> Il **best fit** è un [[Algoritmo|algoritmo]] usato sia per l'[[Allocazione dinamica|allocazione dinamica]] della memoria, sia come _tecnica di swapping_ per limitare il problema della [[Frammentazione esterna|frammentazione esterna]] della [[Segmentazione|segmentazione]]. Consiste nell'_inserire il nuovo processo/segmento nella lacuna più piccola sufficiente_.

Con questo si cerca, quindi, di limitare al più possibile la grandezza del _gap_ che si crea tra il buco lasciato dal segmento "vecchio" e la grandezza del segmento nuovo.

Non solo pero' e' piu' lento del [[First fit|first fit]], in quanto deve scorrere tutta la lista di segmenti per trovare il buco piu' piccolo, ma _puo' portare a una frammentazione esterna maggiore rispetto al first fit_.

## Referenze