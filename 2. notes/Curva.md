---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 03-05-2024 13:01:53
links:
  - "[[Lecture 29042024131336]]"
---
# Curva
---
## Introduzione
> Una **curva** in $\mathbb{R}^{n}$ è una [[Funzione matematica|funzione]] $r$ (o anche $s$, o $\gamma$) definita come $r: ]a, b[ \to \mathbb{R}^{n}$, dove $]a, b[ \subseteq \mathbb{R}$, caratterizzata da un parametro $t \in ]a, b[$. Di solito assume quindi la seguente forma:
> $$r(t) = (r_{1}(t), \cdots, r_{n}(t))$$

E' importante notare che una curva è una funzione di [[Classe C|classe]] $C^{1}$, ovvero che almeno _in $]a, b[$ esistono e sono [[Funzioni continue|continue]] tutte le [[Derivata|derivate prime]] della curva_.

### Esempio
#### Retta in $\mathbb{R}^{3}$
La curva $r(t) = (t, 2-t, 2t)$ è l'equazione parametrica di una retta in $\mathbb{R}^{3}$.
![[curva-retta-3d.png]]

#### Circonferenza
Possiamo scrivere l'equazione di una circonferenza in formato non cartesiano, attraverso la seguente curva
$$r(t) = (r\cos{t}, r\sin{t})$$
dove:
- $t \in [0, 2\pi[$;
- $r$ è il valore del raggio.

#### Ellisse
L'equazione di una curva che rappresenta l'ellisse è invece
$$r(t) = (\alpha \cos{t}, \beta \sin{t})$$
dove:
- $t \in [0, 2\pi[$;
- $\alpha$ e $\beta$ rappresentano quanto l'ellisse è schiacciata rispettivamente sull'asse $x$ e sull'asse $y$.

#### Elica
In $\mathbb{R}^{3}$ possiamo addirittura rappresentare un'elica attraverso una semplice curva:
$$r(t) = (\cos{t}, \sin{t}, t)$$

<u>Attenzione</u>: attenzione a non confondere l'equazione con quella che apparentemente potrebbe sembrare un _cilindro_ --> questa _è infatti una superficie, non una curva_.

## Caratteristiche
Di una curva sono importanti:
- [[Velocità di una curva|velocità]]
- [[Velocità scalare|velocità scalare]]
- [[Punto singolare|punto singolare]]
- [[Curvatura|curvatura]]
- [[Derivata lungo una curva|derivata lungo una curva]]

## Tipologie
- [[Curva regolare]]
- [[Curva semplice]]

## Referenze