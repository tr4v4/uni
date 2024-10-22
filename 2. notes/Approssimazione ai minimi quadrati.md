---
tags:
  - category/note
  - status/ongoing
  - topic/calcolo-numerico
date: 21-10-2024 12:51:57
links:
  - "[[Lecture 14102024131954]]"
---
# Approssimazione ai minimi quadrati
---
## Introduzione
> L'**approssimazione ai minimi quadrati** è un [[Approssimazione di dati|metodo di approssimazione di dati]] che consiste nel trasformare il problema dell'approssimazione in quello della [[Problema dei minimi quadrati|ricerca dei minimi quadrati]].

## Idea
Come requisito assumiamo che la funzione da approssimare sia $f(x)$ e che $f_{\theta}(x)$ sia il modello _[[Polinomio|polinomiale]]_ che vogliamo avvicinare a $f(x)$. Se consideriamo $\alpha = (a_{0}, a_{1}, \cdots, a_{d})$ il vettore $\in \mathbb{R}^{d+1}$ dei coefficienti, allora
$$f_{\theta}(x, \alpha) = \sum\limits_{k=0}^{d} a_{k}x^{k}$$

Se definiamo
$$x^{(d)} = (x^{0}, x^{1}, \cdots, x^{d}) \in \mathbb{R}^{d+1}$$

allora possiamo definire $f_{\theta}(x, \alpha)$ come il [[Prodotto scalare|prodotto scalare]] tra i vettori $\alpha$ e $x^{(d)}$:
$$f_{\theta}(x, \alpha) = \alpha^{T}x^{(d)}$$

Detto ciò, lo scopo iniziale è di approssimare $f_{\theta}(x, \alpha)$ a $f(x)$, ovvero di _trovare il vettore dei coefficienti $\alpha$ tale che minimizzi $f_{\theta}(x_{i}, \alpha) - f(x_{i}) \ \ \ \forall i \in \{1, \cdots, n\}$_, dove $n$ è il numero di variabili indipendenti (dati in input). In altre parole si cerca $\alpha$ tale che:
$$\min_{\alpha} \sum\limits_{i=1}^{n} (f_{\theta}(x_{i}, \alpha) - y_{i})^{2}$$

<u>Nota bene</u>: facciamo la somma tra i quadrati perché è semplicemente più comodo, di fatto ci vogliamo ricondurre ai minimi quadrati.

Ricordando $f_{\theta}(x, \alpha) = \alpha^{T}x^{(d)}$, allora il problema diventa
$$\min_{\alpha} \sum\limits_{i=1}^{n} (\alpha^{T} x^{(d)}_{i} - y_{i})^{2}$$

## Referenze