---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 02-11-2023 23:14:29
links:
  - "[[Lecture 30102023093826]]"
---
# Teorema di Rolle
---
## Introduzione
> Fissata una [[Funzione matematica|funzione]] $f : [a, b] \to \mathbb{R}$, se
> 1. $f$ [[Funzioni continue|continua]] in $[a, b]$
> 2. $f$ [[Funzioni derivabili|derivabile]] in $]a, b[$
> 3. $f(a) = f(b)$
> 
> allora
> $$\exists c \in ]a, b[ : f'(c) = 0$$
> ovvero **esiste un punto $c$ per cui la [[Derivata|derivata]] di $f$ si annulla**.

## Dimostrazione
Consideriamo una funzione $f : [a, b] \to \mathbb{R}$ continua, per il [[Teorema di Weierstrass|teorema di Weierstrass]] esiste un massimo e un minimo assoluto. Assumiamo quindi $x_{0}$ punto di massimo assoluto e $x_{1}$ punto di minimo assoluto, tale che quindi
$$f(x) \leq f(x_{0}) \ \ \ \ f(x) \geq f(x_{1})$$

Distinguiamo 2 casi:
- massimo e minimo _cadono sugli estremi_ $a$ e $b$
- massimo e minimo non cadono sugli estremi

### 1° caso
Nel primo caso $x_{0} = a$ e $x_{1} = b$, perciò abbiamo
$$f(a) \geq f(x) \geq f(b)$$

Dalle ipotesi sappiamo che $f(a) = f(b)$, per cui si ha
$$f(x) = k$$
da che
$$f'(x) = 0 \ \ \forall x \in [a, b]$$
**Cvd**.

### 2° caso
Nel secondo caso abbiamo un $x_{0} \in ]a, b[$, quindi un [[Punto interno|punto interno]] di $[a, b]$, che è un massimo assoluto. Usando il [[Teorema di Fermat|teorema di Fermat]] sappiamo che $f'(x_{0}) = 0$. Analogamente si prova per $x_{1} \in ]a, b[$.

**Cvd**.

### Ipotesi
Per applicare Rolle è _fondamentale avere $f$ derivabile in $]a, b[$_. Se abbiamo per esempio come funzione il [[Valore assoluto|valore assoluto]] definito in un dominio $[-2, 2]$:
```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-10,10,-10,10]
disableZoom: false
grid: true
---
y=abs(x)
```
ci risulta chiaro che nonostante siano rispettate le altre due ipotesi di Rolle, quindi $f$ continua e $f(a) = f(b)$, non essendo derivabile in $x=0$ il teorema non vale: infatti _non esiste alcun punto di annullamento della derivata prima_.

## Referenze