---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 04-10-2024 16:10:58
links:
  - "[[Lecture 30092024131914]]"
---
# Norma matriciale
---
## Introduzione
> Per **norma matriciale**, un'estensione della [[Norma vettoriale|norma vettoriale]], si intende una generica [[Funzione matematica|funzione]]
> $$\| \cdot \|: \mathbb{R}^{n} \times \mathbb{R}^{m} \to \mathbb{R}$$
> tale che:
> 1. $\|A\| \geq 0 \ \ \ \forall A \in \mathbb{R}^{n \times m}, \|A\| = 0 \iff A = \underline{\underline{0}}$
> 2. $\alpha \in \mathbb{R}, \|\alpha A\| = |\alpha| \|A\|$
> 3. $\forall A, B \in \mathbb{R}^{n \times m}, \|A+B\| \leq \|A\| + \|B\|$ ([[Disuguaglianza triangolare|disuguaglianza triangolare]])

## Tipologie
Le più importanti norme matriciali sono:
- **[[Norma di Frobenius|norma di Frobenius]]** --> $\|A\|_{F} = \sqrt{\sum\limits_{i=1}^{m}{\sum\limits_{j=1}^{n}{{a_{ij}}^{2}}}}$, ossia l'equivalente matriciale della [[Norma euclidea|norma euclidea]];
- **norma 2** --> $\|A\|_{2} = \sqrt{p(A^{T}A)}$ dove $p(M)$ è il [[Raggio spettrale|raggio spettrale]], ossia il _massimo [[Autovalore|autovalore]] in modulo_;
- **norma 1** --> $\|A\|_{1} = \max_{1 \leq i \leq m} \sum\limits_{j=1}^{n}{|a_{ij}|}$

## Referenze