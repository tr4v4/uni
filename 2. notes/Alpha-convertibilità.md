---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 21-11-2023 21:32:10
links:
  - "[[Lecture 16112023092027]]"
---
# Alpha-convertibilità
---
## Introduzione
> Due formule in [[Logica del primo ordine|logica del prim'ordine]] si dicono $\alpha$-convertibili quando hanno lo stesso [[Diagramma di legame|diagramma di legame]]. In tal caso esiste una [[Relazione di equivalenza|relazione di equivalenza]] tra di esse.

## Utilizzi
Quando due formule sono equivalenti, e quindi $\alpha$-convertibili, significa che è possibile sostituire i nomi delle variabili di una con altri (per tutte le occorrenze), _senza modificare la semantica dell'espressione_. Per questo l'$\alpha$-convertibilità viene **utilizzata in [[Deduzione naturale|deduzione naturale]] per sostituire il nome di una variabile legata al fine di evitare il fenomeno di [[Shadowing|shadowing]]**: quest'operazione è detta, per l'appunto, [[Sostituzione|sostituzione]].

### Intuizioni
La scelta del nome da sostituire per le variabili legate non ha importanza: esse sono infatti _legate a uno scope definito dal [[Binder|binder]], interno alla formula_.

Invece, la scelta del nome da sostituire per le [[Variabile libera|variabili libere]] è fondamentale, perché dipende dal contesto in cui sarà inserita la formula che contiene il binder che lega tali variabili!

#### Esempio
Possiamo vedere le variabili legate come le _variabili locali_ di un codice: se si modifica ogni occorrenza allo stesso modo, il programma rimane identico. Le variabili/funzioni di [[Libreria|libreria]], invece, rappresentano le _variabili libere_, _fuori dal nostro dominio di controllo_: non possiamo sostituirle.

## Referenze