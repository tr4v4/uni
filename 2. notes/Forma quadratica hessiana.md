---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 11-05-2024 17:39:23
links:
  - "[[Lecture 06052024131425]]"
---
# Forma quadratica hessiana
---
## Introduzione
> Sia $f: \mathbb{R}^{n} \to \mathbb{R}$ una [[Funzione a più variabili|funzione a più variabili]] con [[Derivata|derivate]] [[Funzioni continue|continue]] fino all'ordine 2 ($C^{2}$[^1]). Fissata la [[Matrice hessiana|matrice hessiana]] $Hf(\bar{x})$ per un punto $\bar{x} \in \mathbb{R}^{n}$ tale che $Hf(\bar{x})_{jk} = \partial^{2}_{jk}f(\bar{x})$, allora vale che
> $$q_{Hf(\bar{x})}(h) = <Hf(\bar{x})h, h> = \sum\limits_{j,k=1}^{n} \partial_{jk}f(\bar{x})h_{j}h_{k}$$
> ossia, in poche parole, la matrice hessiana in quanto [[Matrice simmetrica|simmetrica]] per il [[Teorema di Schwarz|teorema di Schwarz]], è una [[Forma quadratica|forma quadratica]].

### Esempio
Nel caso $n = 2$, presa una qualunque funzione $f(x, y)$, e definita la matrice hessiana per un punto $(\bar{x}, \bar{y})$ come
$$Hf(\bar{x}, \bar{y}) = \begin{bmatrix}\partial_{xx}f(\bar{x}, \bar{y}) & \partial_{xy}f(\bar{x}, \bar{y}) \\ \partial_{yx}f(\bar{x}, \bar{y}) & \partial_{yy}f(\bar{x}, \bar{y})\end{bmatrix}$$
allora si ha
$$q_{Hf(\bar{x}, \bar{y})}(h) = \partial_{xx}f(\bar{x}, \bar{y})h_{1}^{2} + 2\partial_{xy}f(\bar{x}, \bar{y})h_{1}h_{2} + \partial_{yy}f(\bar{x}, \bar{y})h_{2}^{2}$$

## Referenze
[^1]: [[Classe C|classe C]]