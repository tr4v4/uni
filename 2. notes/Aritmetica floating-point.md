---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 22-09-2024 20:43:59
links:
  - "[[Lecture 16092024131302]]"
  - "[[Lecture 23092024132935]]"
---
# Aritmetica floating-point
---
## Introduzione
L'idea è che ogni operazione tra due numeri appartenenti a una (stessa) [[Codifica floating-point|codifica floating-point]] deve restituire un numero sempre appartenente ad essa[^1]:
$$\forall \mathbb{F}. \forall x,y \in \mathbb{F}. \ \ \ x \odot y \in \mathbb{F}$$

Se si considera allora $\cdot: \mathbb{R} \times \mathbb{R} \to \mathbb{R}$ come la generica operazione aritmetica reale, e $\odot: \mathbb{F} \times \mathbb{F} \to \mathbb{F}$ come l'operazione floating-point, si ha che
$$x \odot y = fl(x \cdot y)$$
ovvero che l'operazione dell'aritmetica floating-point non è altro che l'_approssimazione_ in codifica ($fl()$) del risultato dell'operazione dell'aritmetica reale.

## Errori
Ogni operazione definita in tal modo provoca un [[Errore di arrotondamento|errore relativo di arrotondamento]] molto piccolo, più piccolo della precisione macchina:
$$\left|\frac{(x \odot y) - (x \cdot y)}{x \cdot y}\right| < \text{eps}$$
dove $\text{esp} = \frac{1}{2}\beta^{1-t}$.

## Esempi
### $\mathbb{F}(10, 2, -20, 20)$
Consideriamo la codifica $\mathbb{F}(10, 2, -20, 20)$, e due numeri
- $x = 2.15 \times 10^{12} = fl(x) \in \mathbb{F}$
- $y = 1.25 \times 10^{-5} = fl(y) \in \mathbb{F}$

Ora voglio calcolare $x-y$, ma per farlo devo prima uguagliare le mantisse allo stesso esponente, scegliendo quello più grande. Allora ho:
- $x = 2.15 \times 10^{12}$
- $y = 0.0000000000000000125 \times 10^{12}$

Faccio l'operazione, e ottengo
$$z = x-y = 2.1499999999999999999 \times 10^{12} \notin \mathbb{F}$$

Notiamo che $z \notin \mathbb{F}$ perché ha ben 16 cifre di mantissa, quando la codifica ne richiede solo 2. Il risultato che sarà salvato sul calcolatore sarà $fl(z)$, calcolato in uno dei 2 modi:
- **arrotondamento** --> $fl(z) = 2.15 \times 10^{12}$
- **troncamento** --> $fl(z) = 2.14 \times 10^{12}$

A prescindere dal metodo scelto, si verifica un errore di arrotondamento. Calcoliamo quello relativo, scegliendo come metodo di $fl(z)$ il troncamento:
$$\left| \frac{2.14 \times 10^{12} - 2.1499999999999999999 \times 10^{12}}{2.1499999999999999999 \times 10^{12}} \right| = \left| \frac{-0.0099999999999999999 \times 10^{12}}{2.1499999999999999999 \times 10^{12}} \right|$$

Il risultato è
$$0.00465116279$$
Facciamo la prova del 9, e dimostriamo quindi che questo è minore della _precisione macchina_. Infatti
$$\frac{1}{2}\beta^{1-t} = \frac{1}{2} \cdot 10^{1-2} = \frac{1}{2} \cdot 10^{-1} = \frac{1}{20} = 0.05$$

Si ha proprio:
$$0.00465116279 < 0.05$$

### $\mathbb{F}(10, 5, -8, 8)$
Ci calcoliamo questa volta sin da subito la precisione macchina:
$$\text{eps} = \frac{1}{2}\beta^{1-t} = \frac{1}{2} \cdot 10^{1-5} = \frac{1}{2} \cdot 10^{-4} = \frac{1}{20000}$$

Prendiamo due numeri:
- $x = 1 \times 10^{0} = fl(x)$
- $y = 2.345 \times 10^{-8} = fl(y)$

Notiamo un dettaglio importante: $y < \text{eps}$. Questo ha conseguenze importantissime. Infatti anche se $x$ e $y$ fanno parte di $\mathbb{F}$, per via della differenza sostanziale tra le loro caratteristiche ($0$ e $-8$), la somma $x+y$ subirà un errore abbastanza visibile.

Proviamolo:
$$z = x + y = fl(x) + fl(y) = 1 \times 10^{0} + 2.345 \times 10^{-8} = (1 + 0.00000002345) \times 10^{0}$$

Si avrà allora
$$z = 1.00000002345 \times 10^{0} \notin \mathbb{F}$$

che appunto non appartiene a $\mathbb{F}$ perché ha più di 5 cifre di mantissa: faccio il troncamento, e ottengo
$$fl(z) = 1.00000 \times 10^{0} \in \mathbb{F}$$

Per cui, in poche parole
$$1 + y = 1$$
proprio perché $y < \text{eps}$. Ricordiamo infatti che $\text{eps}$ è il più piccolo numero che sommato a $1$ fa un numero maggiore di $1$ appartenente a $\mathbb{F}$.

### Errore algoritmico
I limiti dell'aritmetica floating-point si rendono piuttosto evidenti quando si va incontro ad **[[Errore algoritmico|errori algoritmici]]**, ossia errori provocati dalla propagazione degli arrotondamenti/troncamenti delle operazioni floating-point.

Prendiamo per esempio un algoritmo che calcola il [[Numero di Nepero|numero di Nepero]] $e$ usando il famoso [[Limite|limite]]
$$e = \lim_{n \to +\infty} \left(1 + \frac{1}{n}\right)^{n}$$

Fondamentalmente, l'errore diminuisce, finché $n$ non diventa troppo grande. In particolare, nel momento in cui $n$ raggiunge $10^{16}$, all'interno della parentesi viene svolto il calcolo
$$1 + 10^{-16}$$

Nella codifica floating-point standard di Python IEEE754, si ha proprio che
$$\text{eps} \approx 10^{-16}$$
perciò, di conseguenza, avviene che
$$1 + 10^{-16} = 1$$

rompendo completamente il calcolo dell'algoritmo (che darà come risultato da quel momento in poi $1$).

## Referenze
[^1]: [[Algebra astratta|proprietà algebrica]] di chiusura!