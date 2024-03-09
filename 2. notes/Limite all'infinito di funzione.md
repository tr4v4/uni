---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 19-10-2023 20:58:38
links:
  - "[[Lecture 16102023093744]]"
---
# Limite all'infinito di funzione
---
## Premessa
Affinché il limite possa andare all'infinito, _il dominio deve consentire a $x$ di tendere a $\pm \infty$_. Ovvero:
$$\sup D = \pm \infty$$

## Tipologie
- [[Limite finito all'infinito di funzione]]
- [[Limite infinito all'infinito di funzione]]

## Casi standard
- $\lim_{x \to +\infty} x^{n} = +\infty, \ \ \forall n \in \mathbb{N}$
- $\lim_{x \to -\infty} x^{n} = \begin{cases} +\infty \text{ se n è pari} \\ -\infty \text{ se n è dispari} \end{cases}, \ \ \forall n \in \mathbb{N}$
- $\lim_{x \to \pm\infty} P(x) = \text{dipende}$, dove $P$ è un polinomio
	- se $P$ di grado pari --> $+\infty$ per ogni tendenza di $x$ (sia $+\infty$ che $-\infty$)
	- se $P$ di grado dispari --> $+\infty$ se $x$ tende a $+\infty$; $-\infty$ se $x$ tende a $-\infty$
	- in generale vale che per risolverle si raccoglie il monomio di grado maggiore
- $\lim_{x \to \pm\infty} \frac{P(x)}{D(x)} = \text{ dipende}$
	- anche in questo caso vale che sia al numeratore che al denominatore si raccoglie il monomio di grado massimo

## Confronto di funzioni
Se si hanno due funzioni che tendono a $+\infty$ e si vuole capire quale cresce più velocemente _si fa il limite del rapporto_. Si ottiene così che:
$$\lim_{x \to +\infty} \frac{f(x)}{g(x)} = \begin{cases} 0 & g(x) \text{ cresce più velocemente} \\ +\infty & f(x) \text{ cresce più velocemente} \\ l \neq 0 & f(x) \text{ e } g(x)\text{ sono infiniti dello stesso ordine} \end{cases}$$

Far sempre riferimento alla [[Gerarchia degli infiniti|gerarchia degli infiniti]].

## Referenze