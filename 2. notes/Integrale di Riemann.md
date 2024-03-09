---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 26-02-2024 19:36:12
links:
  - "[[Lecture 19022024130000]]"
---
# Integrale di Riemann
---
## Introduzione
Già [[Archimede]] aveva intuito la _costruzione di un'integrale come somma di una serie di rettangoli di un [[Sottografico di funzione|sottografico di funzione]]_, ma [[Riemann]] formalizzò, con gli strumenti matematici dell'epoca, questo concetto.

## Costruzione
Preso un intervallo $[a, b]$ lo scomponiamo in $n \in \mathbb{N}$ sottointervalli uguali:
![[Drawing 2024-02-26 19.39.58.excalidraw|750]]

Assegnamo ad ogni punto un valore:
![[Drawing 2024-02-26 19.44.09.excalidraw|750]]

Sappiamo che ogni segmento è lungo $\frac{b-a}{n}$, per cui avremo:
- $x_{0} = a$
- $x_{1} = a + \frac{b-a}{n}$
- $x_{2} = a + 2\frac{b-a}{n}$
- ...
- $x_{n-1} = a + (n-1) \frac{b-a}{n}$
- $x_{n} = a + n \frac{b-a}{n} = a+b-a = b$ (tutto torna)

Ora ad ogni intervallo fissiamo un punto arbitrario $\xi$ tale che $\xi_{k} \in [x_{k-1}, x_{k}]$:
![[Drawing 2024-02-26 19.50.36.excalidraw|750]]

Immaginiamo allora di costruire questa struttura per ogni $n \in \mathbb{N}$, e definiamo la **somma di Riemann** in questo modo:
> Sia costruita la struttura precedente $\forall n \in \mathbb{N}$ su $f: [a, b] \to \mathbb{R}$, la **somma di Riemann** $n$-esima di $f$ è il numero seguente:
> $$S_{n} = \sum\limits_{k=1}^{n} f(\xi_{k}) \cdot (x_{k} - x_{k-1}) = \sum\limits_{k=1}^{n} f(\xi_{k}) \cdot \frac{b-a}{n}$$
> <u>Nota bene</u>: si definisce un punto arbitrario $\xi_{k}$ per questione di facilità di comprensione, ma si potrebbe scegliere un punto in mezzo, all'inizio o alla fine per ogni intervallo.

![[integrale-riemann.png]]

## Referenze