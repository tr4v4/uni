---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 18-03-2024 21:10:04
links:
  - "[[Lecture 14032024140617]]"
---
# Distanza tra punti
---
## Introduzione
> Dati due [[Vettore|vettori]] (o punti) dello [[Spazio euclideo|spazio euclideo]] $\mathbb{R}^{n}$, quindi $x, y \in \mathbb{R}^{n}$, si ha che la **distanza** tra $x$ e $y$ è
> $$\text{dist}(x, y) :=||x-y||$$
> ovvero la _[[Norma euclidea|norma]] della differenza tra di essi_.
> Per definizione di norma possiamo riassumere il calcolo per vettori di $\mathbb{R}^{n}$ in
> $$||x-y|| = \sqrt{\sum\limits_{k=1}^{n} (x_{k}-y_{k})^{2}} = \sqrt{(x_{1}-y_{1})^{2} + \cdots + (x_{n}-y_{n})^{2}}$$

<u>Nota bene</u>: la _distanza tra punti è fondamentale_ per definire il concetto di [[Intorno|intorno]], da cui a loro volta si ottengono i [[Limite|limiti]] e quindi gran parte degli argomenti di [[Analisi I|analisi I]].

<u>Nota bene</u>: utilizzeremo la formula della distanza da punti per il [[Metodo dei minimi quadrati|metodo dei minimi quadrati]], una tecnica per risolvere [[Sistema lineare|sistemi lineari]].

## Punto di minima distanza da una retta
Consideriamo un vettore $v \in \mathbb{R}^{n}: v \neq \underline{0}$ e un vettore $x \in \mathbb{R}^{n}$. Costruiamo la retta passante per $v$ come
$$l_{v} = \{\lambda v | \lambda \in \mathbb{R}\}$$[^1]

Tra tutti i _punti di $l_{v}$ dobbiamo cercare quello che ha minima distanza da $x$_. Vogliamo allora **minimizzare** la funzione
$$h: \mathbb{R} \to \mathbb{R}, \ h(\lambda) = ||x - \lambda v|| = \text{dist}(x, \lambda v)$$

Considero allora la funzione
$$g(\lambda) = h^{2}(\lambda) = ||x - \lambda v||^{2}$$
e la calcolo usando la formula del [[Quadrato di un binomio|quadrato di un binomio]] generalizzata a vettori, per cui ho
$$g(\lambda) = ||x - \lambda v||^{2} = ||x||^{2} + ||\lambda v||^{2} + 2(x \cdot (- \lambda v)) = ||x||^{2} + \lambda^{2}||v||^{2} - 2 \lambda(x \cdot v)$$

Notiamo che essendo $\lambda^{2}$ un termine di $g(\lambda)$, si tratta di una _parabola con concavità in alto_, per cui se vogliamo sapere il punto minimo ci basta calcolare la derivata e porla a 0!
Infatti si ha
$$g'(\lambda) = 2 \lambda ||v||^{2} - 2xv$$
per cui
$$g'(\lambda) = 0 \iff \lambda = \frac{xv}{||v||^{2}}$$
che è quindi l'unico punto di minimo, locale e assoluto. Allora il punto che minimizza la distanza tra $l_{v}$ e $x$ è proprio
$$\lambda v = \frac{xv}{||v||^{2}} \cdot v \in l_{v}$$

Allora si ha che la distanza è data da
$$\text{dist}(x, \underline{\lambda}v)^{2} = g(\underline{\lambda}) = |x - \frac{xv}{|v|^{2}}v|^{2} = |x|^{2} + \frac{(xv)^{2}}{|v|^{4}} |v|^{2} - 2x \frac{xv}{|v|^{2}}v = |x|^{2} + \frac{(xv)^{2}}{|v|^{2}} - 2\frac{xv}{|v|^{2}}xv = |x|^{2} - \frac{(xv)^{2}}{|v|^{2}}$$

da cui
$$\text{dist}(x, \lambda v) = \sqrt{|x|^{2} - \frac{(xv)^{2}}{|v|^{2}}}$$

## Referenze
[^1]: letteralmente un [[Sottospazio vettoriale|sottospazio vettoriale]] di $\mathbb{R}^{n}$