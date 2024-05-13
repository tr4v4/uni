---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 13-05-2024 21:16:34
links:
  - "[[Lecture 13052024131457]]"
---
# Insieme semplice
---
## Introduzione
> Un **insieme semplice** (o **dominio normale**) è una formulazione [[Insieme|insiemistica]] di un dominio di una [[Funzione matematica|funzione]] che rispetta certe proprietà. E' importante per la definizione di [[Integrale multiplo|integrale multiplo]], perché _consente appunto di definire per quali domini il volume della funzione si può esprimere come integrale multiplo_.

## Tipologie
### Insieme semplice rispetto all'asse $y$
> Sia $[a, b] \subseteq \mathbb{R}$ e siano $g_{1}, g_{2} : [a, b] \to \mathbb{R}$ [[Funzioni continue|continue]] e tali che $g_{1}(x) \leq g_{2}(x) \ \ \forall x \in [a, b]$, allora l'insieme semplice $A$ rispetto all'asse $y$ si definisce come:
> $$A = \{(x, y) \in \mathbb{R}^{2} | x \in [a, b], \ y \in [g_{1}(x), g_{2}(x)]\}$$

![[insieme-semplice-asse-y.jpg|500]]

### Insieme semplice rispetto all'asse $x$
> Sia $[c, d] \subseteq \mathbb{R}$ e siano $h_{1}, h_{2} : [c, d] \to \mathbb{R}$ [[Funzioni continue|continue]] e tali che $h_{1}(y) \leq h_{2}(y) \ \ \forall y \in [c, d]$, allora l'insieme semplice $A$ rispetto all'asse $x$ si definisce come:
> $$A = \{(x, y) \in \mathbb{R}^{2} | y \in [c, d], \ x \in [h_{1}(y), h_{2}(y)]\}$$

![[insieme-semplice-asse-x.jpg|500]]

### Non esistenza
_Posso esistere insiemi che non sono né semplici rispetto a $x$ né semplici rispetto a $y$_. Si pensi a una corona circolare.

## Referenze
- maggiori informazioni [qui](https://mathtube.altervista.org/lezione-18-analisi-2/)