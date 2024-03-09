---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 25-02-2024 21:57:06
links:
  - "[[Lecture 19022024130000]]"
  - "[[Lecture 26022024130925]]"
---
# Integrale
---
## Introduzione
Il motivo per cui si introduce il concetto di **integrale** in [[Analisi I|analisi]] è per la necessità di _calcolare le aree di figure curvilinee_[^1]. Le aree che andremo a calcolare sono [[Sottografico di funzione|sottografici di funzioni]].

## Definizione
> Sia $f: [a, b] \to \mathbb{R}$ [[Funzioni continue|continua]], e $(S_{n})_{n \in \mathbb{N}}$ [[Successione numerica|successione]] delle [[Integrale di Riemann|somme di Riemann]], si ha che
> $$\exists \lim_{n \to +\infty} S_{n} \in \mathbb{R}$$
> ed esso non dipende dalla scelta dei punti $\xi_{k}$ fatta ad ogni passo di $S_{n}$. Si pone
> $$\lim_{n \to +\infty} = \int_{a}^{b} f(x) \ dx$$
> ed è chiamato **integrale** _definito_.
> <u>Nota bene</u>: il simbolo stesso $\int$ suggerisce che stiamo facendo il limite di una somma infinita tra $f(x)$, di fatto l'_altezza_, e $dx$, la _base_.

Quello che facciamo, con il limite per $n \to +\infty$, è _rendere sempre più alto il numero di rettangoli del sottografico, al fine di rendere più precisa la somma delle loro aree_: all'infinito _la somma darà come risultato proprio l'area del sottografico_.

![[riemann-integral.gif]]

### Osservazioni
Dalla definizione si ha che:
1. $f(x) \geq 0 \ \ \forall x \in [a, b] \implies \int_{a}^{b} f(x) \ dx = \text{area del suo sottografo}$
2. $\int_{a}^{a} f(x) \ dx = 0$, di fatto $S_{n} = 0 \ \ \forall n \in \mathbb{N}$
3. $f(x) = k \implies \int_{a}^{b} f(x) \ dx = \int_{a}^{b} k \cdot dx = (b - a) \cdot k$, di fatto $S_{n} = \sum\limits_{k=1}^{n} k \cdot \frac{b-a}{n} = n \cdot k \cdot \frac{b-a}{n} = k \cdot (b-a)$

## Proprietà
### Linearità[^2]
Si ha che se $f, g$ sono funzioni continue su $[a, b]$, e $\lambda, \mu \in \mathbb{R}$, allora
$$\int_{a}^{b} (\lambda f(x) + \mu g(x)) \ dx = \int_{a}^{b} \lambda f(x) \ dx + \int_{a}^{b} \mu g(x) \ dx = \lambda \int_{a}^{b} f(x) \ dx + \mu \int_{a}^{b} g(x) \ dx$$

### Additività
Sia $f: [a, b] \to \mathbb{R}$ continua e $c \in [a, b]$, allora
$$\int_{a}^{b} f(x) \ dx = \int_{a}^{c} f(x) \ dx + \int_{c}^{b} f(x) \ dx$$

### Monotonia
Sia $f: [a, b] \to \mathbb{R}$ e $f(x) \geq 0 \ \ \forall x \in [a, b]$, allora
$$\int_{a}^{b} f(x) \ dx \geq 0$$
(perché $S_{n} \geq 0 \ \ \forall n \in \mathbb{N}$).

#### Monotonia bis
Siano $f, g: [a, b] \to \mathbb{R}$ e $f(x) \leq g(x) \ \ \forall x \in [a, b]$, allora
$$\int_{a}^{b} f(x) \ dx \leq \int_{a}^{b} g(x) \ dx$$

### Inverso
Vale che
$$\int_{a}^{b} f(x) \ dx = - \int_{b}^{a} f(x) \ dx$$

e perciò l'_additività si può generalizzare_, ovvero vale a prescindere dalle collocazioni di $a, b, c$.

## Utilizzi
### Aree con segno
L'utilizzo più conosciuto degli integrali sta nel calcolo delle aree di sottografici di funzioni. Ci sono casi particolari in cui nell'intervallo $[a, b]$ scelto su cui calcolare l'area la funzione $f: [a, b] \to \mathbb{R}$ assume valori sia positivi che negativi, come nel seguente caso:
![[Drawing 2024-02-26 20.08.46.excalidraw|750]]

In questo caso, per poter calcolare l'area complessiva, bisogna dividere l'integrale in 3 sottointegrali, ed è necessario tenere a mente che _$A2$ avrà un valore negativo_, per cui la sua area dovrà essere sottratta nella somma complessiva dei 3 risultati:
$$\int_{a}^{b} f(x) \ dx = \int_{a}^{c} f(x) \ dx - \int_{c}^{d} f(x) \ dx + \int_{d}^{b} f(x) \ dx = A1 - A2 + A3$$

## Tipologie
Gli integrali possono essere:
- [[Integrale definito|definiti]]
- [[Integrale indefinito|indefiniti]]
- [[Integrale improprio|impropri]]

## Teoremi
- [[Teorema della media integrale]]
- [[Teorema fondamentale del calcolo integrale]]
- [[Teorema di Torricelli-Barrow]]

## Referenze
[^1]: anche lunghezze di [[Curva|curve]]...
[^2]: dall'[[Algebra lineare|algebra lineare]]!