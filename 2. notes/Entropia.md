---
tags:
  - category/note
  - status/finished
  - topic/introduzione-all-apprendimento-automatico
date: 01-10-2025 19:39:37
links:
  - "[[Lecture 26092025131224]]"
---
# Entropia
---
## Introduzione
> L'**entropia** $H(X)$ di una [[Variabile aleatoria discreta|variabile aleatoria discreta]] $X$ e'
> $$H(X) = -\sum\limits_{i=1}^{n} \mathbb{P}(X = i) \log_{2}{(\mathbb{P}(X = i))}$$
> ossia una somma pesata (sulla [[Densita' discreta|densita' discreta]] di $X$) di $\log_{2}(\mathbb{P}(X = i))$, detta _funzione di informazione_.

Questa misura il **grado di disordine/impurita'/omogeneita'**, dell'informazione ricavabile dalla [[Distribuzione di una variabile aleatoria|distribuzione]] di $X$.

### Casi
E' massima quando $X$ e' [[Distribuzione uniforme discreta|uniformemente distribuita]] tra tutti i suoi $n$ valori, e in tal caso si ha
$$H(X) = \log{n}$$
E' minima quando la distribuzione di $X$ si concentra su un singolo valore del suo supporto, e in tal caso si ha
$$H(X) = 0$$

<u>Nota bene</u>: in quest'ultimo caso, significa che un solo valore del supporto ha densita' discreta pari a 1, e tutti gli altri pari a 0. Ma questo significa che nella sommatoria di $H(X)$ _appaiono dei logaritmi con argomenti pari a 0_. Se pero' guardiamo il caso al limite, essendo questi moltiplicati per 0, vince il termine $\mathbb{P}(X = i)$.

#### Esempio
Fissiamo il supporto di $X$ a $S_{X} = \{0, 1\}$. Il grafico dell'entropia al variare di $\mathbb{P}(X = 1)$ e' il seguente:
![[entropia-grafico-1.png]]

## Altre entropie
### Entropia condizionale
$$H(X|Y=v) = -\sum\limits_{i=1}^{n} \mathbb{P}(X = i|Y=v) \log_{2}{(\mathbb{P}(X = i|Y=v))}$$
Entropia condizionale di $X$ dato $Y$:
$$H(X|Y) = \sum\limits_{v=1}^{m} \mathbb{P}(Y=v)H(X|Y=v)$$

## Referenze