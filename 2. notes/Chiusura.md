---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 05-04-2025 17:46:07
links:
  - "[[Lecture 12032025111631]]"
---
# Chiusura
---
## Introduzione
> Una **chiusura** e' la coppia ([[Variabile|variabile]], [[Ambiente|ambiente]]), che lega quindi un [[Nome|nome]] all'ambiente in cui sara' valutato.

## Funzioni di ordine superiore
Nel caso del passaggio di [[Funzione di ordine superiore|funzioni di ordine superiore]] come parametri, le due regole di [[Deep binding|deep]] e [[Shallow binding|shallow binding]] sono implementate mediante la chiusura: _come parametro attuale si passa la coppia `(puntatore alla funzione, ambiente non locale)`_.

<u>Nota bene</u>: nel caso di [[Scope statico|scope statico]], l'ambiente non locale sara' sempre lo stesso sia con deep che con shallow binding.

## Referenze