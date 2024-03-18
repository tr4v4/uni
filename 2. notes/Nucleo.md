---
tags:
  - category/note
  - status/finished
  - topic/algebra-e-geometria
date: 16-03-2024 20:17:39
links:
  - "[[Lecture 14032024111404]]"
---
# Nucleo
---
## Introduzione
> Il **nucleo**, meglio conosciuto sotto il nome di **kernel**, di un'[[Applicazione lineare|applicazione lineare]] $f: V \to W$, è definito come
> $$\ker(f) = \{v \in V | f(v) = \underline{0}\}$$
> ovvero l'_[[Insieme|insieme]] di tutti i [[Vettore|vettori]] di $V$ cui [[Immagine di funzione|immagine]] di $f$ è il vettore nullo in $W$_.

![[Drawing 2024-03-17 15.48.45.excalidraw|800]]

### Esempio
Data una funzione $f: \mathbb{R}^{3} \to \mathbb{R}^{2}$ definita come $(x_{1}, x_{2}, x_{3}) \to (x_{1}+x_{2}, x_{1}-x_{3})$ _lineare_, devo trovare $\ker(f)$. Applico la definizione di kernel su $f$, per cui
$$\ker(f) = \{(x_{1}, x_{2}, x_{3}) | f(x_{1}, x_{2}, x_{3}) = \underline{0}\} = \{(x_{1}, x_{2}, x_{3}) | (x_{1}+x_{2}, x_{1}-x_{3}) = (0, 0)\}$$

Il nucleo, allora, sarà formato da tutte quelle coppie di valori $(x_{1}+x_{2}, x_{1}-x_{3})$ per cui vale $x_{1}+x_{2} = 0$ e $x_{1}-x_{3} = 0$, ovvero a [[Sistema lineare|sistema]]
$$\begin{cases} x_{1}+x_{2} = 0 \\ x_{1}-x_{3} = 0 \end{cases}$$

<u>Nota bene</u>: si tratta di un [[Sistema lineare omogeneo|sistema lineare omogeneo]], per cui _sicuramente sappiamo che $\ker(f) \neq \varnothing$_, ma questo è triviale per la [[Applicazione lineare#$f text{ lineare} implies f(0_{V}) = 0_{W}$|proposizione]] che per ogni funzione lineare $f$ si deve avere $f(\underline{0}) = \underline{0}$.

Ad ogni modo, risolvendo il sistema ci accorgiamo che i valori dipendono da 1 variabile libera: anche se in questo caso è molto semplice, risolvendo con [[Algoritmo di Gauss|Gauss]] ci verrebbe $rr(A) = 2 = rr(A|\underline{b}) < 3 = \text{ n° incognite}$. Infatti possiamo scrivere le soluzioni come dipendenti da $x_{1}$:
$$\begin{cases} x_{2} = -x_{1} \\ x_{3} = x_{1} \end{cases}$$

da cui otteniamo che
$$\ker(f) = \{(x_{1}, -x_{1}, x_{1}) | x_{1} \in \mathbb{R}\}$$

che fattorizzando per $x_{1}$ ci viene
$$\ker(f) = \{x_{1}(1, -1, 1) | x_{1} \in \mathbb{R}\} = \langle (1, -1, 1) \rangle$$

ovvero il [[Sottospazio generato|sottospazio generato]] dal vettore $(1, -1, 1)$.

<u>Nota bene</u>: _se ci venisse chiesto se $f$ è [[Funzione iniettiva|iniettiva]] risponderemmo di no_, perché $\ker(f) \neq \{\underline{0}\}$.

## Referenze