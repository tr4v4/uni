---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 10-11-2024 20:10:23
links:
  - "[[Lecture 04112024131513]]"
---
# Fattorizzazione ai valori singolari troncata
---
## Introduzione
> La **fattorizzazione ai valori singolari troncata** (o **TSVD**) è una tecnica di [[Regolarizzazione|regolarizzazione]] dei [[Problemi inversi|problemi inversi]] _lineari_ che, una volta [[Fattorizzazione ai valori singolari|fattorizzata ai valori singolari]] la [[Matrice|matrice]] $A$ del sistema $Ax = y^{\delta}$, calcola la soluzione $x^{*}$ al [[Problema dei minimi quadrati|problema dei minimi quadrati]] attraverso la sommatoria
> $$x^{*} = \sum\limits_{i=1}^{k} \frac{u_{i}^{T}y^{\delta}}{\sigma_{i}}v_{i}$$
> dove $k < n$, con $n$ numero di colonne di $A$.

In particolare, la soluzione al problema viene _approssimata_, fermandosi a $k$ iterazioni. Tale valore deve corrispondere a **quando non sono più soddisfatte le [[Condizioni discrete di Picard|condizioni discrete di Picard]]**.

## Generalizzazione
Posso considerare la sommatoria fino a $n$ introducendo dei _fattori di filtro_ $f_{i}$ che valgono $1$ nelle prime $k$ iterazioni e $0$ in tutte quelle da $k+1$ a $n$:
$$x^{*} = \sum\limits_{i=1}^{n} f_{i} \frac{u_{i}^{T}y^{\delta}}{\sigma_{i}}v_{i}$$

## Referenze