---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 10-11-2024 15:27:07
links:
  - "[[Lecture 22102024092339]]"
---
# Funzione convessa
---
## Introduzione
> Una [[Funzione matematica|funzione]] ([[Funzione a più variabili|a più variabili]]) $f: \mathbb{R}^{n} \to \mathbb{R}$ si dice **convessa** se
> $$\forall \lambda \in [0, 1]. \forall x, y \in \mathbb{R}^{n}. \ \ \ f(\lambda x + (1-\lambda)y) \leq \lambda f(x) + (1-\lambda)f(y)$$

Anche se criptica, è facile capire cosa significa: $f(\lambda x + (1-\lambda)y)$, per un $\lambda$ che varia da 0 a 1, rappresenta tutti i punti della funzione da $x$ a $y$; $\lambda f(x) + (1-\lambda)f(y)$, sempre per un $\lambda$ che varia da 0 a 1, rappresenta tutti i punti della retta da $f(x)$ a $f(y)$.
![[funzione-convessa.png]]

## Caratterizzazione
Se $f(x)$ è _sufficientemente "liscia"_, è possibile distinguere funzioni convesse da non convesse calcolandone l'[[Matrice hessiana|hessiana]].
> Una funzione $f \in C^{2}(\mathbb{R}^{n})$[^1] è convessa $\iff$ la matrice hessiana $H_{f}(x_{0}) = (\nabla^{2}f(x_{0}))_{i,j} \ \ \forall x_{0} \in \mathbb{R}^{n}$ è [[Classificazione forme quadratiche|semi-definita positiva]], ossia $\forall x \in \mathbb{R}^{n} \ \ \ x^{T}H_{f}(x_{0})x \geq 0$.

## Calcolo
Dal teorema precedente, per funzioni $f: \mathbb{R} \to \mathbb{R}$ è facile verificare la convessità: basta calcolarsi la [[Derivata|derivata seconda]] e vedere se è sempre $\geq 0$.

## Referenze
[^1]: [[Classe C|classe C]]