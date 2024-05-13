---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 02-11-2023 22:26:29
links:
  - "[[Lecture 30102023093826]]"
  - "[[Lecture 03052024102451]]"
---
# Massimo e minimo relativo
---
## Introduzione
> Definita una [[Funzione matematica|funzione]] $f: A \to \mathbb{R}$:
> 1. $x_{0} \in A$ è un **punto di massimo locale/relativo** se
>    $$\exists r > 0 : f(x) \leq f(x_{0}) \ \ \forall x \in A \cap I_{r}(x_{0})$$
>    e $f(x_{0})$ è il **massimo locale**.
> 1. $x_{0} \in A$ è un **punto di minimo locale/relativo** se
>    $$\exists r > 0 : f(x) \geq f(x_{0}) \ \ \forall x \in A \cap I_{r}(x_{0})$$
>    e $f(x_{0})$ è il **minimo locale**.

Ciò che distingue i massimi/minimi relativi da i [[Massimo e minimo assoluto|massimi/minimi assoluti]] è che mentre per i secondi la condizione $f(x) \leq f(x_{0})$ o $f(x) \geq f(x_{0})$ deve valere $\forall x \in A$, nei primi deve valere solo per qualunque ($\forall r > 0$) intorno $I_{r}$ del dominio $A$.

### In $\mathbb{R}^{n}$
Chiaramente si può estendere il concetto di massimo e minimo relativo su [[Funzione a più variabili|funzioni a più variabili]].
> Data una funzione $f: \mathbb{R}^{n} \to \mathbb{R}$ un punto $\bar{x} \in \mathbb{R}^{n}$ si dice di massimo (o minimo) locale/relativo se
> $$\exists \delta > 0 : f(\bar{x}) \geq f(x) \ \ \forall x \in \mathbb{R}^{n} \cap I_{\delta}$$
> o
> $$\exists \delta > 0 : f(\bar{x}) \leq f(x) \ \ \forall x \in \mathbb{R}^{n} \cap I_{\delta}$$

## Referenze