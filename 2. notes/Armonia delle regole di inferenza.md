---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 24-10-2023 10:48:35
links:
  - "[[Lecture 19102023092110]]"
---
# Armonia delle regole di inferenza
---
## Introduzione
> L'**armonia** nel campo della [[Deduzione naturale|deduzione naturale]] è una _proprietà logica_ che lega le [[Regole di introduzione|regole di introduzione]] con quelle di [[Regole di eliminazione|eliminazione]].

Fondamentalmente _il sistema con cui eliminiamo delle ipotesi è una conseguenza diretta di come abbiamo dimostrato tali ipotesi_ (a meno che non fossero globali).

### Esempi
#### [[Regole di inferenza dell'OR]]
Le due regole di eliminazione dell'[[OR]] ci dicono che _possiamo supporre $F_{1} \lor F_{2}$ dimostrando $F_{3}$ per entrambi i casi_, ovvero nel caso in cui $F_{1}$ valga e nel caso in cui $F_{2}$ valga. Assumendo che $F_{1} \lor F_{2}$ non sia un'ipotesi globale, per supporla abbiamo dovuto prima dimostrarla usando una delle due regole d'introduzione dell'OR. Abbiamo infatti dovuto dimostrare o $F_{1}$ o $F_{2}$ (in base a ciò che risulta dimostrabile).

Risulta quindi **sensato supporre $F_{1} \lor F_{2}$ in quanto in precedenza abbiamo provato che o $F_{1}$ o $F_{2}$ vale**!
![[Drawing 2023-10-28 11.43.51.excalidraw|750]]

#### [[Regole di inferenza dell'AND]]

## Referenze