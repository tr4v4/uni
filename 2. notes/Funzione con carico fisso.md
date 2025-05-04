---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 09-03-2025 17:25:13
links:
  - "[[Lecture 03032025091200]]"
---
# Funzione con carico fisso
---
## Introduzione
> Una **funzione con carico fisso** e' una [[Funzione matematica|funzione]] obiettivo che, fissati $b, c > 0$, e' della forma
> $$f(x) = \begin{cases} 0 & x = 0 \\ b + cx & x \in (0, u] \end{cases}$$

![[funzione-con-carico-fisso.png]]

Una situazione del genere potrebbe capire se abbiamo una macchina che consuma $0$ se la variabile $x$ e' a $0$, ma non appena viene accesa consuma almeno un valore fisso (carico fisso) $b$, che poi cresce proporzionalmente a $x$ (in base a $c$).

<u>Nota bene</u>: _non si tratta affatto di una funzione lineare_ (ha un punto di discontinuita').

## Modellizzazione
Si introduce una variabile logica $y$, che rappresenta la presenza di produzione, e si aggiungono i vincoli
$$0 \leq x \leq yu$$

Quindi, si minimizza una nuova funzione $g$ della forma
$$g(x, y) = by + cx$$

Infatti
$$g(0, 0) = 0$$
$$g(x, 1) = b + cx$$

<u>Nota bene</u>: quando $y = 0$ si ha $x = 0$ (per il vincolo aggiunto); ma quando $y = 1$ non e' detto che $x > 0$. Puo', in altre parole, capitare il caso in cui $y = 1$ e $x = 0$. In questo caso, vorrebbe dire che $g(0, 1)$ e $g(0, 0)$ corrispondono entrambe a soluzioni ammissibili, quando il valore $(0, 1)$ non dovrebbe esistere (è giusto per il modello ma non per la realtà). Se pero' assumiamo che $f$ sia da minimizzare, allora la scelta tra $g(0, 1)$ e $g(0, 0)$ darebbe sempre $(0, 0)$ come valore ottimale (ovvio, perche' $g(0, 1) > g(0, 0)$ in quanto $b > 0$).

## Referenze