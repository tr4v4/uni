---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 22-09-2024 20:07:25
links:
  - "[[Lecture 16092024131302]]"
---
# Errore di arrotondamento
---
## Introduzione
> Per **errore di arrotondamento** di un numero rispetto a una codifica si intende un qualche tipo di _falsa rappresentazione_ di tale numero dovuto a limiti matematici della codifica.

### Esempio
In Python l'espressione `4.9 - 4.845 == 0.055` restituisce `False`. Questo avviene perché sia `4.9` che `4.845` _in [[Conversione binario-decimale|binario]] sono periodici_, perciò nella [[Codifica floating-point|codifica floating-point]] di Python (IEEE754) devono entrambi subire un **arrotondamento**, con conseguente perdita d'informazione e risultato scorretto.

Di fatto, in qualunque [[Linguaggio di programmazione|linguaggio di programmazione]], mai bisognerebbe confrontare i numeri con l'operatore di uguaglianza:
```cpp
// Da non fare
if (a == b) {
	// ...
}
```

Ma piuttosto definirsi un valore di tolleranza `tol` (del tipo $10^{-10}$, calcolato in base alla definizione della codifica) e scrivere:
```cpp
// Da fare
if (|a-b| < tol) {
	// ...
}
```

## Rappresentazione matematica
Più formalmente, definiamo due tipi di errori di arrotondamento:
- _errore assoluto di arrotondamento_;
- _errore relativo di arrotondamento_.

<u>Nota bene</u>: è bene ricordare le specifica di una codifica floating-point, $\mathbb{F} (\beta, t, +L, u)$.

### Errore assoluto di arrotondamento
$$|fl(x) - x| < \beta^{1-t}$$
dove:
- $fl(x)$ è la rappresentazione di $x$ nella codifica floating-point specificata;
- $\beta$ è la base della codifica floating-point;
- $t$ sono i bit della mantissa.

Si traduce in, affinché $fl(x)$ e $x$ possano essere considerati la stessa cosa, la loro distanza dev'essere inferiore al **gap** della codifica, ossia alla distanza minima tra un numero della codifica e l'altro (il più grande errore possibile).

### Errore relativo di arrotondamento
$$\frac{|fl(x)-x|}{|x|} < \frac{1}{2}\beta^{1-t}$$
dove $\frac{1}{2}\beta^{1-t}$ è spesso indicato come $\text{esp}$ e detta _precisione macchina_, ossia il più piccolo numero macchina ($\in \mathbb{F}$) positivo tale che $fl(1 + \text{esp}) > 1$.

## Referenze