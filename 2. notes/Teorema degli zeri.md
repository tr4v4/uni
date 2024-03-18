---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 21-10-2023 16:06:09
links:
  - "[[Lecture 20102023135306]]"
  - "[[Lecture 23102023094009]]"
  - "[[Lecture 06112023094954]]"
---
# Teorema degli zeri
---
## Introduzione
Il **teorema degli zeri** ci assicura che presa una [[Funzioni continue|funzione continua]] in un _intervallo chiuso e limitato_ contenuto del dominio e per il quale sappiamo che _la funzione agli estremi dell'intervallo assume valori di segno opposto_, allora esiste un valore nell'intervallo per il quale la funzione si annulla.

Ovvero
$$f: [a, b] \longrightarrow \mathbb{R} \text{ continua, } f(a) \cdot f(b) < 0 \implies \exists c \in ]a, b[ : f(c) = 0$$

Questo risulta ovvio alla vista, ma è comunque da dimostrare.

## Dimostrazione
Per poter dimostrare il teorema abbiamo prima bisogno di introdurre alcuni risultati preliminari.

### Lemmi
#### 1
Presa una [[Successione numerica|successione]] $(b_{n})_{n}$:
$$b_{n} < 0 \ \ \forall n, \ \ \ \lim_{n \to +\infty} b_{n} = l \in \mathbb{R} \implies l \leq 0$$[^1]

Ovviamente lo stesso discorso vale specchiato per $b_{n} > 0 \ \ \forall n$.

#### 2
Se una funzione $f(x)$ è continua in $\bar{x}$ allora per ogni valore di una successione che tende a $\bar{x}$ anche l'[[Immagine di funzione|immagine]] tenderà a $f(\bar{x})$ ([[Limite formulato per successione|limite formulato per successione]]).
$$f: A \to \mathbb{R}, \ \ \bar{x} \in A \cap \mathcal{D}(A)$$
$$f \text{ continua in } \bar{x} \implies \forall x_{n} \in A: x_{n} \to \bar{x} \implies f(x_{n}) \stackrel{n \to +\infty}{\longrightarrow} f(\bar{x})$$

### Dimostrazione
Assumendo che $f(a) < 0$ e $f(b) > 0$, vogliamo costruire due successioni $a_{n}$  e $b_{n}$ tali che:
- $a_{1} = a$
- $b_{1} = b$
- $a_{n} \nearrow$ ([[Successione monotona#Successione crescente|crescente]])
- $b_{n} \searrow$ ([[Successione monotona#Successione decrescente|decrescente]])
- $f(a_{n}) < 0$ e $f(b_{n}) > 0 \ \ \forall n$

Utilizzando un [[Algoritmo di bisezione|algoritmo di bisezione]], decidiamo quindi di prendere il punto in mezzo tra i due estremi dell'intervallo
$$\frac{a_{1} + b_{1}}{2}$$

Possono succedere 3 cose:
- $f\left(\frac{a_{1} + b_{1}}{2}\right) = 0$ --> l'algoritmo è finito
- $f\left(\frac{a_{1} + b_{1}}{2}\right) > 0$ --> allora avremo che
	- $a_{2} = a_{1}$
	- $b_{2} = \frac{a_{1} + b_{1}}{2}$
- $f\left(\frac{a_{1} + b_{1}}{2}\right) < 0$ --> allora avremo che
	- $a_{2} = \frac{a_{1} + b_{1}}{2}$
	- $b_{2} = b_{1}$

Se cadiamo negli ultimi due casi _ripetiamo il procedimento restringendo l'intervallo a uno dei due sottointervalli_ (destro o sinistro), così da costruire effettivamente le due successioni in modo che rispettino tutte le loro proprietà.

Reiterando l'algoritmo si saranno costruite le due successioni con le seguenti proprietà:
- $a_{n} \nearrow$
- $b_{n} \searrow$
- $a_{n} \leq b_{n}$
- $f(a_{n}) < 0$ e $f(b_{n}) > 0 \ \ \forall n$
- $b_{n} - a_{n} = \frac{b-a}{2^{n-1}}$

Costruite quindi $a_{n}$ e $b_{n}$, vogliamo dimostrare due cose:
- che i _limiti di $a_{n}$ e $b_{n}$ sono uguali e convergenti a $c$_
- che $f(c) = 0$

#### $\lim_{n \to +\infty} a_{n} = \lim_{n \to +\infty} b_{n} = c$
Unendo le proprietà sopra riportate, sappiamo che
$$a_{n} \subseteq [a, b]$$
e perciò che $a_{n}$ è [[Successione numerica#Tipologie|limitata]]. Dal [[Dimostrazione successioni monotone hanno limite#Corollario|corollario delle successioni monotone]], essendo $a_{n} \nearrow$ e _sup. limitata_, allora **converge a $\alpha$**.

Lo stesso vale per $b_{n}$, che in quanto _inf. limitata_ e $\searrow$ **converge a $\beta$**.

Se ora prendiamo il limite per $n \to +\infty$ di $b_{n} - a_{n}$ otteniamo che
$$\lim_{n \to +\infty} b_{n} - a_{n} = \beta - \alpha$$

Dalla definizione derivata dalle proprietà delle due successioni abbiamo che
$$b_{n} - a_{n} = \frac{b-a}{2^{n-1}}$$

Per cui
$$\beta - \alpha = \lim_{n \to +\infty} \frac{b-a}{2^{n-1}} = 0$$

Abbiamo dimostrato che $\beta = \alpha$ e che quindi **i limiti di $a_{n}$ e $b_{n}$ sono uguali**. Chiamiamo $c$ questo limite.

#### $f(c) = 0$
Dal [[Teorema degli zeri#2|lemma 2]] abbiamo che
$$a_{n} \to c \implies \lim_{n \to +\infty} f(a_{n}) = f(c)$$

per cui dal [[Teorema degli zeri#1|lemma 1]] abbiamo che
$$a_{n} < 0 \ \ \forall n \implies f(c) \leq 0$$

Ripetiamo il ragionamento tenendo in considerazione $b_{n}$.

Dal [[Teorema degli zeri#2|lemma 2]] abbiamo che
$$b_{n} \to c \implies \lim_{n \to +\infty} f(b_{n}) = f(c)$$

per cui dal [[Teorema degli zeri#1|lemma 1]] abbiamo che
$$b_{n} > 0 \ \ \forall n \implies f(c) \geq 0$$

Quindi abbiamo:
- $f(c) \leq 0$
- $f(c) \geq 0$

che può essere soddisfatto solo se $f(c) = 0$.
**Cvd**.

## Osservazioni
Questo tipo di dimostrazione è **costruttiva**, perché non si limita a dimostrare l'esistenza di $c \in ]a, b[ : f(c) = 0$, ma fornisce anche un procedimento da cui dedurre un algoritmo per approssimare le radici di $f$.

## Conseguenze
Per il teorema degli zeri si prova per esempio come **tutti i polinomi di grado dispari si annullino per forza**. Sappiamo che sono [[Funzioni continue#Funzioni|funzioni continuie]] e [[Funzione suriettiva|suriettive]], e perciò in tutto il loro dominio dovranno per forza annullarsi in almeno un punto.

> Ogni polinomio di grado dispari ha almeno una radice.

La stessa osservazione ovviamente _non vale per i polinomi di grado pari_ (non tutti hanno soluzione).

## Referenze
- [info](https://www.youmath.it/lezioni/analisi-matematica/limiti-continuita-e-asintoti/723-teorema-degli-zeri.html)

[^1]: come il [[Teorema di permanenza del segno|teorema di permanenza del segno]] ma per le successioni