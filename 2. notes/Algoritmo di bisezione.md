---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 28-09-2024 13:27:26
links:
  - "[[Lecture 23092024132935]]"
---
# Algoritmo di bisezione
---
## Introduzione
> L'**algoritmo di bisezione** è un [[Algoritmo|algoritmo]] per il [[Algoritmi per il calcolo delle radici di una funzione|calcolo delle radici di un'equazione]] (non lineare).

L'idea alla base di questo algoritmo è di _zoomare_ verso la radice modificando i valori iniziali dell'intervallo preso in considerazione $[a, b]$.

## Algoritmo
In particolare:
1. fisso $c = \frac{a+b}{2}$;
2. $f(a) \cdot f(c) < 0 \implies [a, b] = [a, c]$ (o più semplicemente $b = c$);
3. altrimenti $f(b) \cdot f(c) < 0 \implies [a, b] = [c, b]$ (o più semplicemente $a = c$);

Si _ripete l'algoritmo per un numero di iterazioni $n$_, e **il valore della radice approssimata è l'ultimo valore di $c$**.

Infatti, se $x$ è la radice in considerazione, alla fine si avrà:
$$|c-x| < \frac{b-a}{2}$$
ossia che la distanza di $c$ dalla radice effettiva è minore della distanza dell'intervallo finale $[a, b]$.

Se prendiamo in considerazione i valori iniziali di $[a, b]$, che chiamiamo $a_{0}$ e $b_{0}$, allora si avrà:
$$|c-x| = \frac{b_{0} - a_{0}}{2^{n}}$$

<u>Nota bene</u>: l'algoritmo presenta una grande somiglianza con la [[Teorema degli zeri#Dimostrazione|dimostrazione del teorema degli zeri]].

## Codice
Definiamo la funzione `f(x)`:
```python
def f(x):
	return # generic function of x
```

L'algoritmo allora è
```python
n = 10000
a = -1
b = 1
c = None
for _ in range(n):
	c = (a+b)/2
	if f(a) * f(c) < 0:
		b = c
	else:
		a = c
print(c)
```

## Referenze