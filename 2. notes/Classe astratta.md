---
tags:
  - category/note
  - status/finished
  - topic/algoritmi-e-strutture-dati
  - topic/linguaggi-di-programmazione
date: 15-03-2024 14:17:11
links:
  - "[[Lecture 12032024111356]]"
  - "[[Lecture 14052025105842]]"
---
# Classe astratta
---
## Introduzione
> Per **classe [[Astrazione|astratta]]** in [[Java]] si intende una _superclasse generale che definisce caratteristiche comuni a tutta la gerarchia delle proprie sottoclassi_.

In particolare una classe astratta _impone alle sottoclassi di implementare dei metodi definiti astratti_ (con la keyword `abstract`) che non sono implementati dalla superclasse. Allo stesso tempo fornisce metodi implementati univoci a tutte le sottoclassi[^1].

Si tratta fondamentalmente di una via di mezzo tra le [[Interfaccia|interfacce]] e le [[Classe|classi]]: possono definire campi e implementazioni di metodi, ma anche lasciare dei metodi come _astratti_, come le interfacce, costringendo le sottoclassi ad implementarli.

## Referenze
[^1]: a differenza di quanto avviene con le [[Interfaccia|interfacce]]