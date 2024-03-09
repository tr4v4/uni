---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 15-10-2023 14:17:39
links:
  - "[[Lecture 13102023133536]]"
---
# Limite finito al finito di funzione
---
## Introduzione
> Si dice che
> $$\lim_{x \to x_{0}} f(x) = l$$
> se
> $$\forall \epsilon > 0, \exists \delta = \delta(x_{0}, \epsilon) > 0 : \forall x \in D : 0 < |x - x_{0}| < \delta \implies |f(x) - l| < \epsilon$$
> ovvero, **per ogni $\epsilon$ esiste una soglia $\delta$ tale per cui per ogni $x$ appartenente al dominio in un intervallo tra $x_{0}-\delta$ e $x_{0}+\delta$  il valore di $x$ produce un $f(x)$ tra $l-\epsilon$ e $l+\epsilon$**.

In una singola immagine:
![[limite-finito-finito.png]]

Quindi, per ogni $\epsilon$ deve esistere un intervallo di $l$ in cui cade $f(x)$, dove $x$ si trova nell'intervallo di $x_{0}$, [[Punto di accumulazione|punto di accumulazione]] del dominio, definito da $\delta$ (in funzione di $\epsilon$ e $x_{0}$).

<u>Nota bene</u>: il punto $x_{0}$ non è compreso nell'intervallo del dominio (proprio perché punto di accumulazione). Infatti tale punto potrebbe anche non appartenere al dominio stesso...

## Regole
### Polinomio
Si dimostra che se $p(x)$ è un _polinomio di grado $n$_:
$$p(x) = \sum\limits_{j=0}^{n} a_{j}x^{j}$$
allora
$$\lim_{x \to \bar{x}} p(x) = p(\bar{x})$$

### Trigonometriche
$$\lim_{x \to 0} \sin(x) = 0$$
$$\lim_{x \to 0} \cos(x) = 1$$
$$\lim_{x \to 0} \frac{\sin(x)}{x} = 1$$

Tutti dimostrabili con il [[Teorema del confronto|teorema del confronto]]. L'ultimo in particolare, oltre che essere la [[Dimostrazione area del cerchio|prova della formula dell'area del cerchio]], è fondamentale per comprendere come le [[Funzioni trigonometriche|funzioni trigonometriche]] sia dirette sia [[Funzioni trigonometriche inverse|inverse]] sono [[Funzioni continue|continue]] e [[Funzioni derivabili|derivabili]].

## Referenze