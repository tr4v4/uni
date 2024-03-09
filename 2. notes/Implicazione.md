---
tags:
  - "#category/note"
  - "#status/finished"
  - topic/analisi-I
  - topic/logica-per-informatica
date: 18-09-2023 21:00:26
links:
  - "[[Lecture 18092023093106]]"
---
# Implicazione
---
## Introduzione
Notazione:
$$p \implies q$$
dove:
- $p$ è l'**ipotesi** (_hp_)
- $q$ è la **tesi** (_th_)

Valgono le relazioni:
$$
\begin{align}
hp. \text{ condizione sufficiente e non necessaria per } th. \\
th. \text{ condizione necessaria e non sufficiente per } hp.
\end{align}
$$

## Tabella di verità
| $p$ | $q$ | $p \implies q$ |
| --- | --- | -------------- |
| 0   | 0   | 1              |
| 0   | 1   | 1               |
| 1   | 0   | 0               |
| 1   | 1   | 1               |

Nelle dimostrazioni, l'implicazione viene usata:
- in modo diretto
- [[Dimostrazione per negazione|per negazione]]

infatti si dice che sono **equivalenti**:
$$(p \implies q) \iff (\neg q \implies \neg p)$$

## Esempio
> "Se cammino, allora mi muovo"

- $p$ = _cammino_
- $q$ = mi muovo

Quindi:
- _se non cammino --> non mi muovo_ ✔️
- _se non cammino --> mi muovo_ ✔️
- _se cammino --> non mi muovo_ ❌
- _se cammino --> mi muovo_ ✔️

## Referenze
- [[Notazioni]]
- [ipotesi e tesi](https://www.youmath.it/domande-a-risposte/view/6911-ipotesi-tesi.html)