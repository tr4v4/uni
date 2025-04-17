---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 05-04-2025 18:31:29
links:
  - "[[Lecture 12032025111631]]"
  - "[[Lecture 19032025113725]]"
---
# Shallow binding
---
## Introduzione
> Lo **shallow binding** e' una delle due regole di valutazione dell'[[Ambiente|ambiente]] delle [[Funzione di ordine superiore|funzioni di ordine superiore]] passate come parametro ad altri funzioni, che _risolve le variabili non locali nell'ambiente al momento dell'[[Invocazione di procedura|invocazione]] della funzione passata come parametro attuale_.

In definitiva:
- in caso di [[Scope statico|scope statico]] --> usa sempre la [[Chiusura|chiusura]] con puntatore a [[Catena statica|catena statica]] per determinare l'ambiente di valutazione delle variabili non locali della funzione;
- in caso di [[Scope dinamico|scope dinamico]] --> _e' automatico_! si usa lo stesso principio dello scope dinamico, per cui basta scorrere i record di attivazione e si implementa automaticamente lo shallow binding.

Fatto sta che di solito lo shallow binding viene associato allo scope dinamico.

## Referenze