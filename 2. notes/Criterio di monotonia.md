---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 04-11-2023 11:51:27
links:
  - "[[Lecture 03112023134932]]"
---
# Criterio di monotonia
---
## Definizione
> Fissata una [[Funzione matematica|funzione]] $f : [a, b] \to \mathbb{R}$ [[Funzioni derivabili|derivabile]], si ha che
> $$f'(x) \geq 0 \ \ \forall x \in  ]a, b[ \iff f \text{ crescente su } ]a, b[$$
> $$f'(x) \leq 0 \ \ \forall x \in  ]a, b[ \iff f \text{ decrescente su } ]a, b[$$
> $$f'(x) > 0 \ \ \forall x \in  ]a, b[ \implies f \text{ strettamente crescente su } ]a, b[$$
> $$f'(x) < 0 \ \ \forall x \in  ]a, b[ \implies f \text{ strettamente decrescente su } ]a, b[$$

Questo criterio **associa il ruolo della [[Derivata|derivata]] prima di una funzione con la sua [[Funzioni monotone|monotonia]]**.

<u>Nota bene</u>: per la monotonia stretta il _coimplica ($\iff$) non vale più_. Infatti una funzione può essere strettamente crescente/decrescente e far annullare la derivata prima in un [[Punto interno|punto interno]] al dominio (es. $x^{3}$ o $-x^{3}$)[^1]. Per distinguere, infatti, le funzioni crescenti da quelle strettamente crescenti (o viceversa per le decrescenti) si utilizza il [[Teorema di monotonia stretta|teorema di monotonia stretta]].

## Dimostrazione
Per dimostrare il criterio di monotonia (solo il primo) ci avvaliamo del [[Teorema di Lagrange|teorema di Lagrange]].

### $\implies$
Iniziamo con l'[[Implicazione|implicazione]] a destra, per cui presa come ipotesi $f'(x) \geq 0$ dobbiamo dimostrare $f$ _crescente_.

Fissiamo allora due punti $x_{1}, x_{2} \in ]a, b[$ tali che $x_{1} < x_{2}$, vogliamo allora dimostrare che $f(x_{1}) \leq f(x_{2})$. Sapendo che $f$ è derivabile possiamo applicare Lagrange e dimostrare che
$$\frac{f(x_{2}) - f(x_{1})}{x_{2} - x_{1}} = f'(c)$$
il quale, per ipotesi, è maggiore/uguale a 0. Abbiamo quindi
$$\frac{f(x_{2}) - f(x_{1})}{x_{2} - x_{1}} \geq 0$$ e sappiamo che il denominatore è per forza maggiore di 0. Non rimane che
$$f(x_{2}) - f(x_{1}) \geq 0$$ovvero
$$f(x_{2}) \geq f(x_{1})$$

**Cvd**.

### $\Longleftarrow$
Ora, per dimostrare $f'(x) \geq 0$ avendo a disposizione $f$ _crescente_, fissiamo un punto $x_{0}$ tale che $x > x_{0} \implies f(x) \geq f(x_{0})$.
Abbiamo che $\forall x \in ]a, b[ : x > x_{0}$, per cui
$$\frac{f(x) - f(x_{0})}{x - x_{0}} \geq 0$$

Ora, essendo $f$ derivabile in $x_{0}$ (perché $x_{0} \in ]a, b[$), possiamo fare il **rapporto incrementale** per ottenere $f'(x_{0})$:
$$f'(x_{0}) = \lim_{x \to x_{0}^{+}} \frac{f(x) - f(x_{0})}{x - x_{0}}$$
Sapendo da prima che $\frac{f(x) - f(x_{0})}{x - x_{0}} \geq 0$, per il [[Teorema di permanenza del segno|teorema di permanenza del segno]] possiamo concludere che anche $f'(x_{0}) \geq 0$.

**Cvd**.

## Referenze
[^1]: caso già affrontato con il [[Teorema di Fermat|teorema di Fermat]]