---
tags:
  - category/note
  - status/finished
  - topic/introduzione-all-apprendimento-automatico
date: 11-10-2025 12:26:40
links:
  - "[[Lecture 09102025131347]]"
  - "[[Lecture 10102025131023]]"
---
# MLE
---
## Introduzione
> La **MLE** (**Maximum Likelihood Estimate**) e' una metrica di stima dei parametri di _prior_ e _likelihood_ del [[Naive Bayes|naive Bayes]].

## Stima
$$\pi_{k} = \mathbb{P}(Y = y_{k}) = \frac{|\mathcal{D}\{Y=y_{k}\}|}{|\mathcal{D}|}$$
$$\theta_{ijk} = \mathbb{P}(X_{i} = x_{ij} | Y = y_{k}) = \frac{|\mathcal{D}\{X_{i} = x_{ij} \land Y = y_{k}\}|}{|\mathcal{D}\{Y = y_{k}\}|}$$

## Proprieta'
Si vede da un esempio facile, che MLE, seppur banale, **e' la stima che ovviamente si avvicina di piu' ai dati raccolti, al training set**!

Quindi se assumiamo, e lo facciamo sempre, che il training set modellizzi il mondo reale, allora MLE modellizza nel miglior modo possibile il mondo reale!

Il problema, chiaramente, e' che cosi' facendo _si "scarica" tutta la responsabilita' del modello sul training set_: se questo non e' fatto bene, le stime ne risentono in modo diretto, e quindi il modello non classifica bene.

## Problemi
### Probabilita' zero
Si pongono dei problemi quando per esempio, per una feature $X_{i}$, vale
$$\mathbb{P}(X_{i} = x_{ij} | Y = y_{k}) = 0$$
ossia che nel nostro training set non esiste il caso in cui per un certo output $y_{k}$ la feature $X_{i}$ assume il valore $x_{ij}$.

Il problema e' che nel calcolo della likelihood del naive Bayes, se capita anche solo una probabilita' pari a 0, **viene annullata completamente la probabilita' di quella classe**!

In altri termini, _un certo input non potra' mai essere associato a un certo output_.

## Referenze