---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 21-10-2024 12:20:24
links:
  - "[[Lecture 14102024131954]]"
  - "[[Lecture 15102024091721]]"
---
# Approssimazione di dati
---
## Introduzione
Approssimare dei dati significa ricavare dal _rumore_ un _pattern_ attraverso un [[Algoritmo|algoritmo]] che _approssimi_ tali dati per _capirne la tendenza e prevedere comportamenti futuri_.

## Preliminari
Per definire i modelli di approssimazione, è prima necessario introdurre alcune nozioni.

### Variabili
Definiamo:
- **variabili indipendenti** (o **di input**) le variabili che non dipendono da niente --> indicate con $x$;
- **variabili dipendenti** (o **di output**) le variabili che dipendono da altre variabili --> indicate con $y$;
- **set di dati** (o **dataset**) una collezione di coppie di valori associati $\{(x_{1}, y_{1}), \cdots, (x_{n}, y_{n})\}$ (tra variabili indipendenti e variabili dipendenti).

### Parametri
Definiamo:
- **iperparametri** tutti i parametri del modello di approssimazione che devono essere selezionati a mano dall'utente;
- **parametri** tutti i parametri calcolati dal modello e non modificabili.

### Assunzioni
Al fine di definire i modelli, bisogna assumere due concetti importanti sulla composizione dei dati di input:
1. _i dati seguono una curva complessa ma con un pattern riconoscibile_;
2. _i dati non sono disposti lungo la curva in maniera esatta, ma c'è del **rumore** che fa smuovere i dati rispetto alla curva_;

Formalizzati si possono riassumere come:
1. $\exists f(x) : y \approx f(x)$
2. $\exists e : y = f(x) + e \ \ \ \forall x$

<u>Nota bene</u>: per semplificazione assumo che il rumore $e$ sia una _gaussiana_.

## Definizione
> Fissata una funzione $f(x) : y \approx f(x)$, allora un **metodo di approssimazione** è un qualunque algoritmo che, fissato un modello $f_{\theta}(x)$ dipendente da un insieme di parametri $\theta$, _calcola il valore di tali parametri tali che $f_{\theta}(x)$ sia il più possibile vicina a $f(x)$_.

Solitamente, si assume che $f(x)$ sia una [[Polinomio|funzione polinomiale]], in particolare un polinomio nella variabile $x$ di grado $d$:
$$f(x) = a_{0} + a_{1}x + a_{2}x^{2} + \cdots + a_{d}x^{d} = \sum\limits_{k=0}^{d} a_{k}x^{k}$$

Questo perché i polinomi sono estremamente flessibili, e ricordando [[Polinomi di Taylor|Taylor]] possono approssimare qualunque funzione sotto una determinata soglia di errore[^1]. Inoltre, **un polinomio di grado $d$ è unicamente determinato dai suoi coefficienti $a_{0}, a_{1}, \cdots, a_{d}$**: andiamo proprio a porre di fatto $\theta = (a_{0}, a_{1}, \cdots, a_{d})$, ovvero _modelleremo i coefficienti di $f_{\theta}(x)$ in modo tale da approssimare $f(x)$_.

## Metodi
- [[Approssimazione ai minimi quadrati]]

## Referenze
- [[Problema test]]

[^1]: l'[[O-piccolo|o-piccolo]]