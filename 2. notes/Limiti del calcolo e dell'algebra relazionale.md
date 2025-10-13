---
tags:
  - category/note
  - status/finished
  - topic/basi-di-dati
date: 13-10-2025 12:20:42
links:
  - "[[Lecture 09102025151427]]"
---
# Limiti del calcolo e dell'algebra relazionale
---
## Introduzione
Sia l'[[Algebra relazionale|algebra relazionale]] che il [[Calcolo relazionale|calcolo relazionale]] hanno dei **limiti forti**. Sono equivalenti, ma query potenzialmente utili non possono essere espresse:
- _non possiamo computare nuovi valori dalle query_, ma solo estrarli;
- _non possiamo computare query ricorsive, come la [[Chiusura transitiva|chiusura transitiva]]_;

In particolare per quest'ultima cosa, è impossibile da fare in quanto **ci vorrebbe un numero arbitrario di join**, una per ogni livello di [[Transitività di una relazione|transitività]].

E' per questa ragione che è nato [[Datalog]], un linguaggio ispirato a [[Prolog]] che consente di scrivere query ricorsive.

## Referenze