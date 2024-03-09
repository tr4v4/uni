---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 02-11-2023 22:32:51
links:
  - "[[Lecture 30102023093826]]"
---
# Teorema di Fermat
---
## Introduzione
> Fissata una [[Funzione matematica|funzione]] $f : [a, b] \to \mathbb{R}$, se
> 1. $x_{0} \in ]a, b[$ ([[Punto interno|punto interno]]) è [[Massimo e minimo relativo|punto di massimo o minimo relativo]]
> 2. $f$ è [[Funzioni derivabili|derivabile]] in $x_{0}$
> 
> allora
> $$f'(x_{0}) = 0$$

Questo teorema **lega fondamentalmente la [[Derivata|derivata]] di una funzione ai suoi punti di massimo e minimi relativi**.

<u>Attenzione</u>: non vale il contrario! E' infatti una _condizione necessaria ma non sufficiente_, e quindi se la derivata si annulla in $x_{0}$ non è detto che $x_{0}$ sia un punto di massimo o di minimo relativo.

Si pensi per esempio a $x^3$:
```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-10,10,-10,10]
disableZoom: false
grid: true
---
y=x^3
```
dove in $x=0$ la derivata di annulla ma non è un punto di massimo né di minimo relativo.

## Dimostrazione
Per dimostrare il teorema supponiamo di essere solo nel caso in cui $x_{0}$ è un punto di massimo relativo.

Dalla prima ipotesi, quindi, sappiamo che
$$\forall r > 0: f(x) \leq f(x_{0}), \ \ x \in [a, b] \cap I_{r}(x_{0})$$

Dalla seconda ipotesi invece ricaviamo che
$$\exists \lim_{x \to x_{0}} \frac{f(x) - f(x_{0})}{x - x_{0}}$$

Se esiste la derivata di $f$ per $x_{0}$ allora esiste la sua _derivata destra e sinistra_. Partendo dalla destra si ha
$$\lim_{x \to x_{0}^{+}} \frac{f(x) - f(x_{0})}{x - x_{0}}$$

da cui dalla prima ipotesi sappiamo che il numeratore $f(x) - f(x_{0}) \leq 0$, e tendendo $x \to x_{0}^{+}$ abbiamo che il denominatore $x - x_{0} > 0$. Per il [[Teorema di permanenza del segno|teorema di permanenza del segno]], se per ogni $x$ del [[Derivata#Definizione|rapporto incrementale]] abbiamo un valore $\leq 0$ (da $\frac{\leq 0}{> 0}$), allora anche $f'_{+}(x_{0}) \leq 0$.

Andando ora con la sinistra abbiamo
$$\lim_{x \to x_{0}^{-}} \frac{f(x) - f(x_{0})}{x - x_{0}}$$

da cui otteniamo, unendo la prima ipotesi con il teorema di permanenza del segno, che $f'_{-}(x_{0}) \geq 0$.

In conclusione abbiamo
$$f'(x_{0}) = \begin{cases} f'_{+}(x_{0}) \leq 0 \\ f'_{-}(x_{0}) \geq 0 \end{cases}$$

da cui concludiamo che l'unica soluzione possibile può essere $f'(x_{0}) = 0$.

**Cvd**.

### Ipotesi
E' importante riconoscere il motivo per cui $x_{0}$ dev'essere necessariamente un punto interno al dominio di $f$.
Presa per esempio la funzione
![[ipotesi-fermat.png]]

ci si rende facilmente conto come _pur essendo gli estremi dei massimi e dei minimi relativi, la loro derivata prima non si annulli_. I punti presi in considerazione, per questo, devono necessariamente essere interni.

## Referenze