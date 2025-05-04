---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 03-05-2025 15:35:55
links:
  - "[[Lecture 20032025151643]]"
---
# Loading dinamico
---
## Introduzione
> Il **loading dinamico** è un meccanismo che consente di _caricare moduli o librerie in memoria durante l'esecuzione di un programma_, piuttosto che al momento della sua compilazione.

Questo meccanismo e' implementato dal [[Sistema operativo|sistema operativo]], ma dev'essere esplicitato dal programmatore (non e' trasparente).

## Funzionamento
Tutte le routine (procedure, funzioni) della libreria, sono compilate con [[Binding|binding]] a _load-time_ (codice relocabile). Quando il programma richiede l'esecuzione di una routine in loading dinamico, questa viene caricata in memoria e interviene il [[Linking dinamico|linking dinamico]] per collegarla al programma.

## Esempi
Gli stessi plug-in sono un esempio di loading dinamico, in cui le librerie vengono caricate a run-time.

## Referenze