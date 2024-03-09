---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 02-11-2023 23:30:29
links:
  - "[[Lecture 30102023093826]]"
---
# Teorema di Lagrange
---
## Introduzione
> Fissata una [[Funzione matematica|funzione]] $f : [a, b] \to \mathbb{R}$, se
> 1. $f$ [[Funzioni continue|continua]] in $[a, b]$
> 2. $f$ [[Funzioni derivabili|derivabile]] in $]a, b[$
> 
> allora
> $$\exists c \in ]a, b[ : f'(c) = \frac{f(b) - f(a)}{b-a}$$

## Dimostrazione
Per dimostrare il teorema di Lagrange dobbiamo costruire una _funzione ausiliaria_ a partire da $f$ a cui possiamo applicare il [[Teorema di Rolle|teorema di Rolle]].
Scegliamo quindi $g(x) : [a, b] \to \mathbb{R}$ in modo che
$$g(x) = f(x) + k \cdot x \ \ \ (k \in \mathbb{R})$$

L'obiettivo ora è trovare un valore $k$ tale che $g(a) = g(b)$, per il quale possiamo quindi applicare Rolle. Sappiamo infatti che _$g$ è continua in $[a, b]$ e derivabile in $]a, b[$_.
Affinche $g(a) = g(b)$, dobbiamo avere
$$f(a) + k \cdot a = f(b) + k \cdot b$$
ovvero
$$k = \frac{f(a) - f(b)}{b - a}$$

Definito $k$, dal teorema di Rolle abbiamo che $g'(c) = 0$, da cui
$$f'(c) + k = 0$$[^1]

sostituendo il valore di $k$ calcolato si ha
$$f'(c) = \frac{f(b) - f(a)}{b - a}$$
che dimostra il teorema di Lagrange.

**Cvd**.

## Corollario
> Se abbiamo una funzione $f: [a, b] \to \mathbb{R}$ derivabile t.c. $f'(x) = 0 \ \ \forall x \in ]a, b[$, allora $f$ è **costante** su $]a, b[$.

### Dimostrazione
Avendo $f$ derivabile allora essa è anche continua in $[a, b]$. Possiamo quindi applicare Lagrange, ottenendo che
$$\exists c \in ]a, b[ : f'(c) = \frac{f(b) - f(a)}{b-a}$$

Dalle ipotesi sappiamo che $f'(x) = 0 \ \ \forall x \in ]a, b[$, per cui anche $f'(c) = 0$.
Da cui
$$\frac{f(b) - f(a)}{b-a} = 0 \implies f(b) = f(a)$$

**Cvd**.

### Ipotesi
Bisogna fare attenzione alle ipotesi del corollario. Una funzione cui derivata è sempre nulla in un determinato intervallo **non garantisce che $f$ sia costante sempre su uno stesso valore**.
Presa per esempio la funzione
$$f(x) = \arctan(x) + \arctan(\frac{1}{x})$$
il grafico risultante risulta essere il seguente
```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-10,10,-10,10]
disableZoom: false
grid: true
---
y=atan(x) + atan(1/x)
```

La funzione è derivabile e anche continua nell'intervallo $[-2, 2]$ (ricordiamo $D = x \neq 0$), e la derivata è sempre $f'(x) = 0$. La funzione in effetti è costante, ma su due livelli!

## Referenze
[^1]: $k$ e non $kc$ perché stiamo facendo la [[Derivata|derivata]] di $g(x)$, quindi rimane solo $k$