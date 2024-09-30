---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 13-05-2024 21:09:43
links:
  - "[[Lecture 13052024131457]]"
---
# Integrale multiplo
---
## Introduzione
> Sia $f: A \to \mathbb{R}$, con $A \subseteq \mathbb{R}^{2}$ e [[Insieme semplice|insieme semplice]], una [[Funzione a più variabili|funzione a più variabili]] tale che $f(x, y) \geq 0 \ \ \forall (x, y) \in A$, allora il **volume** del [[Sottografico di funzione|sottografico]] di $f$ definito come $\{(x, y, z) \in \mathbb{R}^{3} | (x, y) \in A, 0 \leq z \leq f(x, y)\}$ ha valore
> $$\int_{A}f(x, y) \ dx\ dy$$
> ossia dell'[[Integrale|integrale]] su tutto l'insieme $A$ di $f(x, y)$.
> In particolare per $\mathbb{R}^{2}$ questo tipo di integrale viene chiamato **integrale doppio**.

<u>Osservazione</u>: con $f(x, y) = 1$ si ha $$\int_{A} 1 \ dx \ dy = \text{area di } A$$, che per analogia è l'integrale $$\int_{a}^{b} 1 \ dx = b - a = \text{lunghezza di } [a, b]$$ per la dimensione $n = 1$.

<u>Nota bene</u>: è _fondamentale come ipotesi che $A$ sia un insieme semplice_. E' infatti possibile applicare la formula di riduzione solo se si è sicuri di trovarsi su un dominio normale (insieme semplice).

## Formula di riduzione
> Sia $f: A \to \mathbb{R}$ continua e $A$ un insieme $y$-semplice, e siano $g_{1}, g_{2} : [a, b] \to \mathbb{R}$ con $g_{1} \leq g_{2}$ su $[a, b]$ continue, allora si ha che
> $$\int_{A}f(x, y) \ dx \ dy = \int_{a}^{b} \left(\int_{g_{1}(x)}^{g_{2}(x)} f(x, y) \ dy\right) \ dx$$
> <u>Nota bene</u>: nel secondo integrale, i limiti $g_{1}(x)$ e $g_{2}(x)$ considerano la $x$ come elemento fissato, per cui dev'essere trattata come costante e si deve integrare solo in $y$ (infatti è in $dy$).

<u>Osservazione</u>: se $g_{1} = g_{2}$ allora $A = \{(x, y) \in \mathbb{R}^{2} | x \in [a, b], y = g_{1}(x) = g_{2}(x)\}$, di conseguenza l'integrale doppio viene calcolato su una superficie piatta, nulla: $$\int_{A} f(x, y) \ dx \ dy = \int_{a}^{b} \left(\int_{g_{1}(x)}^{g_{1}(x)} f(x, y) \ dy\right) \ dx = \int_{a}^{b} 0 \ dx = 0$$

### Esempio
Si consideri come insieme $y$-semplice $A$ quello composto dal triangolo di vertici $(0, 0), (1, 0), (1, 1)$, e come funzione $f: A \to \mathbb{R}$ definita come $f(x, y) = xy$. Vogliamo calcolare il volume di $f$ in $A$, ossia
$$\int_{A}xy \ dx \ dy$$

Disegnando i 3 triangoli possiamo facilmente identificare due funzioni $g_{1}, g_{2}$ tali che $g_{1} \leq g_{2}$ su tutto $[0, 1]$ e continue:
![[Drawing 2024-05-13 21.42.27.excalidraw|750]]

Definiamo infatti:
- $g_{1}(x) = 0 \ \ \forall x \in [0, 1] = [a, b]$
- $g_{2}(x) = x$

Allora usiamo la formula di riduzione:
$$\int_{A}xy \ dx \ dy = \int_{0}^{1} \left(\int_{0}^{x} xy \ dy\right) \ dx = \int_{0}^{1} \left[x \frac{y^{2}}{2}\right]_{0}^{x} \ dx = \int_{0}^{1} \left[x \frac{x^{2}}{2} - x \frac{0}{2}\right] \ dx = \int_{0}^{1} \left[\frac{x^{3}}{2}\right] \ dx = \left[\frac{x^{4}}{8}\right]_{0}^{1} = \frac{1}{8}$$

## Referenze