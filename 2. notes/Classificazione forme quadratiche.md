---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 11-05-2024 16:24:37
links:
  - "[[Lecture 06052024131425]]"
---
# Classificazione forme quadratiche
---
## Introduzione
Sappiamo che delle [[Forma quadratica|forme quadratiche]] si studia il loro _segno_, e sulla base di questo si possono ottenere informazioni utili a seconda del campo di studio.
Si vuole ottenere un criterio più semplice per classificare le forme quadratiche a partire da uno studio della [[Matrice|matrice]] associata $A$.

## Classificazione
### $n = 2$
> Sia $A = \begin{pmatrix}a & b \\ b & c\end{pmatrix}$ una matrice [[Matrice simmetrica|simmetrica]], allora si ha che:
> 1. $A > 0$ (_definita positiva_) $\iff a > 0 \ \land \ \det(A) > 0$;
> 2. $A < 0$ (_definita negativa_) $\iff a < 0 \ \land \ \det(A) > 0$;
> 3. $A$ _indefinita_ $\iff \det(A) < 0$.

#### Dimostrazione
##### 1.
$\impliedby$: supponiamo $a > 0$ e $\det(A) > 0$, ossia $ac - b^{2} > 0$. Dobbiamo dimostrare $A > 0$, vale a dire
$$<Ah, h> > 0 \ \ \forall h \neq 0$$
ossia, fissato $h = (h_{1}, h_{2}) \neq (0, 0)$, che
$$ah_{1}^{2} + ch_{2}^{2} + 2bh_{1}h_{2} > 0$$

Dalle ipotesi ho, avendo $a > 0$ e $ac-b^{2} > 0$
$$ac - b^{2} > 0 \iff \frac{c}{a} > \frac{b^{2}}{a^{2}}$$
per cui, dividendo la tesi per $a$, ottengo
$$h_{1}^{2} + \frac{c}{a}h_{2}^{2} + 2\frac{b}{a}h_{1}h_{2} > 0$$
da cui
$$h_{1}^{2} + \frac{c}{a}h_{2}^{2} + 2\frac{b}{a}h_{1}h_{2} > h_{1}^{2} + \frac{b^{2}}{a^{2}}h_{2}^{2} + 2\frac{b}{a}h_{1}h_{2} > 0$$
raccogliendo a fattor comune $a^{2}$ si ha
$$a^{2}h_{1}^{2} + b^{2}h_{2}^{2} + 2abh_{1}h_{2} = (ah_{1} + bh_{2})^{2} > 0$$

**Qed**.

## Referenze