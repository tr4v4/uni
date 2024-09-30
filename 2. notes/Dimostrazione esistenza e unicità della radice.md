---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 01-10-2023 15:12:53
links:
  - "[[Lecture 29092023135952]]"
  - "[[Lecture 02102023093041]]"
---
# Dimostrazione esistenza e unicità della radice
---
## Introduzione
La [[Proprietà di completezza di R|proprietà di completezza]] di $\mathbb{R}$ ci garantisce che ogni [[Numeri reali|numero reale]] è uguale a un altro numero elevato al quadrato. Vale a dire che **ogni numero reale ammette una sola sua radice**.
Per cui
$$\forall a \in \mathbb{R}_{+} \ \exists! b \in \mathbb{R}_{+}: b^{2} = a$$
codificato quindi in
$$\sqrt{a} = b$$

<u>Attenzione</u>: $\sqrt{a} \neq -b$ perché trattiamo solo di **radici aritmetiche**, ovvero che accettano solo radici positive.

## Dimostrazione
### Lemmi
Per poter dimostrare questo teorema c'è prima bisogno di dichiarare alcuni [[Lemma|lemmi]].
Per cui da $\forall x, y \in \mathbb{R}: x, y \geq 0$ si ha
$$x^{2} \leq y^{2} \iff x \leq y$$
$$x^{2} \geq y^{2} \iff x \geq y$$
$$x^{2} = y^{2} \iff x = y$$
$$x^{2} < y \implies \exists \epsilon > 0: (x+\epsilon)^{2} < y$$
$$x^{2} > y \implies \exists \epsilon > 0: (x-\epsilon)^{2} > y$$

### Dimostrazione
Consideriamo l'insieme
$$A = \{c \in \mathbb{R} | c \geq 0, \ c^{2} \leq a\}$$
Possiamo dedurre che
- $0 \in A \implies A \neq \varnothing$
- $A$ è _superiormente limitato_ (ammette [[Maggiorante|maggioranti]])

Come facciamo a essere certi di quest'ultimo punto? Con questa successione:
$$c^{2} \leq a \leq (a+1) \leq (a+1)^{2} \ \ \ \implies \ \ \ c^{2} \leq (a+1)^{2} $$

Dal _lemma A_
$$c^{2} \leq (a+1)^{2} \iff c \leq a+1$$
Per cui abbiamo trovato che $a + 1$ è un maggiorante di $A$, il che prova che $A$ **è superiormente limitato**.

Per la **proprietà di completezza** allora
$$\exists \sup \ A := b \in \mathbb{R}_{+}$$
Se noi dimostriamo che $b^{2} = a$ allora abbiamo per forza che $b = \sqrt{a}$. Noi sappiamo per forza, infatti, che per la definizione stessa di $A$ è ovvio che il suo $\sup$ sia $\sqrt{a}$, ma per dimostrarlo correttamente dobbiamo essere certi del fatto che $b^{2} = a$.

Procediamo allora [[Dimostrazione per assurdo|per assurdo]], mostrando che non può essere $b^{2} < a$ né $b^{2} > a$.

#### $b^{2} < a$
Se supponiamo come vero $b^{2} < a$, allora dal _lemma D_ otteniamo che
$$\exists \epsilon > 0: (b+\epsilon)^{2} < a$$

Dalla definizione stessa di $A$ allora
$$(b + \epsilon) \in A$$
(perché $c^{2} \leq a$), il che vorrebbe dire però che è più piccolo di $\sup \ A = b$. Per cui
$$(b + \epsilon) \leq sup \ A = b$$
da cui
$$b + \epsilon \leq b$$
che produce $\epsilon \leq 0$, ovvero un _assurdo_.

#### $b^{2} > a$
Se supponiamo come vero invece $b^{2} > a$, allora dal _lemma E_ otteniamo che
$$\exists \epsilon > 0 : (b - \epsilon)^{2} > a$$
Dalla definizione stessa di $A$, essendo $(b - \epsilon)^{2} > a$, otteniamo di conseguenza
$$c^{2} \leq (b - \epsilon)^{2}$$
da cui con il _lemma A_ diventa
$$c \leq (b - \epsilon)$$
Se vale questa espressione, allora $(b- \epsilon)$ è un maggiorante di $A$, ma se $b = sup \ A$ è il più piccolo dei maggioranti allora incombiamo in un _assurdo_.

#### $b^{2} = a$
Non ci resta ora da dimostrare che l'**unicità della radice**. Prendiamo quindi
$${b_{1}}^{2} = a = {b_{2}}^{2}$$
e quindi
$${b_{1}}^{2} = {b_{2}}^{2}$$
Dal _lemma C_ otteniamo
$$b_{1} = b_{2}$$

## Conseguenze
La regola **non vale solo per le radici quadrate**: in generale diremmo quindi che
$$\forall a \in {\mathbb{R}}_{+}: \exists \sqrt[n]{a} \in \mathbb{R}_{+}$$

## Referenze
- [[Radice]]