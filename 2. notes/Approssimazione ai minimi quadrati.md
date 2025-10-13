---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 21-10-2024 12:51:57
links:
  - "[[Lecture 14102024131954]]"
  - "[[Lecture 15102024091721]]"
---
# Approssimazione ai minimi quadrati
---
## Introduzione
> L'**approssimazione ai minimi quadrati** è un [[Approssimazione di dati|metodo di approssimazione di dati]] che consiste nel _ricondurre il problema dell'approssimazione in quello della [[Problema dei minimi quadrati|ricerca dei minimi quadrati]]_.

## Idea
Come requisito assumiamo che la funzione da approssimare sia $f(x)$ e che $f_{\theta}(x)$ sia il modello _[[Polinomio|polinomiale]]_ che vogliamo avvicinare a $f(x)$. Se consideriamo $\alpha = (a_{0}, a_{1}, \cdots, a_{d})$ il vettore $\in \mathbb{R}^{d+1}$ dei coefficienti, allora
$$f_{\theta}(x, \alpha) = \sum\limits_{k=0}^{d} a_{k}x^{k}$$

Se definiamo
$$x^{(d)} = (x^{0}, x^{1}, \cdots, x^{d}) \in \mathbb{R}^{d+1}$$

allora possiamo definire $f_{\theta}(x, \alpha)$ come il [[Prodotto scalare|prodotto scalare]] tra i vettori $\alpha$ e $x^{(d)}$:
$$f_{\theta}(x, \alpha) = \alpha^{T}x^{(d)}$$

Detto ciò, lo scopo iniziale è di approssimare $f_{\theta}(x, \alpha)$ a $f(x)$, ovvero di _trovare il vettore dei coefficienti $\alpha$ tale che minimizzi $f_{\theta}(x_{i}, \alpha) - f(x_{i}) \ \ \ \forall i \in \{1, \cdots, n\}$_, dove $n$ è il numero di variabili indipendenti (dati in input). In altre parole si cerca $\alpha$ tale che:
$$\min_{\alpha} \sum\limits_{i=1}^{n} (f_{\theta}(x_{i}, \alpha) - y_{i})^{2}$$

<u>Nota bene</u>: facciamo la somma tra i quadrati perché è semplicemente più comodo, di fatto ci vogliamo ricondurre ai minimi quadrati.

Ricordando $f_{\theta}(x, \alpha) = \alpha^{T}x^{(d)}$, allora il problema diventa
$$\min_{\alpha} \sum\limits_{i=1}^{n} (\alpha^{T} x^{(d)}_{i} - y_{i})^{2}$$

Ora, definisco $X$ come la matrice che per righe ha $x_{i}^{(d)}$ per ogni $i = 1, \cdots, n$:
$$X = \begin{bmatrix}{x_{1}^{(d)}}^{T} \\ \vdots \\ {x_{n}^{(d)}}^{T}\end{bmatrix} = \begin{bmatrix} x_{1}^{0} & \cdots & x_{1}^{d} \\ \vdots & \ddots & \vdots \\ x_{n}^{0} & \cdots & x_{n}^{d} \end{bmatrix} \in \mathbb{R}^{n \times (d+1)}$$

così che, a questo punto, possa andare a scrivere la sommatoria precedente come
$$\min_{\alpha} {\|X \alpha - y\|_{2}}^{2}$$
dove $y = (y_{1}, \cdots, y_{n})$. La matrice $X$ è chiamata **[[Matrice di Vandermonde|matrice di Vandermonde]]**.

Analizzando passo per passo, il prodotto matriciale $X\alpha$ produce il vettore $\in \mathbb{R}^{n}$ di valori di $f_{\theta}(x, \alpha)$ per ogni $x_{i}$ (con $i = 1, \cdots, n$). Quindi sostanzialmente all'interno della [[Norma vettoriale|norma]] si avrà il [[Vettore|vettore]] differenza tra i valori calcolati da $f_{\theta}$ e i valori reali $f$. La _norma al quadrato sarà quindi la sommatoria tra i quadrati degli elementi di questo vettore_: un numero (il **residuo**), che si vuole minimizzare al variare di $\alpha$.

Il problema ottenuto, si noti, **non è altro che un semplice problema ai minimi quadrati**.

## Algoritmo
Dobbiamo risolvere
$$\min_{\alpha} {\|X \alpha - y\|_{2}}^{2}$$
allora procediamo secondo i dettami del problema ai minimi quadrati.

In particolare:
- se $X$ ha rango massimo, ovvero (essendo $n \gg d+1$) $rk(X) = d+1$, allora possiamo risolvere il sistema alle equazioni normali con la [[Fattorizzazione di Cholesky|fattorizzazione di Cholesky]];
- se $X$ non ha rango massimo, allora bisogna procedere con la [[Fattorizzazione ai valori singolari|fattorizzazione SVD]].

### Cholesky
In questo caso $rk(X) = d+1$, per cui possiamo risolvere il sistema alle equazioni normali
$$X^{T}X\alpha = X^{T}y$$

ed essendo $X^{T}X \in \mathbb{R}^{(d+1) \times (d+1)}$ una _[[Matrice|matrice]] [[Matrice simmetrica|simmetrica]] definita positiva_, possiamo decomporla con Cholesky:
$$X^{T}X = LL^{T}$$

Quindi, risolviamo i due sistemi triangolari:
$$\begin{cases} Lz = X^{T}y \\ L^{T}\alpha = z \end{cases}$$

### SVD
In questo caso $k = rk(X) < d+1$, per cui decomponiamo $X = U \Sigma V^{T}$, e calcoliamo $\alpha$ con la sommatoria
$$\alpha = \sum\limits_{i=1}^{k} \frac{u_{i}^{T} y}{\sigma_{i}}v_{i}$$

## Problemi
Ricordando la definizione di _iperparametri_, nel caso del modello di approssimazione ai minimi quadrati questi consistono solo e unicamente in $d$: **il grado del polinomio approssimante**.

Tralasciando il caso del [[Problema test|problema test]], **noi non sappiamo a priori il grado della funzione polinomiale $f$ originaria, per cui la scelta di $d$ è arbitraria**. Tale valore, tuttavia, è proprio la causa dei due maggiori problemi nell'ambito dell'approssimazione dati:
- $d$ _troppo bassi_ --> [[Underfit|underfit]];
- $d$ _troppo alti_ --> [[Overfitting|overfit]].

### Underfit
Prendiamo il caso $d = 1$, ossia quello di una _retta come funzione approssimante_. Questa, nella maggior parte dei casi, **non cattura la complessità della $f$ originaria**: è una _semplificazione eccessiva dell'andamento dei dati_, per cui _di poca utilità_.

### Overfit
Prendiamo il caso $d \gg d'$ dove $d'$ è il grado della $f$ originaria. In questo caso la funzione approssimante ha una potenza troppo elevata, e _tende a scaricarla in funzione del rumore_[^1]! Il risultato è una _curva troppo flessibile_, **incapace di catturare il comportamento generale della $f$ originaria**.

### Tuning
Attraverso delle operazioni di **tuning** cerchiamo di impostare correttamente gli iperparametri per ottenere un modello che non soffra né di underfit né di overfit.

In questo modello, l'idea è di _cercare di minimizzare il residuo_ mantenendolo distante da 0, altrimenti implicherebbe l'interpolazione del rumore.
$$r(\alpha) = {\|X\alpha - y\|_{2}}^{2}$$

#### Underfit
> _L'underfit non si verifica se si sceglie l'iperparametro che fa arrestare la decrescita del residuo_.

Risolvere l'underfit è abbastanza semplice in questo modello. E' sufficiente calcolare i residui per ogni grado $d$ provato. Si nota che al crescere del grado il residuo $r$ _si arresta_, per poi crollare dopo un certo valore: **è al valore di $d$ che fa arrestare la sua decrescita che non si verifica più l'underfit**.

#### Overfit
Risolvere l'overfit vorrebbe dire **capire dopo quale grado $d$ il modello approssimante viene influenzato troppo dal rumore**: è difficilissimo. Per questo si utilizza una tecnica chiamata [[Regolarizzazione|regolarizzazione]].

## Referenze
[^1]: si dice che [[Interpolazione|interpola]] il rumore.