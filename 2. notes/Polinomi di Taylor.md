---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 16-11-2023 22:06:55
links:
  - "[[Lecture 13112023094129]]"
  - "[[Lecture 17112023134446]]"
---
# Polinomi di Taylor
---
## Sviluppi
### $e^{t}$
$$e^{t} = \sum\limits_{j = 0}^{n} \frac{1}{j!} t^{j} + o(t^{n})$$ $$e^{t} = 1 + t + \frac{t^{2}}{2!} + \frac{t^{3}}{3!} + \frac{t^{4}}{4!} + ... + o(t^{n})$$

### $\sin(t)$
$$\sin(t) = \sum\limits_{j = 0}^{n} \frac{(-1)^{j} \cdot t^{2j+1}}{(2j + 1)!} + o(t^{2n+1})$$
$$\sin(t) = t - \frac{t^{3}}{3!} + \frac{t^{5}}{5!} - \frac{t^{7}}{7!} + ... + o(t^{2n+1})$$

<u>Da notare</u> che il seno è una [[Disparità di una funzione|funzione dispari]], e in quanto tale _il suo sviluppo prevede solo monomi di grado dispari_. Ciò è riscontrabile nella [[Derivata|derivazione]] _ciclica_ del seno[^1], che annullandosi per $t = 0$ fa sparire tutti i monomi di grado pari.

Sempre per questo motivo, l'errore ([[O-piccolo|o-piccolo]]) $o(t^{2n+1})$ potrà estendersi a $o(t^{2n+2})$, ottenendo un grado di precisazione in più. Infatti, il monomio di grado $2n+2$, di grado quindi pari, sarà nullo e lascerà solo il suo o-piccolo $o(t^{2n+2})$.
Questo significa che il polinomio fino al grado $n$ approssima la funzione con un errore pari a quello che approssimerebbe il polinomio del grado $n+1$, di fatto identico a quello di grado $n$.

Altra osservazione: se vogliamo sviluppare il seno a un grado $m$, dobbiamo ricordarci che, venendo presi in considerazione solo i monomi dispari, ci **basteranno $n = \frac{m-1}{2}$ ordini di sviluppo**.

### $\cos(t)$
$$\cos(t) = \sum\limits_{j = 0}^{n} \frac{(-1)^{j} \cdot t^{2j}}{(2j)!} + o(t^{2n})$$
$$\cos(t) = 1 - \frac{t^{2}}{2!} + \frac{t^{4}}{4!} - \frac{t^{6}}{6!} + ... + o(t^{2n})$$

<u>Da notare</u> che al contrario del seno, il coseno in quanto [[Parità di una funzione|funzione pari]] ha uno _sviluppo che prevede solo monomi di grado pari_.

Per le stesse ragioni del seno, anche per il coseno l'errore $o(t^{2n})$, per un qualsiasi _ordine di sviluppo_ $n$, si può precisare in $o(t^{2n+1})$.

Altra osservazione: come avviene per il seno, se vogliamo sviluppare il coseno a un grado $m$, dobbiamo ricordarci che, venendo presi in considerazione solo i monomi pari, ci **basteranno $n = \frac{m}{2} + 1$ ordini di sviluppo**.

### $\ln(1 + t)$
$$\ln(1 + t) = \sum\limits_{j = 1}^{n} \frac{(-1)^{j-1}}{j} t^{j} + o(t^{n})$$
$$\ln(1 + t) = t - \frac{t^{2}}{2} + \frac{t^{3}}{3} - \frac{t^{4}}{4} + ... + o(t^{n})$$

<u>Da notare</u> che non possiamo sviluppare $\ln$ nell'origine, in quanto non è un punto del suo [[Dominio naturale|dominio naturale]] e quindi neanche [[Funzioni derivabili|derivabile]] in $x = 0$. Possiamo però sviluppare per $1 + t$ nell'origine.

### $(1 + t)^{\alpha}$
$$(1 + t)^{\alpha} = \sum\limits_{j = 0}^{n} \binom{\alpha}{j} \cdot t^{j} + o(t^{n}) \ \ \ \ (\alpha \in \mathbb{R})$$
$$(1+t)^{\alpha} = 1 + \alpha t + \frac{\alpha \cdot (\alpha-1)}{2} t^{2} + \frac{\alpha \cdot (\alpha-1) \cdot (\alpha-2)}{6} t^{3} + ... + o(t^{n})$$

Questo sviluppo è di estrema utilità perché è una forma che **per $\alpha \in \mathbb{R}$** si ottiene spesso. Per $\alpha \in \mathbb{N}$ sappiamo che essa corrisponde al [[Binomio di Newton|binomio di Netwon]] (da questo la _somiglianza_); l'unica cosa da modificare sta nella scrittura del [[Coefficiente binomiale|coefficiente binomiale]], che per $\alpha \in \mathbb{R}$ non può essere rappresentata come
$$\frac{\alpha!}{(\alpha-j)!j!}$$
ma piuttosto come
$$\frac{\alpha \cdot (\alpha - 1) \cdot (\alpha - 2) \cdot ... \cdot (\alpha - j + 1)}{j!}$$
(_coefficiente binomiale generalizzato_).

<u>Ricorda</u>: $\binom{\alpha}{0} = 1$

## Osservazioni
Fare attenzione a funzioni elementari composte, per i quali è necessario applicare una sostituzione per $t$. In tal caso, **la sostituzione è valida sse la variabile sostituita tende a 0**, così da far tendere anche $t$ a 0. Infatti ricordiamoci che _questi sviluppi valgono solo per l'origine_.

## Referenze
- [[Teorema di Peano]]
- [[Sviluppo in serie di Taylor]]

[^1]: appartenente infatti a $C^{\infty}$ ([[Classe C]])