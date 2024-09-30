---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 29-09-2024 16:16:00
links:
  - "[[Lecture 24092024092227]]"
---
# Algoritmo di Newton
---
## Introduzione
> L'**algoritmo di Newton** è una versione ottimizzata dell'[[Algoritmo dell'iterazione di punto fisso|algoritmo dell'iterazione di punto fisso]] per il [[Algoritmi per il calcolo delle radici di una funzione|calcolo delle radici di un'equazione]] (non lineare).

## Teoria
Questo algoritmo si basa sugli stessi principi matematici dell'iterazione di punto fisso: si cerca una $g$ relazionata ad $f$ tale che $g(x) = x \iff f(x) = 0$ e che sia una [[Mappa|mappa]] [[Contrazione|contrattiva]] per poter trovare il punto fisso attraverso una [[Successione numerica|successione numerica]].

L'idea che rende, tuttavia, questo algoritmo decisamente migliore del generico punto fisso, è quella di **cercare la $g$ che minimizzi il coefficiente di contrazione $C$**, dove
$$\forall x \in [a, b]. \ \ \ |g'(x)| \leq C < 1$$

Quindi, sapendo che $C$ è una maggiorazione di $g'(x)$ nell'intervallo $[a, b]$, **se imponiamo che nel punto fisso $p$ accada $g'(p) = 0$** (ossia che sia un [[Massimo e minimo relativo|massimo o un minimo relativo]]), **allora tutti i valori di $|g'(x)|$ attorno a $p$, quindi presumibilmente nell'intervallo $[a, b]$, saranno poco sopra lo 0**. Di conseguenza anche $C$, dovendo soddisfare $\forall x \in [a, b]. \ \ \ |g'(x)| \leq C < 1$, sarà poco sopra lo 0.

### Calcolo
Ma come facciamo a trovare una $g$ del genere? Trovando semplicemente una $\omega(x)$ apposita.

Se infatti imponiamo
$$g'(p) = 0$$
sapendo che
$$g(p) = p - \omega(p)f(p)$$
otteniamo
$$g'(p) = 1 - \omega'(p)f(p) - \omega(p)f'(p) = 0$$

Ora, considerato che per ipotesi $g(p) = p$, abbiamo $f(p) = 0$. Non rimane allora che
$$g'(p) = 1 - \omega(p)f'(p) = 0$$
e questo è soddisfatto solo se
$$\omega(p) = \frac{1}{f'(p)}$$

### Formula
Noi ovviamente non conosciamo $p$, ma non importa: ci basta imporre
$$\omega(x) = \frac{1}{f'(x)}$$
da cui otteniamo la **nota formula di Newton per il calcolo delle radici**:
$$g(x) = x - \frac{f(x)}{f'(x)}$$
che in termini di successione $x_{k}$ può essere interpretato come
$$x_{k} = x_{k-1} - \frac{f(x_{k-1})}{f'(x_{k-1})}$$

## Criteri di arresto
Trattandosi di un [[Algoritmo iterativo|algoritmo iterativo]], necessita dei **criteri di arresto**. In particolare utilizza:
- _accuratezza_ --> $\tau$ come valore di tolleranza tale che $|x_{k} - p| < \tau$;
- _tempo di calcolo_ --> $\text{MAXIT}$ come numero massimo di iterazioni tale che $k < \text{MAXT}$.

**E' necessario che nell'algoritmo siano previsti entrambi i criteri** perché se $\tau$, per esempio, fosse troppo piccolo, potrebbe non verificarsi mai la condizione di arresto sull'accuratezza: in tal caso entrerebbe in gioco il numero massimo di iterazioni $\text{MAXIT}$ per fermare l'algoritmo.

## Algoritmo
Definiamo $f(x)$ e $f'(x)$:
```python
def f(x):
	return # generic function

def df(x):
	return # derivative of f(x)
```

L'algoritmo è:
```python
def newton(f, df, x_0, error_tollerance, max_iterations=20):
	x_k = x_0
	error_estimate = MAX_INT
	k = 0
	while error_estimate > error_tollerance and k < max_iterations:
		dx = f(x_k)/df(x_k)
		x_k -= dx
		error_estimate = abs(dx)
		k += 1
	return (x_k, error_estimate, k)
```

<u>Nota bene</u>: la stima dell'errore `error_estimate` ad ogni iterazione, viene calcolata come $\left|\frac{f(x_{k})}{f'(x_{k})}\right|$. Tralasciando $f'(x_{k})$, che è poco rilevante, quello che realmente fa la differenza è $f(x_{k})$, perché man mano che $x_{k}$ si avvicina a $p$, avviene che $f(x_{k})$ si avvicina a 0. Per cui, il criterio di arresto sull'accuratezza, al posto di essere l'impossibile $|x_{k} - p| < \tau$, diventa semplicemente $|f(x_{k})| < \tau$ (dove $\tau$, nell'algoritmo è `error_tollerance`).

## Punti deboli
Questo algoritmo è velocissimo, ma presenta un problema non indifferente: **se infatti la radice di $f$ corrisponde esattamente alla radice di $f'$, l'algoritmo non funziona più**!

## Referenze