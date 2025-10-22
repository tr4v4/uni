---
tags:
  - category/note
  - status/finished
  - topic/introduzione-all-apprendimento-automatico
date: 11-10-2025 12:02:03
links:
  - "[[Lecture 09102025131347]]"
  - "[[Lecture 10102025131023]]"
---
# Naive Bayes
---
## Introduzione
> Il **naive Bayes** e' un [[Classificatori bayesiani|classificatore bayesiano]] che assume l'[[Indipendenza di variabili aleatorie|indipendenza]] delle $n$ [[Features di un dato|features]].

Infatti, sappiamo che i classificatori bayesiano devono calcolare
$$\frac{\mathbb{P}(Y = y_{k}) \cdot \mathbb{P}(X_{1} = x_{1j}, \cdots, X_{n} = x_{nj} | Y = y_{k})}{\sum\limits_{i} \mathbb{P}(Y = y_{i}) \cdot \mathbb{P}(X_{1} = x_{1j}, \cdots, X_{n} = x_{nj} | Y = y_{i})}$$
e che il grande problema sta nella congiunzione $\mathbb{P}(X_{1} = x_{1j}, \cdots, X_{n} = x_{nj} | Y = y_{k})$, ossia nel _calcolo della likelihood_.

Se noi assumiamo che $X_{1} \perp\!\!\!\perp \cdots \perp\!\!\!\perp X_{n}$, notiamo che
$$\mathbb{P}(X_{1} = x_{1j}, \cdots, X_{n} = x_{nj} | Y = y_{k}) = \prod_{i}\mathbb{P}(X_{i} = x_{ij} | Y = y_{k})$$

In altri termini, assumiamo che non ci sia alcuna correlazione tra le [[Features di un dato|features]]! E che quindi una feature $X_{i}$ dipenda solo e unicamente dall'output $Y$.

Chiaramente si tratta di un'assunzione forte, ma ci consente di semplificare i calcoli!

## Funzionamento
A questo punto, la probabilita'
$$p : \mathbb{P}(Y = y_{i} | X_{1} = x_{1j}, \cdots, X_{n}=x_{nj})$$
si calcola con naive Bayes nel seguente modo:
$$\mathbb{P}(Y = y_{k} | X_{1} = x_{1j}, \cdots, X_{n}=x_{nj}) = \frac{\mathbb{P}(Y = y_{k}) \cdot \prod_{i}\mathbb{P}(X_{i} = x_{ij} | Y = y_{k})}{\mathbb{P}(X_{1}=x_{1j}, \cdots, X_{n}=x_{nj})}$$

dove, ricordiamo:
- $\mathbb{P}(Y = y_{k})$ e' la **prior**;
- $\prod_{i}\mathbb{P}(X_{i} = x_{ij} | Y = y_{k})$ e' la **likelihood**;
- $\mathbb{P}(X_{1}=x_{1j}, \cdots, X_{n}=x_{nj})$ e' la **marginal likelihood**;

Attenzione: **a noi interessa solo il numeratore, ossia la prior e la likelihood**! Infatti la marginal likelihood e' ininfluente.

Di fatto, l'_inferenza_ del modello, ossia la classificazione di un nuovo dato $x^{new} = (x_{1}, \cdots, x_{n})$, e' calcolato cosi':
$$Y^{new} = \arg\max_{y_{k}} {\mathbb{P}(Y = y_{k}) \cdot \prod_{i}\mathbb{P}(X_{i} = x_{i} | Y = y_{k})}$$
ossia _il risultato e' la classe $y_{k}$ che massimizza il prodotto tra la prior e la likelihood_.

<u>Nota bene</u>: i risultati della predizione (prior $\times$ likelihood) non sono probabilita'! Per esserlo dovrebbero essere normalizzati sulla marginale $\mathbb{P}(X_{1}=x_{1j}, \cdots, X_{n}=x_{nj})$. Ma non ci importa!

## Training
Ci manca solo da stabilire in che modo calcolare:
- la prior $\mathbb{P}(Y = y_{k})$;
- la likelihood $\prod_{i}\mathbb{P}(X_{i} = x_{ij} | Y = y_{k})$;

Si utilizza la seguente notazione:
$$\pi_{k} = \mathbb{P}(Y = y_{k})$$
$$\theta_{ijk} = \mathbb{P}(X_{i} = x_{ij} | Y = y_{k})$$

Quindi la fase di training consiste semplicemente nel trovare $\pi_{k}$ per ogni $k$, e $\theta_{ijk}$ per ogni $i, j, k$.

### Stime
Esistono tante stime per la prior e la likelihood, in particolare si citano:
- [[MLE]];

## Log likelihood
Di solito, per semplificare i calcoli, non si classifica mai con
$$Y^{new} = \arg\max_{y_{k}} {\pi_{i} \cdot \prod_{i}\theta_{ijk}}$$
ma si usa invece
$$Y^{new} = \arg\max_{y_{k}} {\log(\pi_{i}) + \sum\limits_{i}\log(\theta_{ijk})}$$

Il risultato e' il medesimo, perche' _i logaritmi sono monotoni_. Ma **ora abbiamo una sommatoria, invece che dei prodotti**.

Inoltre, ci sono problemi tali per cui _le $n$ features $X_{i}$ si possono spesso riassumere in un'unica feature $X$_, perche' _si comportano allo stesso modo_, o almeno si assume che sia cosi'.

In tal caso, si ha che
$$\theta_{ijk} = \theta_{i'jk} = \theta_{jk}$$

Abbiamo una sola feature $X$. Quindi la sommatoria su $\theta$ diventa
$$\sum\limits_{i}\log(\theta_{ijk}) = \sum\limits_{j} n_{j} \cdot \log(\theta_{jk})$$
dove $n_{j}$ e' il numero di volte in cui la feature $X = x_{j}$ nell'input $x^{new}$.

Vedendo le cose in questo modo, ecco che la sommatoria diventa il [[Prodotto scalare|prodotto scalare]] tra 2 vettori:
- $s_{k} = (\log(\theta_{1k}), \cdots, \log(\theta_{mk}))$, dove $m$ sono i valori assunti dalla feature $X$ --> sono i logaritmi delle frequenze di ogni valore della feature nella classificazione $k$;
- $d = (n_{1}, \cdots, n_{m})$, dove $m$ sono sempre i valori assunti dalla feature $X$ --> sono il numero di volte in cui compare il valore $j$-esimo della feature nell'input $x^{new}$.

La log likelihood, allora diventa:
$$d \cdot s_{k}$$

Questo ha 2 interpretazioni:
- **geometricamente**, _la log likelihood esprime quanto siano vicini i due vettori in base all'angolo_;
- **analiticamente**, e' semplicemente il prodotto scalare.

## Problemi
### Natura lineare
Ma se le features non fossero indipendenti? Si dimostra che naive Bayes e' un **classificatore lineare**, vale a dire che guarda una sola feature alla volta, in realzione all'output: _non riesce a catturare classificazioni anche semplici, in cui si le feature sono correlate_.

Questo si dimostra facilmente, ci basta considerare $X_{i}, Y$ booleane, e classificare $x^{new}$ come
![[natura-lineare-naive-bayes-1.png]]
quindi passare ai logaritmi
![[natura-lineare-naive-bayes-2.png]]

Ora usiamo il fatto che per una variabile booleana $x$ vale:
$$f(x) = x \cdot f(1) + (1 - x) \cdot f(0)$$
e
![[natura-lineare-naive-bayes-3.png]]

Gli algoritmi di classificazione lineare sono basati su una _[[Combinazione lineare|combinazione lineare]] delle features_: a ognuna e' associato un peso diverso, e a seconda di un threshold facciamo la classificazione.

## Referenze
- [[Naive Bayes gaussiano]]