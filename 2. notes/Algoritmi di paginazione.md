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
> Gli **algoritmi di paginazione** sono [[Algoritmo|algoritmi]] che, a seguito della scatenazione della [[Trap|trap]] _[[Page fault|page fault]]_ nella fase di traduzione di un indirizzo virtuale a fisico nel contesto della [[Paginazione|paginazione]], _determinano quale tra le pagine del working set (in [[RAM]]) è da togliere per sovrascrivere quella richiesta_.

E' ovvio che nel caso migliore, in cui la RAM abbia dei blocchi liberi, questo problema non si verifichi:
![[page-fault.png]]

## Obiettivi
L'obiettivo di un algoritmo di paginazione è quello di **minimizzare il numero di page fault** e quindi il numero di accessi alla memoria secondaria, che sono molto più lenti rispetto agli accessi alla memoria principale.

Tali algoritmi sono valutati sulla base del numero di accessi alla memoria secondaria data una certa sequenza di accessi alla memoria virtuale, detta **stringa di riferimenti** (generata casualmente o in modo deterministico).

<u>Nota bene</u>: della stringa di riferimenti si considera solo la parte che riguarda le pagine, non gli offset.

Ci si aspetta che piu' frame abbiamo, meno page fault si verifichino. In realta' non e' cosi': [[Anomalia di Belady|anomalia di Belady]].

## Algoritmi
- [[FIFO paginazione]]
- [[MIN paginazione]]
- [[LRU]]
- [[LFU]]

Per entrambe le politiche si utilizza, in aggiunta, una tecnica chiamata [[Dirty bit|dirty bit]].

## Referenze
- [slide di approfondimento](https://cs.unibg.it/gherardi/so2013/slides/10.pdf)
- [[Algoritmo a stack]]