---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 06-03-2024 19:31:26
links:
  - "[[Lecture 28022024141133]]"
  - "[[Lecture 04032024131001]]"
---
# Tecniche d'integrazione
---
## Tecniche
- [[Integrazione di derivate di funzioni composte]]
- [[Integrazione per parti]]
- [[Integrazione per sostituzione]]

## Osservazione
Esistono funzioni elementari che _non ammettono [[Primitiva|primitive]] che siano funzioni elementari_: per il [[Teorema fondamentale del calcolo integrale|teorema fondamentale]] **sappiamo che esistono, ma non sono rappresentabili attraverso funzioni elementari**.
Queste sono:
- [[Integrale di Gauss]] --> $\int e^{-x^{2}} \ dx$, da cui si ottiene $\int_{0}^{x} e^{-t^{2}} \ dt$ che è la _funzione integrale degli errori_
- [[Logaritmo integrale]] --> $\int \frac{dx}{\ln{x}}$, che appare nella teoria dei numeri primi
- $\int \frac{e^{x}}{x} \ dx$

Si può viceversa trovare una formula risolutiva per determinate classi di integrali per parti:
- $\int e^{px} \sin{qx} \ dx$ o $\int e^{px} \cos{qx} \ dx \ \ \ q, p \in \mathbb{N}$
- $\int x^{p} \arctan{x} \ dx \ \ \ p \in \mathbb{N}$

## Referenze