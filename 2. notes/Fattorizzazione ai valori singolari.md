---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 13-10-2024 17:50:07
links:
  - "[[Lecture 07102024132143]]"
---
# Fattorizzazione ai valori singolari
---
## Introduzione
> Data una [[Matrice|matrice]] $A \in M_{m \times n}(\mathbb{R})$, la **SVD** (_Single Value Decomposition_, o **fattorizzazione ai valori singolari**) costruisce [[Base ortonormale|basi ortonormali]] di $\mathbb{R}^{m}$ e $\mathbb{R}^{n}$ che permettono di rappresentare $A$ attraverso una [[Matrice diagonale|matrice diagonale]].
> In particolare, data $A$ una matrice reale $m \times n$ di [[Rango righe|rango]] $k$, con $k \leq n \leq m$[^1], esistono:
> - $U$ [[Matrice ortogonale|matrice ortogonale]] $m \times m$
> - $V$ matrice ortogonale $n \times n$
> - $\Sigma$ matrice diagonale $m \times n$
> 
> tali che
> $$A = U \Sigma V^{T}$$
> dove $\Sigma$ contiene sulla diagonale principale $n$ valori singolari $\sigma_{i}$:
> $$\Sigma = \begin{bmatrix} \sigma_{1} & \\ & \ddots \\ & & \sigma_{n} \\ 0 & \cdots & 0 \\ \vdots & \vdots & \vdots \end{bmatrix}$$

<u>Nota bene</u>: è simile alla [[Fattorizzazione agli autovalori|fattorizzazione agli autovalori]], ma più generale. Infatti funziona per qualunque matrice $m \times n$, invece quella agli autovalori solo per le quadrate [[Matrice diagonalizzabile|diagonalizzabili]]!

## Proprietà
Questa fattorizzazione presenta notevoli e importanti proprietà.

### 1.
> Gli elementi disposti sulla diagonale principale di $\Sigma$
> $$\sigma_{1} \geq \cdots \geq \sigma_{n} \geq 0$$
> si chiamano **valori singolari** di $A$.

### 2.
> Se $k = rk(A)$, allora i valori singolari di $A$ sono
> $$\sigma_{1} \geq \cdots \geq \sigma_{k} > 0 \ \ \ \land \ \ \ \sigma_{k+1} = \cdots = \sigma_{n} = 0$$

### 3.
> Le colonne di $U$ e $V$ sono dette rispettivamente _vettori singolari sinistri_ e _vettori singolari destri_ di $A$, associati ai valori singolari $\sigma_{i}$, e formano una base ortonormale di $\mathbb{R}^{m}$ e $\mathbb{R}^{n}$.

### 4.
> Data $A = U \Sigma V^{T}$, allora $A^{T}A$ e $AA^{T}$ sono [[Fattorizzazione agli autovalori|fattorizzabili agli autovalori]].

Prendiamo per esempio $A^{T}A$:
$$A^{T}A = (U \Sigma V^{T})^{T}(U \Sigma V^{T}) = V \Sigma^{T} U^{T} U \Sigma V^{T} = V \Sigma^{T} \Sigma V^{T} = V \begin{bmatrix}\sigma_{1}^{2} & & \\ & \ddots & \\ & & \sigma_{n}^{2}\end{bmatrix} V^{T}$$
e
$$\sigma_{i} = \sqrt{\lambda_{i}(A^{T}A)}$$
ossia i valori singolari $\sigma_{i}$ non sono altro che le radici quadrate degli autovalori $\lambda_{i}$ di $A^{T}A$.

<u>Nota bene</u>: la notazione $\lambda_{i}(A^{T}A)$ significa l'autovalore $i$-esimo della matrice $A^{T}A$.

Ecco che allora, $V \begin{bmatrix}\sigma_{1}^{2} & & \\ & \ddots & \\ & & \sigma_{n}^{2}\end{bmatrix} V^{T}$ è la fattorizzazione agli autovalori di $A^{T}A$.

La stessa cosa si può ottenere per $AA^{T}$, con la differenza che
$$AA^{T} = U \begin{bmatrix}\sigma_{1}^{2} & & \\ & \ddots & \\ & & \sigma_{n}^{2} \\ & & & 0\end{bmatrix} U^{T}$$

### 5.
Unendo la 4° osservazione con la 2°, è possibile dimostrare che
$$\sigma_{1} = \sqrt{\lambda_{\text{max}}(A^{T}A)}$$
e che, dato $k = rk(A)$,
$$\sigma_{k} = \sqrt{\lambda_{\text{min}} (A^{T}A)}$$

Per definizione, l'autovalore massimo di una matrice è detto [[Raggio spettrale|raggio spettrale]] $\rho$, per cui
$$\sigma_{1} = \sqrt{\rho(A^{T}A)} = \|A\|_{2}$$
ossia il primo valore singolare $\sigma_{1}$ corrisponde alla [[Norma matriciale|norma matriciale]] 2 di $A$.

Inoltre, se $m = n$ ($A$ è quadrata), allora
$$\|A^{-1}\|_{2} = \frac{1}{\sigma_{k}} = \frac{1}{\sigma_{n}}$$

Questo ci ricollega al calcolo del [[Numero di condizione|numero di condizione]] di una matrice quadrata $A$. Infatti sappiamo che
$$K(A) = \|A\| \cdot \|A^{-1}\| = \frac{\sigma_{1}}{\sigma_{k}}$$

Abbiamo dimostrare allora che per calcolare il numero di condizione di una matrice è possibile usare la decomposizione ai valori singolari e valutare $\sigma_{1}$ e $\sigma_{k}$ dove $k = rk(A)$.

## Referenze
[^1]: nessuno vieta che $k \leq m \leq n$, è solo un caso esempio