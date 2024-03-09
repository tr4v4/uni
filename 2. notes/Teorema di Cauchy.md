---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 02-11-2023 23:42:56
links:
  - "[[Lecture 30102023093826]]"
---
# Teorema di Cauchy
---
## Introduzione
> Fissate le [[Funzione matematica|funzioni]] $f, g : [a, b] \to \mathbb{R}$, se
> 1. $f, g$ [[Funzioni continue|continue]] in $[a, b]$
> 2. $f, g$ [[Funzioni derivabili|derivabili]] in $]a, b[$
> 3. $g'(x) \neq 0 \ \ \ \forall x \in ]a, b[$
> 
> allora
> $$\exists c \in ]a, b[ : \frac{f(b) - f(a)}{g(b) - g(a)}= \frac{f'(c)}{g'(c)}$$

## Dimostrazione
Per dimostrare il teorema di Cauchy agiamo analogamente alla dimostrazione del [[Teorema di Lagrange|teorema di Lagrange]], andando a costruire una _funzione ausiliaria $g(x)$_ per la quale è possibile applicare il [[Teorema di Rolle|teorema di Rolle]].

Per cui consideriamo la funzione $h: [a, b] \to \mathbb{R}$
$$h(x) = f(x) + k \cdot g(x)$$
Da cui ricaviamo che essa è continua in $[a, b]$ e derivabile in $]a, b[$. Per applicare Rolle dobbiamo garantire che $h(a) = h(b)$, per cui uguagliamo le due funzioni
$$f(a) + k \cdot g(a) = f(b) + k \cdot g(b)$$
ottenendo
$$k = \frac{f(b) - f(a)}{g(a) - g(b)}$$

Per Rolle, allora, esiste un $c \in ]a, b[$ per cui $h'(c) = 0$, ovvero
$$f'(c) + k \cdot g'(c) = 0$$

Sostituendo il valore di $k$ si ottiene proprio
$$\frac{f(b) - f(a)}{g(b) - g(a)}= \frac{f'(c)}{g'(c)}$$
dimostrando il teorema di Cauchy.

**Cvd**.

### Ipotesi
Notare bene il _ruolo della terza ipotesi del teorema $g'(x) \neq 0 \ \ \ \forall x \in ]a, b[$_. Esso non solo permette, nell'ultimo passaggio della dimostrazione, di dividere per $g'(c)$, ma garantisce che $g(b) - g(a) \neq 0$. Questo perché se $g(a) = g(b)$ allora per il teorema di Rolle, essendo $g$ sia continua che derivabile, si avrebbe $g'(x) = 0$, in contraddizione con l'ipotesi.

## Referenze