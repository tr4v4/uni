---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 04-11-2023 13:12:53
links:
  - "[[Lecture 03112023134932]]"
---
# Studio della derivata prima
---
## Introduzione
Lo studio della [[Derivata|derivata]] _prima_ di una [[Funzione matematica|funzione]] che si sta [[Studio di funzione|studiando]] consente di analizzare di quest'ultima:
- [[Massimo e minimo relativo|massimi e minimi relativi]]
- [[Criterio di monotonia|monotonia della funzione]]

e consiste in due semplici passi:
1. **annullamento della derivata**
2. **[[Studio del segno|studio del segno]] della derivata**

### Annullamento
$$f'(x) = 0$$

Quando annulliamo la derivata stiamo cercando, sfruttando il [[Teorema di Fermat|teorema di Fermat]], di _catturare punti di massimo o minimo relativo_. Ricordiamo che lo stesso teorema non garantisce che se la derivata si annulla per un punto allora esso corrisponda necessariamente a un massimo o un minimo locale (non vale il _coimplica_ $\iff$).

Per cui è un bene, una volta calcolata la derivata prima attraverso le [[Regole di derivazione|regole di derivazione]] e posta uguale a 0, studiarne il segno per verificare che effettivamente la funzione per quel punto presenti un massimo o un minimo (in accordo, tra l'altro, con i principi del [[Criterio di monotonia|criterio di monotonia]]).

### Studio del segno
$$f'(x) > 0$$

Come per qualunque altro studio del segno, ponendo la funzione $> 0$, riusciamo a classificare i suoi intervalli positivi da quelli negativi, e quindi in questo caso a sapere _quando $f(x)$ cresce e quando decresce_.

Unendo lo studio del segno con l'annullamento della derivata otteniamo un grafico che ci consente di individuare a tutti gli effetti i punti di massimo o minimo relativo, che dovranno attenersi al seguente schema:
$$ - - - \ 0 \ + + + \implies \text{minimo locale}$$
$$ + + + \ 0 \ - - - \implies \text{massimo locale}$$

## Accorgimenti
> La condizione precedente è solo _sufficiente_ per garantire un minimo o massimo locale: _non necessaria_.

Questi due passaggi infatti, per particolari funzioni _non sono un criterio certo di identificazione di tutti i massimi e minimi relativi_. Si pensi a
$$f(x) = \begin{cases} x^{2} \cdot \sin^{2}\left(\frac{1}{x}\right) & x \neq 0 \\ 0 & x = 0 \end{cases}$$

dove $x = 0$ è un punto di minimo assoluto. Lo _studio del segno non consente semplicemente di identificarlo_, perché la funzione oscilla.

## Referenze