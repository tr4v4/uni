---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 26-10-2023 21:22:11
links:
  - "[[Lecture 23102023094009]]"
---
# Teorema di Weierstrass
---
## Introduzione
Per introdurre il _teorema di Weierstrass_ è necessario essere a conoscenza dei [[Massimo e minimo assoluto|massimi e minimi assoluti]] di una [[Funzione matematica|funzione]].

## Teorema
> Fissata una funzione $f: [a, b] \to \mathbb{R}$ [[Funzioni continue|continua]], **esiste sempre un punto di massimo e un punto di minimo assoluto**[^1]. Ovvero
> $$\exists M \in [a, b] : f(x) \leq f(M) \ \ \forall x \in [a, b]$$
> $$\exists m \in [a, b] : f(x) \geq f(m) \ \ \forall x \in [a, b]$$

Come conseguenza fondamentale di questo teorema abbiamo che
$$f([a, b]) \subseteq [m, M]$$

### Ipotesi
Le ipotesi che consentono al teorema di Weierstrass di applicarsi sono:
- l'intervallo del dominio dev'essere _chiuso_ e _limitato_ ($[a, b]$)
	- se fosse aperto --> potrebbero capitare funzioni in cui il punto di massimo o di minimo coincidono con l'estremo non incluso
	- se fosse illimitato --> potrebbero capitare funzioni in cui il punto di massimo o di minimo è indefinibile perché la funzione tende a $\pm \infty$
- la funzione dev'essere _continua_
	- se non fosse continua --> potrebbero capitare funzioni in cui il punto di massimo o di minimo coincide con la congiunzione di due rami non continui

## Referenze
[^1]: ci riferiamo al concetto di [[Massimo|massimo]] e [[Minimo|minimo]] di un insieme, che in questo caso è il codominio!