---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 27-02-2024 19:53:31
links:
  - "[[Lecture 26022024130925]]"
---
# Caratterizzazione delle primitive su un intervallo
---
## Introduzione
> Sia $f: ]a, b[ \to \mathbb{R}$ una [[Funzione matematica|funzione]] e siano $F: ]a, b[ \to \mathbb{R}$ e $G: ]a, b[ \to \mathbb{R}$ due [[Primitiva|primitive]] di $f$ su $]a, b[$, allora la **caratterizzazione delle primitive su un intervallo** ci dice che
> $$\exists k \in \mathbb{R} : G(x) = F(x) + k \ \ \ \forall x \in ]a, b[$$
> ovvero, informalmente, _$F$ e $G$ differiscono per una costante $k$_.

## Dimostrazione
Considero $H: ]a, b[ \to \mathbb{R}$ come $H(x) = G(x) - F(x)$. Dalle ipotesi sappiamo che $F'(x) = f(x) \land G'(x) = f(x) \ \ \ \forall x \in ]a, b[$, perciò $H'(x) = f(x) - f(x) = 0 \ \ \ \forall x \in ]a, b[$: dal [[Teorema di Lagrange#Corollario|corollario del teorema di Lagrange]] otteniamo che _$H$ è una funzione costante_, e che perciò $\exists k \in \mathbb{R}: H(x) = k \ \ \ \forall x$. Questo, per la definizione di $H$, implica che
$$G(x) - F(x) = k \ \ \ \forall x \in ]a, b[$$

## Osservazione
E' importante notare che _questa caratterizzazione può valere solo se si lavora su intervalli_. In caso contrario potrebbero esserci casi in cui $\nexists k \in ]a, b[: G(x) - F(x) = k$.

Prendiamo in esame $f(x) = \frac{1}{x^{2}}$, e consideriamo le due primitive $F(x) = - \frac{1}{x}$ e $G(x) = \begin{cases} -\frac{1}{x} & x > 0 \\ - \frac{1}{x} + 3 & x < 0 \end{cases}$, per cui risulta $G'(x) = F'(x) = \frac{1}{x^{2}} \ \ \ \forall x \in \mathbb{R} \setminus \{0\}$. Non è possibile trovare una costante $k$ t.c. $G(x) - F(x) = k \ \ \ \forall x \in \mathbb{R} \setminus \{0\}$. Infatti ho
$$\begin{cases} G(x) - F(x) = 0 & x > 0 \\ G(x) - F(x) = 3 & x < 0 \end{cases}$$

## Referenze