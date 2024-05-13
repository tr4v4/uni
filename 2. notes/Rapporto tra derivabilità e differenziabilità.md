---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 29-03-2024 18:13:51
links:
  - "[[Lecture 21032024140949]]"
  - "[[Lecture 27032024141122]]"
---
# Rapporto tra derivabilità e differenziabilità
---
## In $\mathbb{R}^{1}$
Considerando una [[Funzione matematica|funzione]] $f: \mathbb{R} \to \mathbb{R}$ e supponendo che questa sia [[Funzioni derivabili|derivabile]] in $\bar{x} \in \mathbb{R}$, per cui $\exists f'(\bar{x})$, allora otteniamo la seguente catena di equivalenze
$$f'(x) = \lim_{h \to 0} \frac{f(\bar{x}+h) - f(\bar{x})}{h} \iff \lim_{h \to 0} \frac{f(\bar{x}+h) - f(\bar{x}) - f'(\bar{x})h}{h} = 0$$
che per la definizione di [[O-piccolo|o-piccolo]] significa
$$f(\bar{x}+h) - f(\bar{x}) - f'(\bar{x}h) = o(h)$$
ovvero a tutti gli effetti uno [[Sviluppo in serie di Taylor|sviluppo di Taylor al 1° ordine]].

Allora si ha un'equivalenza del seguente tipo:
$$\exists f'(\bar{x}) \ \ \iff \ \ \text{vale Taylor al 1° ordine}$$

ovvero, per la definizione di [[Funzione differenziabile|differenziabilità]]
$$f \text{ derivabile} \iff f \text{ differenziabile}$$

## In $\mathbb{R}^{n}, n > 1$
Per una funzione $f: \mathbb{R}^{n} \to \mathbb{R}$, ovvero [[Funzione a più variabili|a più variabili]], questo legame tra lo sviluppo in serie e la derivabilità non coesiste più, ovvero che l'esistenza delle [[Derivata parziale|derivate parziali]] e la differenziabilità di una funzione sono differenti.

Tuttavia **differenziabilità implica derivabilità**. Prendiamo in esame una funzione $f: \mathbb{R}^{2} \to \mathbb{R}$ differenziabile in $(\bar{x}, \bar{y})$, per cui vale che
$$f(\bar{x} + h, \bar{y} + k) = f(\bar{x}, \bar{y}) + \partial_{x}f(\bar{x}, \bar{y}) \cdot h + \partial_{y}f(\bar{x}, \bar{y}) \cdot k + o(||(h, k)||)$$

Ora, se $k = 0$ il tutto diventa
$$f(\bar{x} + h, \bar{y}) = f(\bar{x}, \bar{y}) + \partial_{x}f(\bar{x}, \bar{y}) \cdot h + o(|h|)$$
e assumendo $h \neq 0$ si ottiene
$$\frac{f(\bar{x}+h, \bar{y}) - f(\bar{x}, \bar{y}) + o(|h|)}{h} = \partial_{x}f(\bar{x}, \bar{y})$$
ovvero _esattamente la definizione di derivata parziale $\partial_{x}f(\bar{x}, \bar{y})$_.

<u>Nota bene</u>: questo è ovvio perché _uno dei criteri della differenziabilità è proprio la derivabilità_.

## Referenze