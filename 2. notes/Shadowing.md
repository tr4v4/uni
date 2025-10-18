---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 17-10-2025 20:26:39
links:
  - "[[Lecture 14052025105842]]"
---
# Shadowing
---
## Introduzione
> Nei [[Linguaggio di programmazione orientato a oggetti|linguaggi orientati agli oggetti]] ([[OOP]]) per **shadowing** si intende il caso in cui una sotto[[Classe|classe]] puo' mascherare i campi della sua superclasse definendo campi con lo stesso nome.

Tale mascheramento _avviene secondo le regole di [[Scope|scope]] a livello di blocco_: la superclasse appartiene al blocco esterno e la sottoclasse al blocco interno, per cui quest'ultimo puo' mascherare qualsiasi variabile del blocco esterno (e dell'eventuale blocco ancora piu' esterno!). Si dice quindi che lo shadowing e' risolto in [[Early binding|early binding]].

Per accedere a una variabile della sua superclasse, [[Java]] impone l'utilizzo del `this` per evitare errori.

## Referenze