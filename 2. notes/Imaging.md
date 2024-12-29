---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 24-11-2024 13:41:15
links:
  - "[[Lecture 11112024131700]]"
  - "[[Lecture 12112024091405]]"
---
# Imaging
---
## Introduzione
> L'**imaging** è una tecnica che permette di _ricavare da un'immagine "corrotta" una sua versione "pulita"_. Si tratta a tutti gli effetti di una delle maggiori applicazione di [[Problemi inversi|problemi inversi]].

## Presupposti
Per poter procedere con l'imaging, è necessario conoscere la [[Convoluzione|convoluzione]].

## Idea
Ogni immagine scattata da un dispositivo di acquisizione, attraverso un _processo di digitalizzazione_, viene memorizzata come un [[Array|array]] bidimensionale composto da _pixel_ che ha per valore l'intensità del bianco (assumiamo di star lavorando in una scala di grigi). Quindi, possiamo vedere un'immagine salvata in [[Memorie|memoria]] come matrice $A \in \mathbb{R}^{M \times N}$.

Tuttavia, l'acquisizione dell'immagine è un processo che per natura genera degli errori, che si manifestano come _rumore_ nell'immagine. L'**obiettivo dell'imaging è, una volta modellato tale rumore, ricavare l'immagine originale**.

Il modello matematico che descrive il processo di acquisizione di un'immagine è definito in 2 fasi:
1. [[PSF]]
2. [[Rumore bianco]]

### Problema inverso
Riassumendo, abbiamo che, se $x$ è l'immagine originale, allora la PSF $\mathcal{A}$ è modellizzata come:
$$\mathcal{A}(x) = [K * (x | \mathcal{P})]$$

Il rumore bianco, invece, viene modellizzato come una matrice $w$ ottenuta da un sampling di una funzione random (con caratteristiche particolari).

Uniamo questi due modelli in un'unica equazione, tale che $y^{\delta}$ sia l'immagine acquisita:
$$y^{\delta} = \mathcal{A}(x) + w = [K * (x | \mathcal{P})] + w$$

Se l'obiettivo, conoscendo $y^{\delta}$ e il modello $A$, è quello di ricavare $x$, **possiamo scrivere il problema come un problema inverso**: data l'immagine osservata $y^{\delta}$ e la nota PSF ($K$), si vuole ripulire l'immagine per riottenere l'oggetto acquisito.
$$y^{\delta} = Ax + w$$
dove $Ax = K * x$.
![[imaging.png]]

## Metodi
### Naive
Una prima soluzione al problema inverso potrebbe essere quella di risolvere il problema dei minimi quadrati:
$$\min_{x} {\|Ax - y^{\delta}\|_{2}}^{2}$$
dove $y^{\delta}$ è l'immagine acquisita con rumore $w$ ($= \delta$).
Per risolvere il problema, si potrebbe quindi pensare alla [[Fattorizzazione ai valori singolari|SVD]], tuttavia nell'imaging le matrici $A$ sono talmente grandi che **la SVD risulterebbe troppo costosa computazionalmente**. Ciò che si fa, allora, è, supponendo che $A$ abbia rango massimo (realistico in quanto si tratta di immagini), di _passare alle equazioni normali_ $A^{T}Ax = A^{T}y^{\delta}$, _risolvendo poi il sistema normale con il comodo [[CGLS]]_ ([[Algoritmo iterativo|metodo iterativo]]). Ricordiamo infatti che questo metodo, oltre ad essere poco costoso computazionalmente, è in grado di gestire matrici _grandi_ e _sparse_, come quelle che si incontrano nell'imaging.
Si deve aprire una breve parentesi sulla soluzione di sistemi in cui $x$ e $y^{\delta}$ sono immagini, e quindi matrici: **devono essere trasformati in vettori attraverso una tecnica chiamata [[Riordinamento lessicografico|riordinamento lessicografico]]** (in [[Python]] `numpy.reshape()`).

Ad ogni modo, come già affrontato con i problemi inversi, il risultato ottenuto è _inaccettabile_, perché **dominato dal rumore**.

### Regolarizzazione
Anche in questo caso, per risolvere il problema inverso, si fa uso di [[Regolarizzazione|metodi di regolarizzazione]]. In particolare, se ne citano 3:
- _[[Fattorizzazione ai valori singolari troncata|TSVD]]_ --> non è comunque efficiente, perché richiede una [[Fattorizzazione ai valori singolari|decomposizione ai valori singolari]] che _per matrici grandi è troppo costosa_;
- _[[Regolarizzazione alla Tikhonov|regolarizzazione di Tikhonov]]_ con eventuale _[[Principio di massima discrepanza|principio di massima discrepanza]]_;
- _[[Variazione totale|variazione totale]]_.

## Metriche
Le tecniche sopra descritte, possono essere valutate in [[Problema test|problemi test]] attraverso l'uso delle seguenti metriche:
- **ER** - _errore relativo_ $$ER = \frac{{\|x - x_{GT}\|_{2}}^{2}}{{\|x_{GT}\|_{2}}^{2}}$$ con valori $[0, 1]$
- **PSNR** - _Peak Signal-to-Noise Ratio_ $$PSNR = 10 \cdot \log_{10} \left( \frac{(\max_{i,j}|x_{i,j}|)^{2}}{MSE} \right)$$ dove **MSE** è il _Mean Squared Error_ $$MSE = \frac{{\|x - x_{GT}\|_{2}}^{2}}{M \cdot N}$$ con valori $[0, 100]$
- **SSIM** - _Structural Similarity Index_, il migliore, con valori $[0, 1]$

## Referenze