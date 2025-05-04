---
tags:
  - category/note
  - status/finished
  - topic/calcolo-delle-probabilità-e-statistica
date: 28-04-2025 20:27:38
links:
  - "[[Lecture 11042025131834]]"
---
# Distribuzione normale
---
## Introduzione
> La **distribuzione normale** e' una [[Distribuzioni notevoli di variabili aleatorie continue|distribuzione notevole]] su [[Variabile aleatoria continua|variabile aleatoria continua]] $X$. In tal caso, si dice che $X$ ha la _legge normale_ con parametri $\mu \in \mathbb{R}$ e $\sigma^{2} > 0$, e si indica
> $$X \sim \mathcal{N}(\mu, \sigma^{2}) \ \ \ \sigma^{2} > 0$$

Formalmente, preso come supporto $S_{X} = \mathbb{R}$, la [[Densita' continua|densita' continua]] $f_{X}$ sara' definita come
$$f_{X}(x) = \frac{1}{\sigma\sqrt{2 \pi}} e^{- \frac{(x - \mu)^{2}}{2 \sigma^{2}}}$$

Invece, la [[Funzione di ripartizione|funzione di ripartizione]] $F_{X}$, e' definita come
$$F_{X}(x) = \int_{-\infty}^{x} \frac{1}{\sigma\sqrt{2 \pi}} e^{- \frac{(y - \mu)^{2}}{2 \sigma^{2}}} \, dy$$
che non ha una forma chiusa, ma si puo' calcolare numericamente.

Una particolare distribuzione normale e' la [[Distribuzione normale standard|distribuzione normale standard]].

## Proprieta'
### Valore atteso
Si dimostra che il [[Valore atteso|valore atteso]] di una variabile aleatoria continua con distribuzione normale e' proprio
$$\mathbb{E}[X] = \mu$$

### Varianza
Si dimostra che la [[Varianza|varianza]] di una variabile aleatoria continua con distribuzione normale e' proprio
$$Var(X) = \sigma^{2}$$
ossia la [[Deviazione standard|deviazione standard]] al quadrato.

### $\mu$
Questo, oltre a indicare la media, indica il punto di massimo della [[Densita' continua|densita' continua]], e quindi il centro della curva gaussiana, il punto di simmetria della distribuzione.

### $\sigma$
Questo, oltre a indicare la [[Deviazione standard|deviazione standard]], indica il raggio della curva gaussiana, e quindi la sua ampiezza. In particolare, piu' $\sigma$ e' grande, piu' la curva e' piatta.

## Referenze