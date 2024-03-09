---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 26-10-2023 21:52:00
links:
  - "[[Lecture 23102023094009]]"
---
# Teorema di Weierstrass esteso
---
## Introduzione
Unendo il [[Teorema di Weierstrass]] al [[Teorema degli zeri]] otteniamo il **teorema di Weierstrass esteso**.

## Teorema
> Fissata una funzione $f: [a, b] \to \mathbb{R}$ continua, esiste sempre un [[Massimo e minimo assoluto|punto di massimo e di minimo assoluto]] e
> $$f([a, b]) = [m, M]$$

Mentre con solo il teorema di Weierstrass potevamo dire $f([a, b]) \subseteq [m, M]$, sfruttando il teorema degli zeri garantiamo che in realtà _l'[[Immagine di funzione|immagine]] dell'intervallo del dominio è proprio uguale all'intervallo definito da massimo e minimo assoluto_.

### Dimostrazione
Per dimostrarlo ci basta prendere una funzione definita in un intervallo chiuso e limitato $[a, b]$ e continua in $\mathbb{R}$ per il quale non vale $f(a) \cdot f(b) < 0$. Procediamo allora considerando un valore $y \in [m, M]$. Se trasliamo la funzione di questo $y$ otteniamo una nuova funzione che per forza avrà $f(m) < 0$ e $f(M) > 0$, e per il quale quindi si potrà applicare il teorema degli zeri! Infatti esisterà un $c$ che annullerà la funzione: $f(c) = 0 = y$.

Questo ragionamento è valido _per ogni_ $y \in [m, M]$, per cui si ha $f([a, b]) = [m, M]$.

## Conseguenze
Questo teorema spiega il motivo per cui l'immagine della funzione _seno_ in $[-\frac{\pi}{2}, \frac{\pi}{2}]$ è uguale all'intervallo tra il punto minimo e massimo assoluto della funzione, quindi $[-1, 1]$.

Lo stesso vale per il _coseno_, per cui $\cos([0, \pi]) = [-1, 1]$, per la tangente e l'[[Funzione esponenziale|esponenziale]].

## Referenze