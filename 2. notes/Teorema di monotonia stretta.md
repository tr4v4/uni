---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 04-11-2023 12:54:56
links:
  - "[[Lecture 03112023134932]]"
---
# Teorema di monotonia stretta
---
## Introduzione
> Fissata una [[Funzione matematica|funzione]] $f : ]a, b[ \to \mathbb{R}$ [[Funzioni derivabili|derivabile]], se
> 1. $f'(x) \geq 0 \ \ \ \forall x \in ]a, b[$ ([[Funzioni monotone|funzione crescente]])
> 2. $N = \{x \in ]a, b[ : f'(x) = 0\}$ _finito_
> 
> allora
> $$f \text{ strettamente crescente}$$
> ovvero, **se si ha una funzione crescente cui derivata prima si annulla un numero finito di volte allora essa è strettamente crescente**.
> Ovviamente il _teorema vale ribaltato per le funzioni decrescenti e strettamente decrescenti_.

Questo teorema risulta fondamentale nella distinzione tra le funzioni monotone e le funzioni strettamente monotone.

## Dimostrazione
Per dimostrare il teorema (solo il caso della crescenza) assumiamo di avere una funzione $f : ]a, b[$ crescente, e per contraddizione supponiamo che essa non sia strettamente crescente. Per la definizione di crescenza vorrebbe dire che potenzialmente
$$\exists x_{1}, x_{2} \in ]a, b[ : x_{1} < x_{2} \implies f(x_{1}) = f(x_{2})$$
Essendo $f$ crescente avremo allora che
$$\forall x \in ]x_{1}, x_{2}[ : f(x_{1}) \leq f(x) \leq f(x_{2})$$
ovvero, in quanto $f(x_{1}) = f(x_{2})$, $f(x)$ è **costante** su $[x_{1}, x_{2}]$. Vale a dire
$$f'(x) = 0 \ \ \ \forall x \in ]x_{1}, x_{2}[$$
in contraddizione con l'ipotesi $N = \{x \in ]a, b[ : f'(x) = 0\}$ _finito_.

**Cvd**.

## Referenze