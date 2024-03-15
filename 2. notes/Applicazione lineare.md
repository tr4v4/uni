---
tags:
  - category/note
  - status/finished
  - topic/algebra-e-geometria
date: 09-03-2024 11:26:02
links:
  - "[[Lecture 07032024111604]]"
  - "[[Lecture 12032024091825]]"
---
# Applicazione lineare
---
## Introduzione
Per comprendere la potenza delle applicazioni lineari, prendiamo in esempio il seguente caso. Fissiamo uno [[Spazio vettoriale|spazio vettoriale]] $V$ e $\beta = \{v_{1}, \cdots, v_{n}\}$ una sua [[Base|base]] _ordinata_, quindi prendiamo un $v \in V$ t.c. le sue [[Coordinate rispetto a una base|coordinate]] rispetto a $\beta$ sono
$$(v)_{\beta} = (\lambda_{1}, \cdots, \lambda_{n})$$
con $v = \lambda_{1}v_{1} + \cdots + \lambda_{n}v_{n}$.

Ora consideriamo la [[Funzione matematica|funzione]] $f_{\beta}: V \to \mathbb{R}^{n}$ definita come $v \to (v)_{\beta}$, ovvero una funzione che preso un vettore ci associa le sue coordinate rispetto a una certa base, si dimostra che:
- $f_{\beta}$ è _[[Iniettività di una funzione|iniettiva]]_
- $f_{\beta}$ è _[[Suriettività di una funzione|suriettiva]]_
- $f_{\beta}$ _rispetta la somma e il prodotto per scalari_

o in poche parole che **$f_{\beta}$ è un [[Isomorfismo|isomorfismo]] di spazi vettoriali**. Proprio per questo, date le proprietà degli isomorfismi, _possiamo lavorare in $V$ passando alle coordinate (quindi in $\mathbb{R}^{n}$) per poi tornare a $V$_.

## Definizione
> Dati $V, W$ spazi vettoriali, una funzione $f: V \to W$ si dice **applicazione lineare** (o **funzione lineare**, **mappa lineare**) se si ha:
> 1. $f(v + u) = f(v) + f(u) \ \ \ \forall u, v \in V$[^1]
> 2. $f(\lambda v) = \lambda f(v) \ \ \ \forall \lambda \in \mathbb{R}, \forall v \in V$
> 
> ovvero fondamentalmente se _$f$ rispetta la somma e il prodotto per scalare_.

### Esempi
#### $v \to (v)_{\beta}$
Si ha che la funzione $f: V \to \mathbb{R}^{n}$ definita come $v \to (v)_{\beta}$, ovvero la funzione che associa a un vettore le sue coordinate rispetto a una base dello spazio a cui appartiene, è un'applicazione lineare.

#### $f \to f'$
Dato $V = \{f: \mathbb{R} \to \mathbb{R}\}$ un insieme di [[Funzioni derivabili|funzioni derivabili]], $W = \{f: \mathbb{R} \to \mathbb{R}\}$, allora la funzione $d: V \to W$ definita come $f \to f'$ è lineare.

#### $\mathbb{R}^{n} \to \mathbb{R}^{m}$
Data la [[Matrice|matrice]] $A \in M_{m \times n} (\mathbb{R})$ e una funzione $f: \mathbb{R}^{n} \to \mathbb{R}^{m}$ definita come $(x_{1}, \cdots, x_{n}) \to A \cdot \begin{pmatrix} x_{1} \\ \vdots \\ x_{n} \end{pmatrix}$, ovvero che _mappa un vettore di $n$ elementi con il vettore di $m$ elementi come risultato del prodotto riga $\times$ colonna_ (tutti i [[Prodotto scalare|prodotti scalari]]) _tra il vettore in input e la matrice $A$_, questa è un'applicazione lineare.

In particolare questa funzione è molto usata in algebra lineare, e ha proprietà importantissime. Per esempio, considerata la matrice $A = \begin{pmatrix} 3 & -1 & 5 \\ 0 & 2 & 1 \end{pmatrix}$ e la funzione $f$, si ha che:
- $f(1, 0, 0) = (3, 0)$
- $f(0, 1, 0) = (-1, 2)$
- $f(0, 0, 1) = (5, 1)$

ovvero è una funzione che prese in input le _basi canoniche_ di $\mathbb{R}^{3}$ restituisce le colonne di $A$: la colonna $1$ è immagine di $e_{1}$; la colonna $2$ è immagine di $e_{2}$; ecc...

## Referenze
[^1]: a tutti gli effetti un [[Morfismo|morfismo]] di [[Gruppo|gruppi]]