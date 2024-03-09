---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 21-11-2023 21:10:09
links:
  - "[[Lecture 16112023092027]]"
---
# Diagramma di legame
---
## Introduzione
> Il **diagramma di legame** di una formula in [[Logica del primo ordine|logica del prim'ordine]] è un sistema che consente di _distinguere graficamente le [[Variabile libera|variabili libere]] dalle variabili legate_.

## Composizione
Presa un'espressione $P$, il suo diagramma di legame si compone:
1. collegando ogni occorrenza di una _variabile legata_ con il suo binder, per mezzo di una freccia
2. collegare ogni _variabile libera_ mediante una freccia che punta all'infinito, su cui scrivere il nome della variabile

<u>Nota bene</u>: **il nome della variabile scritto sulla freccia è di estrema importanza**. Infatti è da tenere in considerazione che le variabili libere, quando inserite in un "programma più ampio", si legheranno a un binder definito, che dovrà sapere il nome preciso della variabile[^1].

## Referenze
- [[Alpha-convertibilità]]

[^1]: è lo stesso principio dei [[Funzione informatica#Sintassi|parametri formali]] delle funzioni: un programma deve poter richiamare la funzione conoscendo i nomi dei parametri formali. Essa di fatto espone le proprie _variabili libere_ come un'[[Interfaccia|interfaccia]].