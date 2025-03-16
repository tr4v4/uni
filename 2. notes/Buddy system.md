---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 16-03-2025 13:06:16
links:
  - "[[Lecture 26022025111603]]"
---
# Buddy system
---
## Introduzione
> Il **buddy system** e' un'implementazione delle [[Liste libere multiple|liste libere multiple]] dinamiche che prevede che la lista $k$ contenga blocchi di dimensione $2^{k}$.

## Funzionamento
### Allocazione
Se serve un blocco di dimensione fino a $2^{k}$, e tutti i blocchi di dimensione $2^{k}$ sono occupati, allora prendo un blocco di dimensione $2^{k+1}$ (dalla lista successiva), lo divido in 2 parti di dimensione $2^{k}$, li metto nella lista di riferimento e ne prendo uno per l'allocazione.

Questi due blocchi diventano _buddy_.

### Deallocazione
Se un blocco di dimensione $2^{k}$ viene deallocato, se il suo _buddy_ (la sua meta' di riferimento) e' disponibile (nella lista libera), allora viene riunito con esso e torna a far parte della lista libera dei blocchi di dimensione $2^{k+1}$.

<u>Nota bene</u>: le due metà si ricordano reciprocamente della loro esistenza, e quindi si riuniscono quando diventano entrambi liberi.

## Referenze