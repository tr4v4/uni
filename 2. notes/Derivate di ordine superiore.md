---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 27-10-2023 19:00:02
links:
  - "[[Lecture 27102023135003]]"
---
# Derivate di ordine superiore
---
## Introduzione
La [[Derivata|derivata]] di una [[Funzione matematica|funzione]] è, a sua volta, una funzione. Essa può essere [[Funzioni continue|continua]] _e/o_ [[Funzioni derivabili|derivabile]]. Se è derivabile possiamo allora ricorsivamente derivare tale funzione per riottenerne un'altra.

Questo processo porta alla formazione di **derivate di ordine superiore** al primo. _Dopo la derivata prima c'è la derivata seconda_, poi la terza, la quarta, e così via...

## Definizione
> Se una generica funzione $f^{k}(x)$ è derivabile in $x_{0} \in I$, si ha che:
> $$f^{k+1}(x_{0}) = \lim_{h \to 0} \frac{f^{k}(x_{0} + h) - f^{k}(x_{0})}{h}$$

### Esempio
> Se $f'(x)$ è derivabile in $x_{0} \in I$:
> $$f''(x_{0}) = \lim_{h \to 0} \frac{f'(x_{0} + h) - f'(x_{0})}{h}$$
> dove $f''(x_{0})$ si chiama _derivata seconda_.

## Derivabilità delle funzioni elementari
Seguendo questo schema logico, ogni funzione elementare ha un comportamento distinto in merito alle volte in cui può essere derivato.

### Polinomiali
> Le derivate dei polinomi di grado $n$ si _annullano dal grado $n+1$ in poi_:
> $$g^{k}(x) \equiv 0 \ \ \ \text{se } k \geq n+1$$

### Trigonometriche
> Le derivate delle [[Funzioni trigonometriche|funzioni trigonometriche]] si _ripetono ogni 4 volte_.

### Esponenziali
> Le derivate delle [[Funzione esponenziale|funzioni esponenziali]] _rimangono invariate_.

Si dimostra anzi che l'esponenziale è l'unica funzione ad avere tale proprietà[^1].

## Referenze
- [[Classe C]]

[^1]: ed è per questo motivo che si ha che l'esponenziale è la soluzione della basilare [[Equazione differenziale|equazione differenziale]] $Df = f$