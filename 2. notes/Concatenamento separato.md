---
tags:
  - category/note
  - status/ongoing
  - topic/algoritmi-e-strutture-dati
date: 24-03-2024 22:20:14
links:
  - "[[Lecture 21032024091145]]"
---
# Concatenamento separato
---
## Introduzione
> Per **concatenamento separato** si intende una tecnica di mitigazione delle [[Collisione hash|collisioni hash]] nel contesto delle [[Tabella hash|tabelle hash]], che _consiste nel memorizzare le chiavi $k$ con lo stesso valore $h(k) = i$ in una [[Lista|lista]] concatenata_, chiamata _lista di trabocco_.

![[concatenamento-separato.png]]

## Pseudocodice
![[pseudo-concatenamento-separato.png]]

### Costi
I [[Complessità computazionale|costi]] delle 3 operazioni risultano allora essere:
- _caso ottimo_: $O(1)$;
- _caso pessimo_: $\Theta(T[h(k)].\text{length})$, perché dipendono dalla ricerca lineare sulla lista di trabocco $T[h(k)]$ (e non da $m$, la dimensione della tabella);
- _caso medio_: difficile da calcolare;

## Referenze