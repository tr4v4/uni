---
tags:
  - category/note
  - status/finished
  - topic/programmazione
date: 12-10-2023 19:40:03
links:
  - "[[Lecture 11102023092734]]"
---
# Libreria
---
## Introduzione
> Una **libreria** in informatica consiste in una serie di [[Funzione informatica|funzioni]] e/o [[Classe informatica|classi]] utili per l'implementazione del programma che si vuole scrivere.

Talvolta librerie diverse possono contenere funzioni con lo stesso nome, o addirittura funzioni della stessa libreria possono essere omonime. Per evitare quindi di incorrere in _conflitti_ si utilizzano i [[Namespace|namespace]].

## Costruzione
Per costruire una libreria in [[C++]] è necessario:
1. creare il file `library.h` contenente le dichiarazioni ([[Funzione informatica#Firma|firme]]) delle funzioni
2. creare il file `library.cpp` (in cui includere `library.h`) contenente le definizioni (implementazioni) delle funzioni
3. includere nel `main` la libreria `library.h`

## Referenze