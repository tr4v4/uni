---
tags:
  - category/note
  - status/finished
  - topic/programmazione
  - topic/linguaggi-di-programmazione
date: 26-09-2023 09:08:32
links:
  - "[[Lecture 25092023151613]]"
  - "[[Lecture 27022025131944]]"
---
# Assegnamento
---
## Introduzione
> L'istruzione di assegnamento **memorizza un valore o il risultato di un calcolo in una variabile**. Segue la sintassi:
> `variabile = espressione`
> dove
> - `variabile` ([[Variabile|variabile]]) è un [[Identificatore|identificatore]];
> - `espressione` è un'[[Espressione|espressione]].
> 
> Segue la [[Dichiarazione|dichiarazione]].

## Sintassi
E' necessario comprendere bene la sintassi dell'assegnamento. Per esempio, considerata l'operazione `X = X + 1`, avremo che:
- la prima `X` è **l-value**, ovvero la variabile vera e propria, il contenitore del [[Nome|nome]] `X`;
- la seconda `X` è **r-value**, ossia vale come il contenuto della variabile di nome `X`;

Inoltre, normalmente l'assegnamento non restituisce un valore, piuttosto produce un _side-effect_... Tuttavia, in alcuni linguaggi tra cui [[C]], l'assegnamento restituisce il valore della variabile dell'assegnamento (es. `X = 2` restituisce 2).

## Referenze