---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 09-03-2025 17:50:02
links:
  - "[[Lecture 03032025091200]]"
---
# Funzioni lineari a tratti
---
## Introduzione
Si suppone di avere come funzione obiettivo una [[Funzione matematica|funzione]] lineare a tratti del tipo
$$f(x) = \begin{cases} b_{1} + c_{1}x & x \in [a_{1}, a_{2}] \\ b_{2} + c_{2}x & x \in (a_{2}, a_{3}] \end{cases}$$
![[funzione-lineare-a-tratti.png]]

## Modellizzazione
Si introducono due variabili logiche $y_{1}, y_{2}$, tali che
$$y_{1} = \begin{cases} 1 & x \in [a_{1}, a_{2}] \\ 0 & altrimenti \end{cases} \ \ \ \ \ \ \ \ \ \ \ y_{2} = \begin{cases} 1 & x \in (a_{2}, a_{3}] \\ 0 & altrimenti \end{cases}$$

Inoltre, si introducono due variabili ausiliarie quantitative $z_{1}, z_{2}$, tali che
$$z_{1} = \begin{cases} x-a_{1} & x \in [a_{1}, a_{2}] \\ 0 & altrimenti \end{cases} \ \ \ \ \ \ \ \ \ \ \ z_{2} = \begin{cases} x-a_{2} & x \in (a_{2}, a_{3}] \\ 0 & altrimenti \end{cases}$$
catturabili dai vincoli
$$0 ≤ z_{1} ≤ (a_{2} − a_{1})y_{1} \ \ \ \ \ \ \ \ \ \ \ 0 ≤ z_{2} ≤ (a_{3} − a_{2})y_{2}$$
e
$$y_{1} + y_{2} = 1 \ \ \ \ \ \ \ \ y_{1}, y_{2} ∈ \{0, 1\}$$

Definite queste variabili catturate dai precedenti vincoli, possiamo definire la nuova funzione obiettivo $g$ nella forma
$$g(z_{1}, z_{2}, y_{1}, y_{2}) = b_{1}y_{1} + c_{1}(a_{1}y_{1} + z_{1}) + b_{2}y_{2} + c_{2}(a_{2}y_{2} + z_{2})$$
o
$$g(z_{1}, z_{2}, y_{1}, y_{2}) = (b_{1} + c_{1}a_{1})y_{1} + c_{1}z_{1} + (b_{2} + c_{2}a_{2})y_{2} + c_{2}z_{2}$$

<u>Nota bene</u>: nel punto di discontinuita' $a_{2}$, sono valide entrambe le due quadruple $(a_{2} − a_{1}, 0, 1, 0)$ e $(0, 0, 0, 1)$, dove solo la prima dovrebbe essere accettabile. Come avviene per le [[Funzione con carico fisso|funzioni con carico fisso]], si ha che se si vuole minimizzare $f$ allora verra' sempre scelta la prima quadrupla come soluzione ottimale.

## Referenze