---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 05-05-2024 13:08:27
links:
  - "[[Lecture 03052024102451]]"
---
# Matrice hessiana
---
## Introduzione
> Data $f: \mathbb{R}^{n} \to \mathbb{R}$ una [[Funzione a più variabili|funzione a più variabili]] [[Funzioni derivabili|derivabile]] due volte con continuità (quindi appartenenti alla [[Classe C|classe C2]], $\in C^{2}$) definiamo $\forall \bar{x} \in \mathbb{R}^{n}$ la [[Matrice|matrice]] $Hf(\bar{x}) \in M_{n}(\mathbb{R})$ definita come $$Hf(\bar{x})_{jk} = \frac{\partial^{2} f}{\partial x_{j} \partial x_{k}}(\bar{x})$$
> cioè come la matrice delle [[Derivata parziale seconda|derivate parziali seconde]].
> Tale matrice soddisfa $Hf(\bar{x})_{jk} = Hf(\bar{x})_{kj}$, ovvero $Hf(\bar{x}) = Hf(\bar{x})^{T} \ \ \forall \bar{x} \in \mathbb{R}^{n}$, o in altre parole $Hf(\bar{x})$ è una [[Matrice simmetrica|matrice simmetrica]], come conseguenza del [[Teorema di Schwarz|teorema di Schwarz]].

<u>Osservazione</u>: se il [[Gradiente|gradiente]] è un [[Vettore|vettore]] che contiene le [[Derivata|derivate prime]] di una funzione a più variabili, la matrice hessiana è l'oggetto (matrice) che contiene le [[Derivate di ordine superiore|derivate seconde]].

### In $\mathbb{R}^{2}$
$$Hf(x) = \begin{bmatrix} \partial_{xx}f & \partial_{xy}f \\ \partial_{yx}f & \partial_{yy}f \end{bmatrix}$$

### In $\mathbb{R}^{3}$
$$Hf(x, y, z) = \begin{bmatrix} \partial_{xx} f & \partial_{xy} f & \partial_{xz} f \\ \partial_{yx} f & \partial_{yy} f & \partial_{yz} f \\ \partial_{zx} f & \partial_{zy} f & \partial_{zz} f \end{bmatrix}$$

### Casi particolari
Ho la funzione $f: \mathbb{R}^{n} \to \mathbb{R}$ definita come
$$f(x) = ||x||^{2} = \sum\limits_{k = 1}^{n} x_{k}^{2} = x_{1}^{2} + \cdots + x_{n}^{2}$$
allora per $k \in \{1, \cdots, n\}$ ho che
$$\partial_{k}f(x) = 2x_{k}$$
Voglio passare alla matrice hessiana, e ottengo che per $j \in \{1, \cdots, n\}$ ho
$$\partial^{2}_{jk} f(x) = \frac{\partial f}{\partial x_{j}}(2x_{k})$$

Perciò ho due casi:
- $j = k$ --> $\partial^{2}_{jj} f(x) = 2$
- $j \neq k$ --> $\partial^{2}_{jk}f(x) = 0$

Costruirò la matrice hessiana allora nel seguente modo
$$Hf(x) = \begin{bmatrix} 2 & \cdots & 0 \\ \vdots & \ddots & \vdots \\ 0 & \cdots & 2 \end{bmatrix} = 2I_{n}$$[^1]

## Referenze
[^1]: 2 volte la [[Matrice identità|matrice identità]]