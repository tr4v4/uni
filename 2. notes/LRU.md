---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
date: 24-11-2023 15:24:32
links:
  - "[[Lecture 16112023133640]]"
---
# LRU
---
## Introduzione
> L'**LRU** (_Least Recently Used_) è un [[Algoritmi di paginazione|algoritmo di paginazione]] che _privilegia la rimozione della [[Paginazione|pagina]] del working set da più tempo non utilizzata_.

Si implementa attraverso una [[Liste|lista]]: le pagine accedute vengono inserite in coda, e se già presenti vengono ritrasferite in coda; in questo modo in testa si avrà la pagina che da più tempo non è stata acceduta, e quindi ritenuta "sacrificabile".

## Referenze