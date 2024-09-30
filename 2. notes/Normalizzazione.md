---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 18-03-2024 20:30:12
links:
  - "[[Lecture 11032024131300]]"
---
# Normalizzazione
---
## Introduzione
> L'operazione di **normalizzazione** applicata a un [[Vettore|vettore]] $v$ consiste nel _portarlo nel range $[0, 1]$_. In particolare cerco un $r > 0$ t.c. $||rx|| = 1$, ovvero, per le [[Norma euclidea#Proprietà|proprietà della norma]], $r||x|| = 1$, quindi
> $$r = \frac{1}{||x||}$$
> Il vettore $$\frac{x}{||x||} \in \mathbb{R}^{n}$$
_ha norma 1_ e si dice, appunto, _normalizzato_ di $x \in \mathbb{R}^{n} \setminus \{\underline{0}\}$.

Preso per esempio un vettore in $\mathbb{R}^{2}$, **normalizzarlo vorrebbe dire mantenere la direzione ma diminuire la sua intensità, confinandolo nella circonferenza unitaria**.
![[Drawing 2024-03-18 20.35.32.excalidraw|750]]

## Proprietà
Posso scrivere, per un vettore $x \in \mathbb{R}^{n}$ e $x \neq \underline{0}$, che
$$x = ||x|| \cdot \frac{x}{||x||}$$

In particolare in $\mathbb{R}^{2}$ vale che
$$(x, y) = ||(x, y)|| \cdot \left(\frac{x}{||(x, y)||}, \frac{x}{||(x, y)||}\right)$$
e allora possiamo scrivere quel punto $(x, y)$ come
$$(\cos{\theta}, \sin{\theta}) = \left(\frac{x}{||\left(x, y\right)||}, \frac{x}{||(x, y)||}\right)$$
perché sappiamo che il vettore $(x, y)$ normalizzato è nella circonferenza unitaria. Da questo ricaviamo che
$$(x, y) = r \cdot (\cos{\theta}, \sin{\theta})$$
dove:
- $r = ||(x, y)|| > 0$ è detto _modulo_;
- $\theta \in [0, 2 \pi[$ è detto _argomento_;

Abbiamo così ottenuto le [[Coordinate polari|coordinate polari]], un modo diverso di rappresentare dei vettori.

## Referenze