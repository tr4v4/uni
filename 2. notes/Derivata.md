---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 26-10-2023 22:30:23
links:
  - "[[Lecture 23102023094009]]"
  - "[[Lecture 27102023135003]]"
---
# Derivata
---
## Definizione
> La **derivata** di una [[Funzione matematica|funzione]] $f$ in un punto $x_{0}$ corrisponde al valore del _coefficiente angolare_ della [[Retta|retta]] tangente a quel punto.

Da un punto di vista geometrico, _la derivata può essere definita con un procedimento al limite_. Se il nostro intendo è quello di calcolare il coefficiente angolare $m$ di una retta tangente ad $f$ sul punto $x_{0}$, allora attraverso un limite **ci calcoliamo tutti i coefficienti angolari delle rette che passano per due punti distinti $x_{0}$ e $x$ facendo avvicinare sempre più $x$ a $x_{0}$**. Come in figura:
![[approccio-geometrico-derivata.png]]
tale per cui
![[approccio-geometrico-rigoroso-derivata.png]]

Per cui avremo
$$m = \lim_{x \to x_{0}} \frac{f(x) - f(x_{0})}{x - x_{0}}$$

o se consideriamo $h$ come la distanza tra $x$ e $x_{0}$, ovvero $h = x - x_{0}$, allora abbiamo
$$m = \lim_{h \to 0} \frac{f(x_{0} + h) - f(x_{0})}{h}$$

Questo limite viene chiamato **rapporto incrementale**.

## Referenze
- [[Regole di derivazione]]
- [[Algebra delle derivate]]
- [[Derivate di ordine superiore]]