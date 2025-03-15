---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 23-02-2025 15:24:57
links:
  - "[[Lecture 19022025091652]]"
  - "[[Lecture 24022025091339]]"
---
# Programmazione lineare
---
## Introduzione
> Un **problema di programmazione lineare** (**PL**) e' un [[Problema di ottimizzazione|problema di ottimizzazione]] definito dando:
> - un numero finito $n \in \mathbb{N}$ di _variabili reali_ $x = (x_{1}, \cdots, x_{n}) \in \mathbb{R}^{n}$;
> - una _funzione obiettivo_ $f: \mathbb{R}^{n} \to \mathbb{R}$ nella forma $f(x) = cx$ dove $c \in \mathbb{R}^{n}$ ([[Prodotto scalare|prodotto scalare]]);
> - un insieme di $m$ _vincoli lineari_, tutti in una delle forme seguenti:
	- $ax = b$
	- $ax \leq b$
	- $ax \geq b$
	- dove $a \in \mathbb{R}^{n}$ e $b \in \mathbb{R}$

<u>Nota bene</u>: le variabili reali corrispondono a $\mathbb{G}$, la funzione obiettivo a $c_{\mathcal{P}}$ e i vincoli lineari a $\mathbb{F}_{\mathcal{P}}$.

## Caratterizzazione
Un problema di PL puo' **sempre** essere espresso nella forma
$$\max\{cx | Ax \leq b\}$$
con $A \in \mathbb{R}^{m \times n}$ e $b \in \mathbb{R}^{m}$ (un [[Sistema lineare|sistema lineare]] di disequazioni).

Infatti:
- ogni riga di $(A|b)$ e' un vincolo degli $m$ totali, e il vettore colonna $x$ sono le variabili;
- ogni vincolo $ax = b$ diventa la coppia di vincoli $ax \leq b$ e $ax \geq b$;
- ogni vincolo $ax \geq b$ diventa $(-a)x \leq (-b)$ (e' equivalente).

## Steps
Per modellizzare un problema di programmazione lineare occorre seguire 3 semplici steps:
1. _capire le variabili in gioco_;
2. _capire la funzione obiettivo_;
3. _capire i vincoli_;

## Esempi
### Pianificazione della produzione
![[pianificazione-produzione.png]]

#### Variabili
Le variabili saranno:
- $x_{C}$ --> numero di processori Coloron prodotti settimanalmente;
- $x_{P}$ --> numero di processori Pintium prodotti settimanalmente;

#### Funzione obiettivo
Dobbiamo massimizzare il ricavo totale, ma da cosa e' determinato? Ogni processore Coloron si vende a 200\$ al pezzo, mentre ogni processore Pintium si vende 500\$ al pezzo, ma bisogna tenere conto della resa! Per cui il ricavo totale e':
$$f(x_{C}, x_{P}) = \frac{3}{5} x_{C}*200 + \frac{1}{2}x_{P}*500 = 120x_{C} + 250x_{P}$$

Per cui ci interessa
$$\max{f(x_{C}, x_{P})}$$

#### Vincoli
Partiamo dal fatto che si possono realizzare fino a 3000 wafer alla settimana, e sapendo che su ogni wafer ci sono o 500 Coloron, o 300 Pintium, allora il numero di wafer alla settimana vincolato sara' (tenendo conto della resa):
$$\frac{3}{5}\frac{x_{C}}{500} + \frac{1}{2}\frac{x_{P}}{300} \leq 3000 \iff \frac{3}{2500}x_{C} + \frac{1}{600}x_{P} \leq 3000$$

Inoltre, viene imposto un tetto massimo di produzione delle due tipologie di processori (considerando la resa):
$$0 \leq \frac{3}{5}x_{C} \leq 700000$$
$$0 \leq \frac{1}{2}x_{P} \leq 400000$$

<u>Nota bene</u>: questo problema dovrebbe essere di [[Programmazione lineare intera|PLI]], inserendo dei vincoli di interezza su $x_{P}, x_{C}$; in questo caso ci semplifichiamo la vita, e approssimiamo all'intero più vicino.

## Referenze