---
tags:
  - category/note
  - status/finished
  - topic/architettura-degli-elaboratori
date: 24-11-2023 15:05:49
links:
  - "[[Lecture 16112023133640]]"
---
# Algoritmi di paginazione
---
## Introduzione
> Gli **algoritmi di paginazione** sono [[Algoritmo|algoritmi]] che, a seguito della scatenazione della [[Trap|trap]] _page fault_ nella fase di traduzione di un indirizzo virtuale a fisico nel contesto della [[Paginazione|paginazione]], _determinano quale tra le pagine del working set (in [[RAM]]) è da togliere per sovrascrivere quella richiesta_.

E' ovvio che nel caso migliore, in cui la RAM abbia dei blocchi liberi, questo problema non si verifichi:
![[page-fault.png]]

## Politiche
- [[LRU]]
- [[FIFO paginazione]]

Per entrambe le politiche si utilizza, in aggiunta, una tecnica chiamata [[Dirty bit|dirty bit]].

## Referenze
- [slide di approfondimento](https://cs.unibg.it/gherardi/so2013/slides/10.pdf)