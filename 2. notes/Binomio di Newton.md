---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 24-09-2023 18:53:38
links:
  - "[[Lecture 22092023133316]]"
  - "[[Lecture 25092023093433]]"
---
# Binomio di Newton
---
## Definizione
> $$(a + b)^{n} = \sum\limits_{k=0}^{n} \binom{n}{k} a^{n-k}b^{k}$$

Esempi:
$$(a + b)^{2} = a^{2} + 2ab + b^{2}$$
$$(a + b)^{3} = a^{3} + 3a^{2}b + 3ab^{2} + b^{3}$$
$$(a + b)^{4} = a^{4} + 4a^{3}b + 6a^{2}b^{2} + 4ab^{3} + b^{4}$$


## Dimostrazione
### $a^{n-k}b^{k}$
Se guardiamo le _parti letterali_ negli esempi sopra riportati ci accorgiamo che gli esponenti di $a$ partono da $n$ e poi scendono fino a $0$, mentre gli esponenti di $b$ partono da $0$ e salgono fino a $n$.

### $\binom{n}{k}$
Ogni _coefficiente_ dei monomi coincide con il numero di combinazioni che si possono ottenere di quel preciso monomio facendo la moltiplicazione tra i binomi: si usa infatti il [[Coefficiente binomiale|coefficiente binomiale]]. Quindi per un totale di $n$ insiemi al passo $k$ avremo $\binom{n}{k}$ monomi.

## Triangolo di Tartaglia
I coefficienti dei monomi sono calcolabili anche attraverso uno schema chiamato **triangolo di Tartaglia**, che consiste nella costruzione di tutti i possibili coefficienti dei binomi di Newton a partire dal caso 1:
![[triangolo-di-tartaglia.png]]

Lo schema vuole che il $k$-esimo coefficiente del $n$-esimo binomio sia la somma dei due coefficienti soprastanti. Questa regola funziona grazie a **una delle due proprietà dei coefficienti binomiali**:
$$\binom{n}{k-1} + \binom{n}{k} = \binom{n+1}{k}$$

Notiamo infatti come si possa tradurre in: _il coefficiente binomiale successivo alla corrente posizione ($\binom{n+1}{k}$) è la somma del coefficiente binomiale della riga precedente nella posizione precedente ($\binom{n}{k-1}$) con il coefficiente binomiale della riga precedente nella corrente posizione ($\binom{n}{k}$)_.

## Referenze