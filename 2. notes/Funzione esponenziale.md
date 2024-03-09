---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 07-10-2023 13:03:49
links:
  - "[[Lecture 06102023134057]]"
---
# Funzione esponenziale
---
## Introduzione
Una [[Funzione matematica|funzione]] esponenziale si definisce come
$$a^{x}$$
dove:
- $a \in \mathbb{R}$
- $a > 0$
- $a \neq 1$

<u>Attenzione</u>: $a > 0$ perché l'esponenziale non è ben definito per basi negative.

## Notazione
> $$\exp_{a}(x) = a^{x}$$
> dove
> $$\exp_{a} : \mathbb{R} \longrightarrow \mathbb{R}^{*}_{+}$$

Se si sceglie $a = e$, ovvero al [[Numero di Nepero|numero di Nepero]] allora si dice che **l'esponenziale è a base naturale**.

## Grafico
```functionplot
---
title: a > 0
xLabel: x
yLabel: y
bounds: [-3,5,-3,5]
disableZoom: false
grid: true
---
f(x) = exp(x)
```

```functionplot
---
title: 0 < a < 1
xLabel: x
yLabel: y
bounds: [-3,5,-3,5]
disableZoom: false
grid: true
---
f(x) = exp(-x)
```


## Casistiche
Ora, a seconda del valore di $x$ si distinguono diversi casi.

### $x \in \mathbb{Q}$
Se $x$ è [[Numeri razionali|razionale]] allora:
- $x \in \mathbb{Q}^{+} \implies x = \frac{n}{m} \implies a^{x}=a^{\frac{n}{m}} = \sqrt[m]{a^{n}}$
- $x \in \mathbb{Q}^{-} \implies x = -\frac{n}{m} \implies a^{x} = a^{-\frac{n}{m}} = \sqrt[m]{\frac{1}{a^{n}}} = \frac{1}{\sqrt[m]{a^{n}}}$

dove in entrambi i casi $n, m \in \mathbb{N}, \ m \neq 0$.

### $x \in \mathbb{R} \setminus \mathbb{Q}$
In questo caso, $x$ è [[Numeri irrazionali|irrazionale]]. Per esempio, se ci troviamo di fronte al caso
$$3^{\sqrt{2}}$$
come facciamo a definirlo?

Ebbene l'idea è di **approssimare $\sqrt{2}$ con una [[Successione monotona|successione crescente]] di numeri razionali**.

Prendendo allora una successione $q_{n}$ che si sviluppa nel seguente modo
![[dimostrazione-rappresentazione-esponenziale-irrazionale.png]]
per cui $A = \{q_{n} | n \in \mathbb{N}\} \in \mathbb{Q}$, notiamo che:
1. la successione è _crescente_
2. la successione è _[[Maggiorante|superiormente limitata]]_
3. la successione si avvicina sempre più a $\sqrt{2}$

Per queste 3 ragioni, come [[Dimostrazione successioni monotone hanno limite#Corollario|conseguenza del limite delle successioni monotone]], si dimostra che $q_{n}$ converge a $\sqrt{2}$. Per cui $3^{q_{n}}$ converge a $3^\sqrt{2}$.

Nel caso generale vale che
> Definita una qualunque successione $q_{n}$, se essa è crescente e superiormente limitata allora **$a^{q_{n}}$ è convergente**.

da cui la definizione
$$a^{r} := \lim_{n \to +\infty} a^{q_{n}}$$

<u>Nota bene</u>: si dimostra che il suddetto limite è _indipendente_ dalla successione $q_{n}$ scelta per approssimare $r$.

## Referenze