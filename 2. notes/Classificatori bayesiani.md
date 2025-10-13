---
tags:
  - category/note
  - status/finished
  - topic/introduzione-all-apprendimento-automatico
date: 11-10-2025 11:37:28
links:
  - "[[Lecture 09102025131347]]"
---
# Classificatori bayesiani
---
## Introduzione
> I **classificatori bayesiani** sono un modelli di [[Machine learning|machine learning]] basati sull'[[Approccio probabilistico|approccio probabilistico]] in stretto rapporto con la [[Formula di Bayes|formula di Bayes]].

Fondamentalmente, sono tutte quelle tecniche, tali per cui al posto di calcolare
$$\mathbb{P}(Y = y_{i} | X = x_{j})$$
si calcola
$$\frac{\mathbb{P}(Y = y_{i}) \cdot \mathbb{P}(X = x_{j} | Y = y_{i})}{\sum\limits_{k} \mathbb{P}(Y = y_{k}) \cdot \mathbb{P}(X = x_{j} | Y = y_{k})}$$

Se si considera, chiaramente, $X$ come l'insieme delle features $X_{1}, \cdots, X_{n}$, allora la formula diventa
$$\frac{\mathbb{P}(Y = y_{i}) \cdot \mathbb{P}(X_{1} = x_{1j}, \cdots, X_{n} = x_{nj} | Y = y_{i})}{\sum\limits_{k} \mathbb{P}(Y = y_{k}) \cdot \mathbb{P}(X = x_{j} | Y = y_{k})}$$

## Funzionamento
La formula ci dice che quindi, per conoscere l'intera distribuzione $\mathbb{P}(Y = y_{i} | X = x_{j})$, e' sufficiente calcolare:
- $\mathbb{P}(Y = y_{i}) \ \ \ \forall i$, semplice;
- $\mathbb{P}(X_{1} = x_{1j}, \cdots, X_{n} = x_{nj} | Y = y_{i}) \ \ \ \forall i$, difficile!

Il secondo parametro, la likelihood, e' complesso perche' per la [[Regola della catena|regola della catena]], calcolare tali intersezioni, significa calcolare:
$$\mathbb{P}(X_{1}=x_{1j} | X_{2}=x_{2j}, \cdots, X_{n}=x_{nj}, Y=y_{i}) \cdot \ \cdots \ \cdot \mathbb{P}(X_{n}=x_{nj} | Y=y_{i})$$

Questo si traduce nel calcolare $2^{n}$ probabilita', e quindi negli stessi problemi della [[Distribuzione congiunta|distribuzione congiunta]].

Per questa ragione, nasce il [[Naive Bayes|naive Bayes]].

## Referenze