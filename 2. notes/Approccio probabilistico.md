---
tags:
  - category/note
  - status/finished
  - topic/introduzione-all-apprendimento-automatico
date: 11-10-2025 10:48:43
links:
  - "[[Lecture 09102025131347]]"
  - "[[Lecture 16102025131029]]"
---
# Approccio probabilistico
---
## Introduzione
L'obiettivo e' il seguente. Vorremmo trovare un modello appartenente a un certo [[Spazio delle ipotesi|spazio delle ipotesi]] $H$ che piu' si avvicini a quello reale. In particolare vogliamo trovare una funzione
$$f : X \to Y$$
Ma sappiamo che questo e' difficile!
Allora subentra l'**approccio probabilistico**, in cui chiediamo qualcosa di piu' semplice: di trovare una [[Distribuzione di una variabile aleatoria|distribuzione]] su una [[Probabilita' condizionata|probabilita' condizionata]]
$$p : \mathbb{P}(Y|X)$$

Nella fattispecie, i nostri $Y$ e $X$ non sono [[Evento|eventi]], ma [[Variabile aleatoria|variabili aleatorie]], per cui ci chiediamo per qualunque $i, j$
$$p : \mathbb{P}(Y = y_{i} | X = x_{j})$$
ovvero la probabilita' che l'output sia $y_{i}$ sapendo che l'input e' $x_{j}$.

## Bayes
Gli approcci probabilistici, per calcolare questa $p$, si basano fortemente sulla [[Formula di Bayes|formula di Bayes]]:
$$\mathbb{P}(Y = y_{i} | X = x_{j}) = \frac{\mathbb{P}(Y = y_{i}) \cdot \mathbb{P}(X = x_{j} | Y = y_{i})}{\mathbb{P}(X = x_{j})} \ \ \ \ \ \forall i, j$$

Sappiamo dalla [[Formula delle probabilità totali|formula delle probabilita' totali]] che
$$\mathbb{P}(X = x_{j}) = \sum\limits_{k} \mathbb{P}(Y = y_{k}) \cdot \mathbb{P}(X = x_{j} | Y = y_{k})$$
per cui riscriviamo il denominatore in Bayes come
$$\mathbb{P}(Y = y_{i} | X = x_{j}) = \frac{\mathbb{P}(Y = y_{i}) \cdot \mathbb{P}(X = x_{j} | Y = y_{i})}{\sum\limits_{k} \mathbb{P}(Y = y_{k}) \cdot \mathbb{P}(X = x_{j} | Y = y_{k})} \ \ \ \ \ \forall i, j$$

dove:
- $\mathbb{P}(Y = y_{i})$ viene detta **prior**, ed effettivamente nel contesto del [[Machine learning|machine learning]] _identifica la probabilita' a priori che l'output appartenga alla classe $y_{i}$_;
- $\mathbb{P}(X = x_{j} | Y = y_{i})$ viene detta **likelihood**, e _identifica la probabilita' che l'input sia $x_{j}$ sapendo che l'output e' $y_{i}$_;
- $\sum\limits_{k} \mathbb{P}(Y = y_{k}) \cdot \mathbb{P}(X = x_{j} | Y = y_{k})$ viene detta **marginal likelihood**, e _identifica la probabilita' totale che $X = x_{j}$_;

Qual e' il risultato? **Sia il prior, che il likelihood, che il marginal likelihood, sono calcolabili a partire dal training set**!

## Regressione logistica
Sempre gli approcci probabilistici, comprendono l'idea di [[Regressione logistica|regressione logistica]].

## Referenze