---
tags:
  - category/note
  - status/finished
  - topic/calcolo-delle-probabilità-e-statistica
date: 28-04-2025 20:19:20
links:
  - "[[Lecture 11042025131834]]"
---
# Distribuzione esponenziale
---
## Introduzione
> La **distribuzione esponenziale** e' una [[Distribuzioni notevoli di variabili aleatorie continue|distribuzione notevole]] su [[Variabile aleatoria continua|variabile aleatoria continua]] $X$. In tal caso, si dice che $X$ ha la legge esponenziale con parametro $\lambda > 0$, e si indica
> $$X \sim Exp(\lambda) \ \ \ \lambda > 0$$

Formalmente, preso come supporto $S_{X} = [0, +\infty)$, la [[Densita' continua|densita' continua]] $f_{X}$ sara' definita come
$$f_{X}(x) = \lambda e^{-\lambda x} \mathbb{1}_{[0, +\infty)}(x)$$
usando la [[Variabile aleatoria indicatrice|variabile aleatoria indicatrice]].

La [[Funzione di ripartizione|funzione di ripartizione]] $F_{X}$, di conseguenza sara' definita come:
$$F_{X}(x) = (1 - e^{-\lambda x}) \mathbb{1}_{(0, +\infty)}(x)$$

## Proprieta'
### Valore atteso
Il [[Valore atteso|valore atteso]] di una variabile aleatoria continua con distribuzione esponenziale e' dato da
$$\mathbb{E}[X] = \frac{1}{\lambda}$$

### Varianza
La [[Varianza|varianza]] di una variabile aleatoria continua con distribuzione esponenziale e' data da
$$Var(X) = \frac{1}{\lambda^{2}}$$

## Referenze