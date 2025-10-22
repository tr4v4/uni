---
tags:
  - category/note
  - status/finished
  - topic/introduzione-all-apprendimento-automatico
date: 22-10-2025 21:20:42
links:
  - "[[Lecture 16102025131029]]"
---
# Regressione logistica
---
## Introduzione
### Idea
[[Naive Bayes|Naive Bayes]], e in generale i [[Classificatori bayesiani|classificatori bayesiani]], permettono di calcolare $\mathbb{P}(Y|X)$ sapendo $\mathbb{P}(Y)$ e $\mathbb{P}(X|Y)$. E', come già detto, un'_approccio generativo_, in cui cerchiamo di _stimare i dati di input dalla categoria di output_.

Ci chiediamo, allora: **ma perché non è possibile calcolare direttamente $\mathbb{P}(Y|X)$**? La verità è che non è così ovvio! Infatti, calcolare $\mathbb{P}(Y|X)$ significa, nel [[Machine learning|machine learning]] **trovare un modello nello [[Spazio delle ipotesi|spazio delle ipotesi]] che sia parametrizzabile**. In altri termini, dobbiamo _cercare di esprimere parametricamente la probabilità $\mathbb{P}(Y|X)$_, e sapendo che si tratta di una [[Distribuzione di una variabile aleatoria|distribuzione di probabilità]], non dobbiamo far altro che capire come è fatta questa distribuzione, e appunto come parametrizzarla.

### Forma
Per trovare questa forma usiamo le stesse assunzioni del [[Naive Bayes gaussiano|naive bayes gaussiano]], in particolare che:
- $Y$ sia una [[Variabile aleatoria discreta|variabile aleatoria booleana]], e in particolare con [[Distribuzione di Bernoulli|distribuzione di Bernoulli]];
- $X_{i}$ siano [[Variabile aleatoria continua|variabili aleatorie continue]];
- $X_{i}$ siano [[Indipendenza di variabili aleatorie|indipendenti]] l'una dall'altra, data $Y$;
- $\mathbb{P}(X_{i} | Y = k)$ hanno [[Distribuzione normale|distribuzioni gaussiane]] $\mathcal{N}(\mu_{ik}, \sigma_{i})$ (attenzione, non $\sigma_{ik}$, per semplicità);

Allora si dimostra, in tal caso, che
$$\mathbb{P}(Y = 1 | X = (x_{1}, \cdots, x_{n})) = \frac{1}{1 + \exp(w_{0} + \sum\limits_{i}w_{i}x_{i})}$$
e complementarmente
$$\mathbb{P}(Y = 0 | X = (x_{1}, \cdots, x_{n})) = \frac{\exp(w_{0} + \sum\limits_{i}w_{i}x_{i})}{1 + \exp(w_{0} + \sum\limits_{i}w_{i}x_{i})}$$

Quindi, se riusciamo a calcolare questi parametri $w_{0}$ e $w_{i}$, allora la classificazione (per questo caso booleano) è semplicissima.
Ricordiamo infatti che per classificare su classi booleane, è sufficiente considerare la seguente disequazione:
$$\frac{\mathbb{P}(Y = 0 | X = (x_{1}, \cdots, x_{n}))}{\mathbb{P}(Y=1|X = (x_{1}, \cdots, x_{n}))} > 1$$
Ora, sappiamo che
$$\frac{\mathbb{P}(Y = 0 | X = (x_{1}, \cdots, x_{n}))}{\mathbb{P}(Y=1|X = (x_{1}, \cdots, x_{n}))} = \exp\left(w_{0} + \sum\limits_{i}w_{i}x_{i}\right)$$
e ora prendendo il logaritmo
$$\ln\left(\frac{\mathbb{P}(Y = 0 | X = (x_{1}, \cdots, x_{n}))}{\mathbb{P}(Y=1|X = (x_{1}, \cdots, x_{n}))}\right) = w_{0} + \sum\limits_{i}w_{i}x_{i}$$
la classificazione di $X$ diventa semplicemente
$$w_{0} + \sum\limits_{i}w_{i}x_{i} > 0$$

Notare che **si tratta di un modello lineare**!

## Definizione
> La **regressione logistica** è un [[Approccio probabilistico|approccio probabilistico]] che _assume_ che
> $$\mathbb{P}(Y=1 | X = (x_{1}, \cdots, x_{n})) = \frac{1}{1 + \exp(-w_{0} - \sum\limits_{i}w_{i}x_{i})}$$
> e che cerca di stimare i parametri $w_{0}, w_{i}$.

La funzione
$$\sigma = \frac{1}{1 + e^{-x}}$$
si chiama [[Funzione logistica|funzione logistica]] o [[Sigmoide|sigmoide]].
![[funzione-logistica.png]]

Questa _trasforma un valore numerico in una [[Probabilita'|probabilità]]_.

## Training
Come calcoliamo $w_{0}, w_{i}$? Sappiamo che
$$\mathbb{P}(Y=1 | x, w) = \sigma(w_{0} + \sum\limits_{i}w_{i}x_{i})$$

Ora, dati dei sample di un training set qualunque $(x^{l}, y^{l})$, le loro probabilità, messe in produttoria tra di loro, formano
$$\prod_{l} \mathbb{P}(y^{l} | x^{l}, w) = \prod_{l} \mathbb{P}(y^{l} = 1 | x^{l}, w)^{y^{l}} \cdot \mathbb{P}(y^{l} = 0 | x^{l}, w)^{1 - y^{l}}$$
Quindi, usando la stima [[MLE]], l'ideale sarebbe quello di **massimizzare questo prodotto**: più è alto, più il modello ci prende.
Allora passiamo ai logaritmi, e otteniamo
$$\sum\limits_{l} \log(\mathbb{P}(y^{l}|x^{l}, w)) = \sum\limits_{l}(y^{l} \cdot \log(\mathbb{P}(Y=1 | x^{l}, w)) + (1 - y^{l}) \cdot \log(\mathbb{P}(Y=0 | x^{l}, w)))$$

Problema: **non esiste una soluzione analitica per questo [[Problema di ottimizzazione|problema di ottimizzazione]]**. Di fatti, sarà necessario introdurre un [[Algoritmo|algoritmo]] _iterativo_ per calcolare il massimo: [[Metodo di discesa del gradiente|metodo di discesa del gradiente]].

## Referenze