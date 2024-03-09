---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 26-02-2024 20:15:00
links:
  - "[[Lecture 19022024130000]]"
  - "[[Lecture 26022024130925]]"
---
# Teorema della media integrale
---
## Introduzione
> Sia $f: [a, b] \to \mathbb{R}$ una [[Funzione matematica|funzione]] [[Funzioni continue|continua]], allora per il **teorema della media integrale** si ha che
> $$\exists c \in [a, b] : \frac{1}{b-a} \int_{a}^{b} f(x) \ dx = f(c)$$
> o meglio
> $$\int_{a}^{b} f(x) \ dx = (b-a) \cdot f(c)$$

Il teorema quindi ci dice che preso un intervallo $[a, b]$ su qualunque funzione continua, ci sarà sempre un valore $c$ tale per cui $(b-a) \cdot f(c)$ sarà uguale all'integrale di $f$ in $[a, b]$.
![[teorema-media-integrale.png|500]]

## Spiegazione
Il teorema si chiama della "media" integrale perché guardando alla [[Integrale di Riemann|definizione di integrale di Riemann]] si ha che
$$\frac{1}{b-a} \int_{a}^{b} f(x) \ dx = \frac{1}{b-a} \lim_{n \to +\infty} \sum\limits_{k=1}^{n} f(\xi_{k}) \cdot \frac{b-a}{n} = \lim_{n \to +\infty} \sum\limits_{k=1}^{n} \frac{f(\xi_{k})}{n}$$
ovvero di fatto la media delle altezze. Stiamo dicendo allora che _esiste un punto $c \in [a, b]$ che è la media delle altezze della funzione in $[f(a), f(b)]$_.

## Dimostrazione
### Premesse
Per dimostrare il teorema è necessario ricordare due teoremi:
- [[Teorema dei valori intermedi]]
- [[Teorema di Weierstrass]]

### Corpo
Procedo con la dimostrazione applicando Weierstrass agli integrali. Se so infatti che presa una $f$ continua in $[a, b]$ esiste un $x_{1}$ e un $x_{2}$ (_massimi e minimi locali_) oltre il quale $f(x)$ non può andare ($\forall x \in [a, b]$), allora posso dire la stessa cosa dell'integrale di $f$ in $[a, b]$, ovvero:
$$\int_{a}^{b} f(x_{1}) \ dx \leq \int_{a}^{b} f(x) \ dx \leq \int_{a}^{b} f(x_{2}) \ dx$$
Sapendo che $f(x_{1})$ e $f(x_{2})$, posso riscrivere la disequazione come
$$(b-a) \cdot f(x_{1}) \leq \int_{a}^{b} f(x) \ dx \leq (b-a) \cdot f(x_{2})$$
A questo punto divido per $(b-a)$ e ottengo
$$f(x_{1}) \leq \frac{1}{b-a} \int_{a}^{b} f(x) \ dx \leq f(x_{2})$$
Assegno allora
$$y = \frac{1}{b-a} \int_{a}^{b} f(x) \ dx \in [f(x_{1}), f(x_{2})]$$
perciò per il teorema dei valori intermedi ho
$$\exists c \in [a, b] : f(c) = y$$
ovvero esattamente quello che stavamo cercando di dimostrare.

**Qed**.

## Osservazioni
Nota che se $b < a$, per via della [[Integrale#Inverso|proprietà dell'inverso dell'integrale]], vale che
$$\frac{1}{b-a} \int_{a}^{b} f = \frac{1}{a-b} \int_{b}^{a} f$$

Nota anche che _la continuità di $f$ è necessaria_. Se prendiamo per esempio $f: [-1, 1] \to \mathbb{R}$ definita come $f(x) = \begin{cases} x & x \neq 0 \\ 2 & x = 0 \end{cases}$, sappiamo che $\int_{-1}^{-1} f(x) \ dx = 0$, _ma non esiste alcun punto $c \in [-1, 1] : f(c) = 0$_.

## Referenze