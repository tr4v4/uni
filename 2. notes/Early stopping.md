---
tags:
  - category/note
  - status/finished
  - topic/introduzione-all-apprendimento-automatico
date: 08-10-2025 18:46:22
links:
  - "[[Lecture 02102025131619]]"
---
# Early stopping
---
## Introduzione
> L'**early stopping** e' una tecnica usata per evitare l'[[Overfitting|overfitting]] degli [[Albero di decisione|alberi decisionali]].

## Funzionamento
Il principio e' semplice: **terminiamo la costruzione dell'albero non appena non e' piu' statisticamente significativo migliorare il modello**.

Con statisticamente significativo, per esempio, possiamo intendere quando il [[Guadagno informativo|guadagno informativo]] e' sotto una certa soglia, o quando il numero dei dati relativo al nodo e' troppo piccolo.

## Referenze