---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 07-10-2023 15:07:51
links:
  - "[[Lecture 06102023134057]]"
---
# Funzione logaritmica
---
## Introduzione
> Se $a \in \mathbb{R}, \ 0 < a, \ a \neq 1$
> $$\forall y \in \mathbb{R} : y > 0, \exists! x \in \mathbb{R}: a^{x} = y$$
> dove quindi $x$ si scrive come
> $$x := \log_{a} y$$
> Per cui
> $$\log_{a} : \mathbb{R}^{*}_{+} \longrightarrow \mathbb{R}$$

<u>Nota bene</u>: il logaritmo è la funzione inversa dell'[[Funzione esponenziale|esponenziale]].

Da ciò si ha:
- $a^{\log_{a}y} = y$
- $\log_{a}(a^{x}) = x$

Per cui è facile passare da logaritmo ad esponenziale e viceversa:
![[rapporto-logaritmo-esponenziale.png]]

## Grafico
```functionplot
---
title: a > 1
xLabel: x
yLabel: y
bounds: [-1,3,-5,3]
disableZoom: false
grid: true
---
f(x)=log(x)
```
```functionplot
---
title: 0 < a < 1
xLabel: x
yLabel: y
bounds: [-1,3,-3,5]
disableZoom: false
grid: true
---
f(x)=-log(x)
```

## Referenze