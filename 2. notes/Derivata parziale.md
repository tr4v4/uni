---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 29-03-2024 16:17:02
links:
  - "[[Lecture 18032024130735]]"
  - "[[Lecture 21032024140949]]"
---
# Derivata parziale
---
## Introduzione
> Sia $A \subseteq \mathbb{R}^{2}$ [[Insieme|insieme]] [[Insieme aperto|aperto]], e $(\bar{x}, \bar{y}) \in A$. Si dice allora che $f: A \to \mathbb{R}$ ([[Funzione a più variabili|funzione a più variabili]]) è **derivabile parzialmente rispetto a $x$** se
> $$\exists \lim_{h \to 0} \frac{f(\bar{x}+h, \bar{y}) - f(\bar{x}, \bar{y})}{h} \in \mathbb{R}$$
> e tale limite si indica con
> $$\frac{\partial f}{\partial x}(\bar{x}, \bar{y}) = \partial_{x}f(\bar{x}, \bar{y}) = D_{x}f(\bar{x}, \bar{y}) = f_{x}(\bar{x}, \bar{y})$$.
> Si dice invece che $f: A \to \mathbb{R}$ è **derivabile parzialmente rispetto a $y$** se
> $$\exists \lim_{h \to 0} \frac{f(\bar{x}, \bar{y}+h) - f(\bar{x}, \bar{y})}{h} \in \mathbb{R}$$
> e tale limite si indica con
> $$\frac{\partial f}{\partial y}(\bar{x}, \bar{y}) = \partial_{y}f(\bar{x}, \bar{y}) = D_{y}f(\bar{x}, \bar{y}) = f_{y}(\bar{x}, \bar{y})$$

## Calcolo
Per calcolare una derivata parziale rispetto a una variabile è dimostrabile che **basta fare il calcolo della [[Derivata|derivata a 1 variabile]] considerando come costante l'altra variabile**.

Geometricamente parlando, prendendo in esame una derivata parziale di una funzione $f: \mathbb{R}^{2} \to \mathbb{R}$ rispetto a una variabile per un punto $v$, questa è un **piano di equazione che nell'equazione del piano passante per un punto è tangente ad $f$ per $v$**.

<u>Nota bene</u>: ricorda che il calcolo della derivata avviene _sempre con limite del rapporto incrementale_.

## Derivate parziali in $\mathbb{R}^{n}$
Nel caso ci trovassimo in $\mathbb{R}^{n}$ con $n > 2$ potremmo usare una _legge che ci consente di semplificare il calcolo della derivata parziale rispetto a una $k$-esima variabile per $k \in \{1, \cdots, n\}$_.

Presa la [[Base canonica|base canonica]] di $\mathbb{R}^{n}$ composta da $e_{1} = (1, 0, \cdots, 0), \cdots, e_{n} = (0, \cdots, 0, 1)$, allora definiamo la derivata rispetto a a una $k$-esima variabile per un punto $\bar{x} \in \mathbb{R}^{n}$ nel seguente modo
$$\partial_{k}f(\bar{x}) = \lim_{t \to 0} \frac{f(\bar{x} + t \cdot e_{k}) - f(\bar{x})}{t}$$
dove $\bar{x} + t \cdot e_{k} = (\bar{x}_{1}, \cdots, \bar{x}_{k-1}, \bar{x}_{k}+t, \bar{x}_{k+1}, \cdots, \bar{x}_{n})$.

<u>Nota bene</u>: è semplicemente un modo compatto di definire una derivata parziale in $\mathbb{R}^{n}$ rispetto a una $k$-esima variabile.

## Referenze
- [[Gradiente]]