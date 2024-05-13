---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 26-04-2024 16:58:20
links:
  - "[[Lecture 08042024130916]]"
  - "[[Lecture 24042024142113]]"
---
# Teorema del gradiente
---
## Introduzione
> Sia $f: \mathbb{R}^{2} \to \mathbb{R}$ [[Funzione differenziabile|differenziabile]] in $(\bar{x}, \bar{y})$, allora si ha che $\forall v = (v_{1}, v_{2}) \neq (0, 0)$ t.c. $||v|| = 1$ (di [[Norma euclidea|norma]] unitaria) vale
> $$\frac{\partial_{f}}{\partial_{v}}(\bar{x}, \bar{y}) = \nabla f(\bar{x}, \bar{y}) \cdot (v_{1}, v_{2}) = \partial_{x}f(\bar{x}, \bar{y})v_{1} + \partial_{y}f(\bar{x}, \bar{y})v_{2}$$
> ovvero _è possibile calcolare la [[Derivata direzionale|derivata direzionale]] di una funzione rispetto a un [[Vettore|vettore]] [[Normalizzazione|normalizzato]] $v$ non nullo facendo il [[Prodotto scalare|prodotto scalare]] tra il [[Gradiente|gradiente]] della funzione con il vettore stesso_.

Questo ci è utilissimo dal momento che _altrimenti, per calcolare le derivate direzionali, dovremmo svolgere un [[Limite|limite]]_ (rapporto incrementale)!

### In $\mathbb{R}^{n}$
Chiaramente la formula vale anche in $\mathbb{R}^{n}$, e si definisce nel seguente elegante modo:
> Sia $f: \mathbb{R}^{n} \to \mathbb{R}$, $\bar{x} \in \mathbb{R}^{n}$, $v \in \mathbb{R}^{n}$ t.c. $||v|| = 1$, allora se $f$ è differenziabile in $\bar{x}$ vale
> $$\partial_{v}f(\bar{x}) = \nabla f(\bar{x}) \cdot v = \sum\limits_{k = 1}^{n} \partial_{x}f(\bar{x})v_{k}$$

## Dimostrazione
Dimostriamo la formula per $\mathbb{R}^{n}$.

Sapendo che $f$ è differenziabile in $\bar{x}$ allora sappiamo che $\exists \partial_{k}f(\bar{x}) \ \forall k \in \{1, \cdots, n\}$, e che vale $f(\bar{x} + h) = f(\bar{x}) + \nabla f(\bar{x}) \cdot h + o(||h||)$ per $h \to 0$. Devo dimostrare
$$\partial_{v}f(\bar{x}) = \nabla f(\bar{x}) \cdot v$$

Uso la definizione di derivata direzionale, per cui
$$\partial_{v}f(\bar{x}) = \lim_{t \to 0} \frac{f(\bar{x} + tv) - f(\bar{x})}{t}$$

Considero $h = tv$ perché $h \to 0 \land tv \to 0$ in quanto $||v|| = 1$, per cui
$$\partial_{v}f(\bar{x}) = \lim_{t \to 0} \frac{f(\bar{x}) + \nabla f(\bar{x}) \cdot tv + o(||tv||) - f(\bar{x})}{t} = \nabla f(\bar{x}) \cdot v + \lim_{t \to 0} \frac{o(|t| \cdot ||v||)}{t} = \nabla f(\bar{x}) \cdot v$$

**Qed**.

## Referenze