---
tags:
  - category/homework
  - status/finished
  - topic/calcolo-numerico
date: 31-10-2024 11:01:23
---
# Calcolo numerico - HW. 1
---
## Esercizi
### Zeri di funzione
#### Introduzione
L'obiettivo dell'esercitazione è di mostrare empiricamente le proprietà degli [[Algoritmi per il calcolo delle radici di una funzione|algoritmi per il calcolo delle radici di una funzione]] studiati. In particolare, definita una funzione $f(x)$ e un intervallo $[a, b]$, useremo l'[[Algoritmo di bisezione|algoritmo di bisezione]], il [[Algoritmo dell'iterazione di punto fisso|metodo delle iterazioni di punto fisso]] e l'[[Algoritmo di Newton|algoritmo di Newton]], per calcolare la soluzione $x^{*} \in [a, b]$ tale che $f(x^{*}) = 0$.

Sarà necessario dimostrare inizialmente l'_esistenza_ e _unicità_ della soluzione $x^{*}$ nell'intervallo $[a, b]$. Quindi per ogni algoritmo si andrà ad analizzare il rapporto tra _accuratezza_ e _numero di iterazioni effettuate_, e si osserveranno i valori degli _errori assoluti_ $|x_{k} - x^{*}|$ ad ogni iterazione $k$, con l'intenzione di verificare le rispettive [[Velocità di convergenza|velocità di convergenza]].

<u>Nota bene</u>: trattandosi di un [[Problema test|problema test]] già siamo a conoscenza dell'esistenza, unicità e valore effettivo di $x^{*}$.

#### Sviluppo
La funzione in esame è
$$f(x) = e^{x} - x^{2}$$
di cui conosciamo la soluzione
$$x^{*} = -0.7034674$$

Ci viene suggerito di analizzare $f$ nell'intervallo $[-1, 1]$. Verifichiamo quindi, usando il [[Teorema degli zeri|teorema degli zeri]], l'esistenza di un punto $x^{*} \in [-1, 1] : f(x^{*}) = 0$. Ci basta dimostrare che $f$ sia [[Funzioni continue|continua]], e che se $[a, b] = [-1, 1]$ allora $f(a) \cdot f(b) < 0$. La continuità di $f$ deriva dal fatto che è _composizione di due funzioni continue_, quali l'_esponenziale_ e un _polinomio_. La seconda ipotesi si verifica eseguendo i conti
$$f(a) \cdot f(b) = f(-1) \cdot f(1) = \left(\frac{1}{e} - 1\right) \cdot (e - 1)$$
e notando che $\left(\frac{1}{e} - 1\right) < 0$ e $(e-1) > 0$, per cui il prodotto sarà negativo.

##### Grafico
Per cui una soluzione esiste nell'intervallo. Per essere certi che si tratti proprio di $x^{*} = -0.7034674$, disegniamo il grafico di $f$ e _plottiamo_ il punto $(x^{*}, f(x^{*}))$.

Usiamo [[Python]] e le librerie `numpy` e `matplotlib`:
```python
import numpy as np
import matplotlib.pyplot as plt

def f(x: np.ndarray) -> np.ndarray:
	return np.exp(x) - x**2

x = np.linspace(-1, 1, 50)
y = f(x)
r = -0.7034674

plt.plot(x, y, 'b')
plt.plot(r, f(r), 'ro')
plt.legend([r"$f(x)$", "radice"])
plt.grid()
plt.show()
```
che produce come risultato
![[calcolo-hw-1-grafico.png]]

In effetti il punto sembra proprio coincidere con lo 0 di $f$. Tuttavia se stampiamo il suo valore con `print(f(r))` otteniamo `4.278746923436216e-08` e non `0`. Questa differenza minimale è sopportabile, e anzi potrà esserci utile nelle prossime fasi. Di fatto rappresenta un _valore di tolleranza_ sfruttabile a nostro favore come _criterio di arresto_ per gli [[Algoritmo iterativo|algoritmi iterativi]]: se la soluzione considerata effettiva ha un errore assoluto da quella reale nell'ordine di $10^{-8}$, siamo autorizzati a non spingerci oltre nel calcolo algoritmico.

##### Bisezione
Procediamo con lo sviluppo dell'algoritmo di bisezione, ricordando che non si tratta di un vero e proprio algoritmo iterativo. Come unico criterio di arresto, infatti, abbiamo il numero di iterazioni `n`.

L'algoritmo è il seguente:
```python
def bisection(f, a: float, b: float, n: int) -> float:
	c = None
	for _ in range(n):
		c = (a+b) / 2
		if f(a) * f(c) < 0:
			b = c
		else:
			a = c
	return c
```
dove `f` nei parametri è la funzione in esame.

Non resta che eseguire l'algoritmo sull'intervallo $[-1, 1]$ e su un numero di iterazioni `n` a scelta:
```python
r = -0.7034674
for n in range(1, 200, 10):
	x = bisection(f, -1, 1, n)
	print(f"{n}° iter.: {x}, err. ass.: {np.abs(x - r)}")

# Output:
"""
1° iter.: 0.0	 err. ass.: 0.7034674
11° iter.: -0.7041015625	 err. ass.: 0.000634162500000035
21° iter.: -0.7034673690795898	 err. ass.: 3.092041012120461e-08
31° iter.: -0.7034674221649766	 err. ass.: 2.2164976631877664e-08
41° iter.: -0.7034674224987612	 err. ass.: 2.249876118742833e-08
51° iter.: -0.7034674224983641	 err. ass.: 2.2498364171674723e-08
61° iter.: -0.7034674224983632	 err. ass.: 2.2498363283496303e-08
71° iter.: -0.7034674224983632	 err. ass.: 2.2498363283496303e-08
81° iter.: -0.7034674224983632	 err. ass.: 2.2498363283496303e-08
91° iter.: -0.7034674224983632	 err. ass.: 2.2498363283496303e-08
101° iter.: -0.7034674224983632	 err. ass.: 2.2498363283496303e-08
111° iter.: -0.7034674224983632	 err. ass.: 2.2498363283496303e-08
121° iter.: -0.7034674224983632	 err. ass.: 2.2498363283496303e-08
131° iter.: -0.7034674224983632	 err. ass.: 2.2498363283496303e-08
141° iter.: -0.7034674224983632	 err. ass.: 2.2498363283496303e-08
151° iter.: -0.7034674224983632	 err. ass.: 2.2498363283496303e-08
161° iter.: -0.7034674224983632	 err. ass.: 2.2498363283496303e-08
171° iter.: -0.7034674224983632	 err. ass.: 2.2498363283496303e-08
181° iter.: -0.7034674224983632	 err. ass.: 2.2498363283496303e-08
191° iter.: -0.7034674224983632	 err. ass.: 2.2498363283496303e-08
"""
```

Ci sono un paio di osservazioni da fare.
Anzitutto ho considerato come _errore assoluto_ $|x - x^{*}|$, dove $x^{*}$ è il valore di riferimento $-0.7034674$ che sappiamo non essere "perfetto". Infatti è possibile vedere un _incremento dell'errore dalla 31° alla 41° iterazione_, causato dall'imprecisione della soluzione $x^{*}$. Per questo a volte può essere più conveniente usare $f(x)$ come valore dell'errore. Ma assumiamo che $x^{*}$ sia la soluzione esatta.
E' da notare come dalla 61° iterazione in poi l'algoritmo si fissi sulla soluzione $-0.7034674224983632$. Non vengono aggiunte più cifre decimali, né modificate quelle calcolate. Questo è causato dai _limiti dei calcolatori_ (memoria finita) e dalla _[[Codifica floating-point|codifica floating-point]]_ adottata. In particolare Python usa lo standard _IEEE754_, una codifica floating point che prevede una _precisione macchina_ $\text{eps}$ pari circa a $10^{-16}$. Significa che $\text{eps}$ è il numero più piccolo che sommato a $1$ produce un numero $> 1$ appartenente alla codifica. Il numero $-0.7034674224983632$ ha esattamente 16 cifre dopo lo 0, quindi qualunque modifica calcolata dall'algoritmo dell'ordine inferiore a $10^{-16}$ non viene presa in considerazione.

Detto questo possiamo considerare la 31° iterazione come quella che produce l'errore minimo rispetto a $x^{*}$, e la 61° iterazione come quella che produce l'errore minimo rispetto a $f(x)$.
```python
x = bisection(f, -1, 1, 61)
print(f(x))

# Output:
# 5.4012350148013866e-14
```

Modifichiamo l'algoritmo in modo tale da tenere conto per ogni iterazione dell'errore assoluto $|x_{k} - x^{*}|$:
```python
def bisection(f, a: float, b: float, n: int, r: float) -> float:
	c = None
	err = []
	for _ in range(n):
		c = (a+b) / 2
		if f(a) * f(c) < 0:
			b = c
		else:
			a = c
		err.append(np.abs(c - r))
	return c, err

n = 65
r = -0.7034674
x, err = bisection(f, -1, 1, n, r)

plt.plot(range(1, n+1), err, 'r')
plt.grid()
plt.show()
```
che produce
![[calcolo-hw-1-err-1.png]]

<u>Nota bene</u>: il picco nelle prime 10 iterazioni è causato dalla definizione stessa dell'algoritmo. Significa che un estremo $a$ o $b$ ha assunto un valore di $c$ molto vicino alla soluzione, per cui il $c$ calcolato all'iterazione successiva si troverà necessariamente più distante $x^{*}$. Questi picchi, hanno un _upperbound_. Infatti dalla teoria sappiamo che
$$|c - x^{*}| < \frac{b-a}{2}$$
e possiamo facilmente dimostrarlo modificando di poco l'algoritmo e plottando $\frac{b-a}{2}$ per ogni iterazione (ometto il codice). Si ottiene
![[calcolo-hw-1-err-2.png]]
dove la linea tratteggiata blu è il grafico di $\frac{b - a}{2}$ per ogni iterazione.

Questa linea, di fatto, rappresenta il **fattore di contrazione** $C = \frac{1}{2}$, caratteristico dell'algoritmo di bisezione. Ci dice che _nel caso peggiore_ (quando uno degli estremi iniziali è molto vicino alla soluzione), _l'errore assoluto iniziale verrà dimezzato ad ogni iterazione_.
Se scegliamo nel nostro caso l'estremo sinistro `a = r - 1e-7` (un valore prossimo a $x^{*}$), otteniamo infatti il grafico
![[calcolo-hw-1-err-3.png]]

##### Punto fisso
Proseguiamo con l'implementazione del metodo delle iterazioni del punto fisso. Ci vengono fornite due $g$ diverse della forma $g(x) = x - \omega(x)f(x)$ (con $0 < \omega(x) < +\infty \ \ \forall x$) da utilizzare per il calcolo della successione $x_{k} = g(x_{k-1})$ tale che $x_{k} \longrightarrow_{k \to +\infty} p$, $g(p) = p$ e $g(p) = p \iff f(p) = 0$. Dalla teoria sappiamo che _per verificare queste proprietà ci è sufficiente mostrare che $g$ è una [[Mappa|mappa]] [[Contrazione|contrattiva]]_. Quindi, prima di procedere con l'esecuzione dell'algoritmo, dimostriamo che
$$g_{1}(x) = x - f(x)e^{\frac{x}{2}} \ \ \ \ \ g_{2}(x) = x - f(x)e^{-\frac{x}{2}}$$
siano contrazioni.

###### Contrazioni
Per fare ciò dobbiamo verificare intanto che siano mappe, ovvero che per entrambe le $g$ esista un intervallo $[a, b]$, contenente $x^{*}$, tale che
$$g([a, b]) \in [a, b]$$

Per farlo velocemente possiamo plottare entrambi i grafici per un intervallo iniziale di $[-1, 1]$, facendo attenzione a mantenere le proporzioni giuste tra ascisse e ordinate (con `plt.axis('scaled')`):
```python
def g_1(x: np.ndarray) -> np.ndarray:
	return x - f(x)*np.exp(x/2)

def g_2(x: np.ndarray) -> np.ndarray:
	return x - f(x)*np.exp(-x/2)

r = -0.7034674
x = np.linspace(-1, 1, 50)
y_1 = g_1(x)
y_2 = g_2(x)

plt.plot(x, y_1, 'r')
plt.plot(x, y_2, 'b')
plt.plot(r, g_1(r), 'go')
plt.legend([r"$g_{1}(x)$", r"$g_{2}(x)", "punto fisso"])
plt.grid()
plt.axis('scaled')
plt.show()
```
![[calcolo-hw-1-fixed-1.png]]

Possiamo notare che nell'intervallo $[-1, 1]$, né $g_{1}$ né $g_{2}$ sono mappe. Se restringiamo il dominio a $[-0.8, -0.6]$, invece, otteniamo
![[calcolo-hw-1-fixed-2.png]]

E' facile capire che _solo $g_{1}$ è una mappa nell'[[Intorno|intorno]] di $x^{*}$_, mentre $g_{2}$ non sarà una mappa contenente $x^{*}$ per nessun dominio possibile. Se cade questa ipotesi, **non possiamo applicare il teorema per il quale ogni mappa contrattiva ha esattamente un punto fisso nel dominio (e per il quale vale la successione $x_{k} \longrightarrow_{k \to +\infty} x^{*}$)**, nonostante sappiamo che $g_{2}$ ha $x^{*}$ come punto fisso (dalla sua definizione).

Quindi ci concentriamo solo su $g_{1}$. Dimostriamo che si tratta di una contrazione in $[-0.8, -0.6]$. Già possiamo esserne abbastanza sicuri dal grafico: nell'intervallo $[-0.8, -0.6]$, $g_{1}$ mappa in $[-0.75, -0.65] \subset [-0.8, -0.6]$. Formalmente, però, per mostrare che si tratta di una contrazione è necessario dimostrare
$$|g_{1}'(x)| < 1 \ \ \ \forall x \in [-0.8, -0.6]$$

Allora
$$g_{1}'(x) = 1 - f'(x)e^{\frac{x}{2}} + \frac{f(x)e^{\frac{x}{2}}}{2}$$
sapendo che $f(x) = e^{x} - x^{2}$,
$$g_{1}'(x) = 1 - (e^{x} - 2x)e^{\frac{x}{2}} + \frac{1}{2}(e^{x}-x^{2})e^{\frac{x}{2}} = 1 + e^{\frac{x}{2}}\left(\frac{1}{2}e^{x} - \frac{1}{2}x^{2} - e^{x} + 2x\right)$$
e quindi
$$g_{1}'(x) = 1 - e^{\frac{x}{2}}\left(\frac{1}{2}e^{x} + \frac{1}{2}x^{2} - 2x\right)$$
il quale è sempre $< 1$ dal momento che il secondo termine della sottrazione è sempre positivo $\forall x \in [-0.8, -0.6]$.

###### Algoritmo
Ora che siamo certi del fatto che $g_{1}$ sia una mappa contrattiva in $[-0.8, -0.6]$, possiamo applicare il metodo dell'iterazione di punto fisso. Trattandosi di un algoritmo iterativo, definiamo prima i criteri di arresto:
- _accuratezza_ --> `err_tol`, inizializzato di default a `1e-9`;
- _numero di iterazioni_ --> `max_iter`, inizializzato di default a `10`.

Quindi l'algoritmo è:
```python
def fixed_point(x_0: float, r: float, g, err_tol: float=1e-9, max_iter: int=10) -> float:
	i = 1
	err_estimate = np.abs(x_0 - r)
	while i <= max_iter and err_estimate > err_tol:
		x_0 = g(x_0)
		err_estimate = np.abs(x_0 - r)
		i += 1
	return x_0
```

Per analizzarne l'accuratezza e l'efficacia procediamo eseguendo l'algoritmo su punti di partenza `x_0`, tolleranze `err_tol` e numero di iterazioni `max_iter` differenti.

Modifichiamo intanto l'algoritmo in modo tale che restituisca rispettivamente la soluzione, il numero di iterazioni effettuate e l'[[Array|array]] di errori assoluti:
```python
def fixed_point(x_0: float, r: float, g, err_tol: float=1e-9, max_iter: int=10):
	i = 1
	err_estimate = np.zeros((max_iter,))
	err_estimate[i-1] = np.abs(x_0 - r)
	while i < max_iter and err_estimate[i-1] > err_tol:
		x_0 = g(x_0)
		i += 1
		err_estimate[i-1] = np.abs(x_0 - r)
	return x_0, i-1, err_estimate[:i]
```

Lo eseguiamo con i seguenti iperparametri:
```python
r = -0.7034674
x, iterazioni, errori = fixed_point(-0.8, r, g_1, err_tol=1e-6, max_iter=100)
print(f"Soluzione: {x}\nNumero di iterazioni: {iterazioni}\nErrori assoluti: {errori}")

# Output:
"""
Soluzione: -0.7034668106803403
Numero di iterazioni: 12
Errori assoluti: [9.65326000e-02 3.12780176e-02 1.07027660e-02 3.59992494e-03
 1.21808987e-03 4.11300857e-04 1.39013848e-04 4.69337605e-05
 1.58872237e-05 5.33744690e-06 1.83338795e-06 5.89319660e-07]
"""
```
e otteniamo che l'algoritmo ci mette 12 iterazioni per ottenere una soluzione distante da $x^{*}$ nell'ordine di $10^{-6}$. Se vogliamo mettere a confronto questo algoritmo con quello di bisezione, impostiamo come soglia di errore quella raggiunta da quest'ultimo dopo 61 iterazioni: `2.2498363283496303e-08`.
```python
# Output:
"""
Soluzione: -0.7034674145268017
Numero di iterazioni: 16
Errori assoluti: [9.65326000e-02 3.12780176e-02 1.07027660e-02 3.59992494e-03
 1.21808987e-03 4.11300857e-04 1.39013848e-04 4.69337605e-05
 1.58872237e-05 5.33744690e-06 1.83338795e-06 5.89319660e-07
 2.29204372e-07 4.73382991e-08 4.60930836e-08 1.45268018e-08]
"""
```

Dopo **sole 16 iterazioni il metodo dell'iterazione di punto fisso raggiunge una distanza da $x^{*}$ minore di quella raggiunta dal metodo della bisezione in 61 iterazioni**. Da che cosa dipende? Dal fattore di contrazione $C$. Infatti se nell'algoritmo di bisezione è fissato a massimo $\frac{1}{2}$, in quello dell'iterazione è una _maggiorazione di $g'$ nell'intervallo analizzato_.

Considerata $g_{1}'(x)$, è facile trovarne una maggiorazione in $[-0.8, -0.6]$. Infatti il massimo _valore assoluto_ raggiunto dalla funzione è in $-0.8$. Valutiamo il suo valore:
$$g_{1}'(-0.8) = 1 - e^{\frac{-0.8}{2}}\left(\frac{1}{2}e^{-0.8} + \frac{1}{2}(-0.8)^{2} - 2(-0.8)\right) = -0.4376 \ldots$$

Per cui il fattore di contrazione $C$ sarà
$$C > |g_{1}'(x)| \iff C > 0.4376 \ldots$$
che per quanto alto è comunque minore di $\frac{1}{2}$.

Per convincerci di ciò, plottiamo il grafico dell'errore assoluto del metodo del punto fisso
![[calcolo-hw-1-fixed-err-1.png]]
e poi con il seguente codice produciamo un grafico che mette in relazione l'andamento dei due errori:
```python
r = -0.7034674
n = 100

x_fix, iterazioni, errori_fix = fixed_point(-0.8, r, g_1, err_tol=2.2498363283496303e-08, max_iter=n)
x_bis, errori_bis = bisection(f, -1, 1, n, r)

plt.plot(range(1, iterazioni+1), errori_fix, 'r')
plt.plot(range(1, n+1), errori_bis, 'b')
plt.legend(["punto fisso", "bisezione"])
plt.grid()
plt.show()
```
![[calcolo-hw-1-fixed-err-2.png]]

Risulta qui più chiara l'influenza del fattore di contrazione $C$.

<u>Nota bene</u>: anche se modificassimo gli estremi $a, b$ dell'intervallo di partenza dell'algoritmo di bisezione otterremmo una convergenza più lenta di quella del punto fisso. Per esempio, se poniamo `a = -0.8` e `b = -0.6`, e diminuiamo il numero di iterazioni `n` a 16 (per una maggiore leggibilità) il grafico risultante è il seguente
![[calcolo-hw-1-fixed-err-3.png]]

Otterrei lo stesso risultato (_la linea rossa sotto la blu_) se modificassi il punto di partenza `x_0`. Questo perché la velocità di convergenza è propria di $g_{1}$.

Come abbiamo fatto per l'algoritmo di bisezione, determiniamo l'_upperbound_ della curva dell'errore assoluto relativo alle iterazioni. Se fissiamo $C = 0.44$, allora varrà la relazione
$$|E_{k+1}| \leq 0.44 \cdot |E_{k}|$$
che si traduce in
$$|x_{k+1} - x^{*}| \leq 0.44 \cdot |x_{k} - x^{*}|$$

Quindi l'errore assoluto all'iterazione successiva ($k+1$) sarà meno della metà ($0.44$) dell'errore assoluto all'iterazione precedente ($k$). Graficamente:
![[calcolo-hw-1-fixed-err-4.png]]

Se volessimo ottenere risultati più precisi, potremmo azzardare una diminuzione di `err_tol`. Questo comporta un utilizzo maggiore di iterazioni. Come già sperimentato e discusso con l'algoritmo di bisezione, _oltre a una certa soglia l'algoritmo non può andare_. In particolare, l'errore minimo raggiungibile è proprio `2.2498391705205734e-08`, raggiunto dopo 16 iterazioni.

Come ultima analisi dell'algoritmo esplicitiamo il suo funzionamento plottando la _spirale_ di punti _convergente_ a $x^{*}$ partendo da `x_0` (ometto il codice), e mostriamo che la spirale per $g_{2}$ _diverge_, in quanto non mappa contrattiva.
![[calcolo-hw-1-fixed-spirale-1.png]]
![[calcolo-hw-1-fixed-spirale-2.png]]

##### Newton
Per implementare l'algoritmo di Newton è necessario prima di tutto calcolare la derivata prima di $f$, e, definita $g$ come
$$g(x) = x - \frac{f(x)}{f'(x)}$$
bisogna verificare due cose:
1. _che per $x^{*}$ non si annulli $f'$_;
2. _che $g$ sia una mappa contrattiva per un certo intervallo contenente $x^{*}$_;

Calcoliamo allora $f'$ sapendo che $f(x) = e^{x} - x^{2}$:
$$f'(x) = e^{x} - 2x$$

Che $f'(x^{*}) \neq 0$ lo si prova valutando la derivata:
$$f'(-0.7034674) \approx 1.9 \neq 0$$

Per verificare che $g$ sia una mappa contrattiva la plottiamo nell'intervallo $[-0.8, -0.6]$:
![[calcolo-hw-1-newton-1.png]]

Quindi $g$ è una mappa tra $[-0.8, -0.6]$, e possiamo anche facilmente intuire che si tratti di una contrazione: $|g'(x)|$ non assume mai valori superiori o uguali a 1 nell'intervallo (ometto la verifica formale).

Possiamo allora implementare l'algoritmo vero e proprio, eseguirlo e analizzare la sua velocità di convergenza:
```python
def newton(f, df, x_0: float, r: float, err_tol: float=1e-9, max_iter: int=10):
	i = 1
	err_estimate = np.zeros((max_iter,))
	err_estimate[i-1] = np.abs(x_0 - r)
	while i < max_iter and err_estimate[i-1] > err_tol:
		dx = f(x_0)/df(x_0)
		x_0 -= dx
		i += 1
		err_estimate[i-1] = np.abs(x_0 - r)
	return x_0, i-1, err_estimate[:i]
```

che sull'invocazione seguente produce l'output
```python
r = -0.7034674
n = 100
x, iterazioni, err = newton(f, df, -0.8, r, 1e-6, n)
print(f"Soluzione: {x}\nNumero iterazioni: {iterazioni}\nErrori: {err}")

# Output:
"""
Soluzione: -0.7034674225075672
Numero iterazioni: 3
Errori: [9.65326000e-02 3.49188315e-03 4.83783160e-06 2.25075673e-08]
"""
```

In **sole 3 iterazioni ha raggiunto un errore nell'ordine di $10^{-8}$**. Se come `err_tol` impostiamo `2.2498391705205734e-08`, ossia il _valore minimo dell'errore raggiungibile con i due algoritmi precedenti_ (per limiti della codifica), otteniamo:
```python
# Output:
"""
Soluzione: -0.7034674224983917
Numero iterazioni: 4
Errori: [9.65326000e-02 3.49188315e-03 4.83783160e-06 2.25075673e-08
 2.24983917e-08]
"""
```

Ebbene, per raggiungere l'errore assoluto minimo ci sono volute:
- _61 iterazioni_ con l'algoritmo di bisezione;
- _16 iterazioni_ con il metodo dell'iterazione di punto fisso;
- _4 iterazioni_ con l'algoritmo di Newton.

Questo non dovrebbe stupirci: l'algoritmo di Newton, a differenza dei due precedenti, ha una **velocità di convergenza quadratica**.

Proviamo a plottare l'errore assoluto ad ogni iterazione:
```python
r = -0.7034674
n = 100
x, iterazioni, err = newton(f, df, -0.8, r, 2.2498391705205734e-08, n)

plt.plot(range(0, iterazioni+1), err, 'r')
plt.grid()
plt.show()
```
![[calcolo-hw-1-newton-2.png]]

<u>Nota bene</u>: parto dall'iterazione 0 perché considero anche il primo errore assoluto $|x_{0} - x^{*}|$.

E' doveroso a questo punto mettere a confronto tutti gli errori assoluti degli algoritmi, in un unico grafico.
![[calcolo-hw-1-newton-3.png]]

Come già fatto in precedenza, possiamo inizializzare il range $[a, b]$ dell'algoritmo di bisezione a $[-0.8, -0.6]$ (piuttosto che a $[-1, 1]$), ma il risultato è medesimo:
![[calcolo-hw-1-newton-4.png]]

Da quest'ultimo grafico, però, _si nota molto meglio la convergenza lineare della bisezione e del punto fisso_, matematicamente battuta da quella quadratica di Newton.

Infatti, una volta individuato il fattore di contrazione $C$ per l'algoritmo di Newton, possiamo usare la formula
$$|E_{k+1}| \leq C |E_{k}|$$
e plottare l'_upperbound_ di Newton.

<u>Attenzione</u>: bisogna **distinguere il fattore di contrazione $C$ usato nella formula precedente con il fattore $C$ per il quale è valida la formula $|E_{k+1}| \leq C |E_{k}|^{2}$**, che giustifica la convergenza quadratica di Newton. Infatti la prima $C$ equivale proprio al fattore di contrazione della mappa contrattiva $g$, ed è una conseguenza del fatto che il metodo di Newton è un'istanza di quello dell'iterazione di punto fisso; la seconda $C$, invece, è un altra costante univoca di $g$ ma derivante dalle [[Sviluppo in serie di Taylor|formule di Taylor]]. Se _la prima è una maggiorazione di $|g'(x)|$, la seconda si calcola come $- \frac{f''(x^{*})}{2f'(x^{*})}$_[^1]. Ovviamente si può passare dall'una all'altra, ma la "formula della convergenza quadratica" non è applicabile al metodo dell'iterazione di punto fisso "standard" (solo a Newton).

Per trovare $C$ (fattore di contrazione) è necessario calcolare $g'(x)$:
$$g'(x) = D\left[x - \frac{e^{x}-x^{2}}{e^{x}-2x}\right] = 1 - \frac{(e^{x}-2x)(e^{x}-2x) - (e^{x}-2)(e^{x}-x^{2})}{(e^{x}-2x)^{2}}$$
ovvero
$$g'(x) = 1 - 1 + \frac{(e^{x}-2)(e^{x}-x^{2})}{(e^{x}-2x)^{2}} = \frac{(e^{x}-2)(e^{x}-x^{2})}{(e^{x}-2x)^{2}}$$

Nell'intervallo $[-0.8, -0.6]$, questa funzione si comporta nel seguente modo:
![[calcolo-hw-1-newton-5.png]]

Per cui una maggiorazione di $|g'(x)|$ potrebbe essere $0.1$. Fissiamo allora $C = 0.1$ (_estremamente basso_), e plottiamo il grafico dell'errore assoluto ad ogni iterazione insieme a quello del suo upperbound, usando la formula
$$|x_{k+1} - x^{*}| \leq 0.1 \cdot |x_{k} - x^{*}|$$
![[calcolo-hw-1-newton-6.png]]

Possiamo per completezza calcolare anche la $C$ per cui vale
$$|E_{k+1}| \leq C |E_{k}|^{2}$$
In questo caso
$$C = - \frac{f''(x^{*})}{2f'(x^{*})} \approx 0.39$$[^1]

Se plottiamo il grafico otteniamo un secondo upperbound (più preciso e specifico):
![[calcolo-hw-1-newton-7.png]]

#### Conclusioni
Per concludere riassumiamo in una breve tabella il numero di iterazioni necessarie ad ogni algoritmo per raggiungere l'errore assoluto minimo, e in un grafico finale mostriamo l'andamento degli errori assoluti e i relativi upperbound.

| Algoritmo       | Iterazioni | Errore assoluto          |
| --------------- | ---------- | ------------------------ |
| **Bisezione**   | _61_       | `2.2498391705205734e-08` |
| **Punto fisso** | _16_       | `2.2498391705205734e-08` |
| **Newton**      | _4_        | `2.2498391705205734e-08` |

![[calcolo-hw-1-finale.png]]

### Sistemi lineari
#### Introduzione
Lo scopo dell'esercizio è di mostrare il problema dell'[[Errore inerente|errore inerente]] nell'ambito degli [[Algoritmi per la risoluzione di sistemi lineari|algoritmi per la risoluzione di sistemi lineari]]. In particolare si richiede di generare 2 problemi test $Ax = b$, di dimensione $n$ variabile, e per ognuno di questi di:
- calcolare il [[Numero di condizione|numero di condizione]] $k(A)$;
- risolvere il sistema lineare usando la [[Fattorizzazione LU|fattorizzazione LU]] o [[Fattorizzazione di Cholesky|Cholesky]];
- calcolare l'errore relativo rispetto alla soluzione esatta (ossia l'_errore inerente_ $\frac{\|\Delta x\|}{\|x\|}$), e al variare di $n$ fare un grafico dell'errore e del numero di condizione.

In particolare i problemi test sono:
- $A$ _matrice casuale_;
- $A$ _[[Matrice di Hilbert|matrice di Hilbert]]_ (nota per il suo alto numero di condizione).

#### Sviluppo
##### Matrice casuale
Per generare una matrice di numeri casuali $A$, usiamo la libreria `numpy` e in particolare la funzione `numpy.random.randn()`, che restituisce una matrice di una dimensione specificata (_shape_) di numeri randomici presi dalla _distribuzione normale "standard"_.

Genero $A \in M_{n}(\mathbb{R})$ (quadrata) con $n$ inizialmente uguale a 3:
```python
np.random.seed(42)
n = 3
A = np.random.randn(n, n)
print(A)

# Output:
"""
[[ 0.49671415 -0.1382643   0.64768854]
 [ 1.52302986 -0.23415337 -0.23413696]
 [ 1.57921282  0.76743473 -0.46947439]]
"""
```

<u>Nota bene</u>: imposto il `seed` della funzione random a una costante, per garantire continuità tra le singole esecuzioni.

Creo il problema test scegliendo come soluzione un vettore $x \in \mathbb{R}^{n}$ a scelta: $x = (1, 1, 1)$, per esempio. Quindi la colonna dei termini noti $b$ sarà $Ax$:
```python
x = np.ones((n,))
b = A @ x
print(b)

# Output:
# [1.00613839 1.05473952 1.87717316]
```

Generato il problema test, calcoliamo il numero di condizione $k(A)$. Lo facciamo sia usando la funzione `np.linalg.cond(A)` che usando la formula $k(A) = \|A\| \cdot \|A^{-1}\|$.
```python
cond_1 = np.linalg.cond(A)
cond_2 = np.linalg.norm(A, ord=2) * np.linalg.norm(np.linalg.inv(A), ord=2)
print(cond_1, cond_2)

# Output:
# 4.344807943204735 4.344807943204733
```

<u>Osservazione</u>: la funzione di _numpy_ `cond` usa la [[Norma matriciale|norma matriciale]] 2, ovvero $\|A\|_{2} = \sqrt{p(A^{T}A)}$, dove $p(M)$ è il [[Raggio spettrale|raggio spettrale]] (_massimo [[Autovalore|autovalore]] in modulo_).

A questo punto, dobbiamo risolvere il sistema lineare $Ax = b$. Per farlo usiamo una fattorizzazione tra le due disponibili: LU o Cholesky. Ricordiamo che la _fattorizzazione di Cholesky_ è un sottocaso di quella LU più efficiente che può essere _applicato solo su matrici [[Matrice simmetrica|simmetriche]] [[Forma quadratica#Segno|definite positive]]_. La matrice in analisi $A$ non è simmetrica, per cui possiamo fattorizzarla solo in $LU$.

Definiamo una funzione apposita per risolvere un sistema lineare usando la fattorizzazione LU:
```python
def solve_linear_system_lu(A: np.ndarray, b: np.ndarray) -> np.ndarray:
	P, L, U = sp.linalg.lu(A)
	y = np.linalg.solve(L, b @ P)
	x = np.linalg.solve(U, y)
	return x
```
che eseguiamo sull'input
```python
x_hat = solve_linear_system_lu(A, b)
print(x_hat)

# Output:
# [1. 1. 1.]
```

Il sistema è stato risolto correttamente. Se calcoliamo l'errore relativo
$$\frac{\|\hat{x} - x\|}{\|x\|}$$
otteniamo ovviamente $0$.
```python
relative_error = np.linalg.norm(x_hat - x) / np.linalg.norm(x)
print(relative_error)

# Output:
# 0.0
```

D'altronde il numero di condizione di $A$ è relativamente basso, sicuramente non $k(A) \gg 1$. Per cui in questo caso _$A$ è ben condizionata e il sistema $Ax = b$ ben posto_.

###### $n$ variabile
Proviamo ora ad aumentare $n$, per esempio $n = 10$. Rieseguiamo tutte le parti del codice, e otteniamo:
```python
# Output:
"""
A: [[ 1.06564386 -0.65463253 -0.60770793 -1.26314464  0.75211796 -1.8765348
  -1.17299205  0.62038318 -0.17606546 -1.07157877]
 [-0.43915246 -0.80370197  0.52772473  0.63063799 -0.99447353  0.99144561
  -1.29472444 -1.25136123  0.33227628 -0.27434977]
 [-0.64050855  1.11976932 -0.55327338 -1.499298    1.31399699 -0.07560542
  -0.98321234  0.87370289 -1.71748832 -0.03113409]
 [ 1.09083055  0.47347617  0.73883126  0.64043792 -0.04065221 -0.57557178
  -0.93790017 -0.57451473 -1.4111697   0.38255129]
 [-0.63372589  1.09384822  0.02283063 -0.20908499  0.96142658 -0.88194418
  -1.70330266 -1.93370015 -0.66215846 -1.00968   ]
 [-0.93977615 -0.30428352  1.74227428  0.23693487 -1.44335962  0.62295939
  -1.59352742  0.88005554  0.21520803 -1.65644839]
 [-0.60487401  0.13082905  0.12929008  0.28530858 -0.37983012  0.28870143
  -0.87613613 -0.08646795  0.49626277  1.97713501]
 [ 0.08685838 -0.99703087  0.86590514 -0.18062112  0.91400543  0.27049565
   0.75842211 -2.34948427 -1.00556017  0.79561309]
 [ 0.40773459  0.36026209  0.04625287 -0.53169646  0.10205865 -0.26880111
   0.1770047   0.15442951 -0.41001676  0.01436771]
 [ 2.68621853  1.11945457  1.63631915  0.04991572 -1.23792397 -0.13454062
   0.06889131 -0.76283884  0.43951572 -0.29602665]]
b: [-4.38451118 -2.57567879 -2.1930509  -0.2136814  -4.95549089 -2.239963
  1.36021872 -0.84139663  0.05159578  3.56898491]
Numero di condizione: 22.048807779320104

Soluzione calcolata: [1. 1. 1. 1. 1. 1. 1. 1. 1. 1.]
Soluzione reale: [1. 1. 1. 1. 1. 1. 1. 1. 1. 1.]
Errore relativo: 7.09153599073145e-16
"""
```
il che risulta sempre accettabile. In questo caso il numero di condizione è $\approx 22$, e l'errore relativo $\neq 0$ è causato dall'[[Errore di arrotondamento|errore di arrotondamento]] (e probabilmente anche [[Errore algoritmico|algoritmico]]) di `x_hat`, che non è esattamente $(1, \cdots, 1)$.

Vediamo a questo punto fino a che valore di $n$ possiamo spingere l'algoritmo nel trovare soluzioni accettabili. In particolare, generiamo problemi test per $n = 2, \cdots, 100$ e valutiamo errore relativo e numero di condizione plottando i loro valori in due grafici distinti:
```python
conds = []
errors = []
max_n = 100
for n in range(2, max_n):
	A = np.random.randn(n, n)
	x = np.ones((n,))
	b = A @ x
	cond = np.linalg.cond(A)
	x_hat = solve_linear_system_lu(A, b)
	relative_error = np.linalg.norm(x_hat - x) / np.linalg.norm(x)
	conds.append(cond)
	errors.append(relative_error)

plt.subplot(1, 2, 1)
plt.title(r"$k(A)$")
plt.plot(range(2, max_n), conds, 'b')
plt.subplot(1, 2, 2)
plt.title(r"$err_{rel}$")
plt.plot(range(2, max_n), errors, 'g')
plt.show()
```

Questo produce i seguenti grafici:
![[calcolo-hw-1-sistema-lineare-1.png]]

da cui possiamo produrre le seguenti considerazioni:
1. sia il numero di condizione $k(A)$ che l'errore relativo $err_{rel}$ non crescono regolarmente all'aumentare della dimensione $n$ della matrice $A$ --> in realtà _al crescere di $n$ si verificano con più frequenza e intensità dei picchi dei due valori_;
2. tali picchi sono, banalmente, correlati tra di loro, tale che se il numero di condizione è alto, l'errore relativo sarà alto --> ma _il grado di correlazione non è lineare_;

La prima osservazione si spiega con il fatto che, generando casualmente la matrice, **all'aumentare di $n$ si ha una maggiore probabilità di incorrere in matrici mal condizionate**, **non la certezza che questo accada**. La seconda osservazione, invece, è dovuta al fatto che **il numero di condizione non è una misura diretta dell'errore relativo**. Prendiamo in esame il caso $n = 40$ e $n = 60$:
```python
print(f"Numero di condizione per n = 40: {conds[38]}")
print(f"Errore relativo per n = 40: {errors[38]}")
print()
print(f"Numero di condizione per n = 60: {conds[58]}")
print(f"Errore relativo per n = 60: {errors[58]}")

# Output
"""
Numero di condizione per n = 40: 3234.4529002131003
Errore relativo per n = 40: 6.775357161865569e-14

Numero di condizione per n = 60: 1279.1532721416793
Errore relativo per n = 60: 1.236154767327777e-13
"""
```

Per $n = 40$ il numero di condizione è 3 volte tanto quello per $n = 60$, mentre l'errore relativo è di un intero ordine di grandezza inferiore ($6 \times 10^{-14} < 1 \times 10^{-13}$). Ma questo non si contrappone alla teoria: l'_errore inerente ha come upperbound il numero di condizione di $A$ moltiplicato per la somma tra l'errore relativo di $A$ e l'errore relativo di $b$_.
$$\frac{\|\Delta x\|}{\|x\|} \leq k(A)\left( \frac{\|\Delta A\|}{\|A\|} + \frac{\|\Delta b\|}{\|b\|} \right)$$

<u>Nota bene</u>: in questo caso i valori di $\frac{\|\Delta A\|}{\|A\|}$ e $\frac{\|\Delta b\|}{\|b\|}$, ossia gli errori di rappresentazione della matrice $A$ e del vettore $b$, non sono calcolabili. Infatti generiamo $A$ casualmente usando una funzione di numpy: _dalla funzione viene restituita già $A + \Delta A$_! Lo stesso si ripercuote su $b$, che è $Ax$ (con $x$ nota).

##### Matrice di Hilbert
Proviamo invece adesso a riproporre gli stessi passaggi con una matrice di Hilbert. Questa matrice è definita come
$$H_{i,j} = \frac{1}{i+j-1}$$
ed è _particolarmente nota per la rapida crescita del suo numero di condizione all'aumentare della dimensione $n$_.

Come per il caso precedente, generiamo la matrice di Hilbert $H$ di dimensione $n = 3$, usando la funzione `scipy.linalg.hilbert()`:
```python
n = 3
H = sp.linalg.hilbert(n)
print(H)

# Output
"""
[[1.         0.5        0.33333333]
 [0.5        0.33333333 0.25      ]
 [0.33333333 0.25       0.2       ]]
"""
```

Stampo il suo numero di condizione:
```python
cond = np.linalg.cond(H)
print(f"Condizione di H: {cond}")

# Output:
# Condizione di H: 524.0567775860644
```
una cifra molto alta, considerando che siamo sempre nel caso $n = 3$. Messa a confronto con la matrice casuale $A$ di dimensione $n = 3$, la _matrice di Hilbert ha un numero di condizione più di 100 volte superiore_.

Procedo con la generazione del problema test con $H$ e $x = (1, 1, 1)$:
```python
def solve_linear_system_chol(A: np.ndarray, b: np.ndarray) -> np.ndarray:
	L = np.linalg.cholesky(A)
	y = np.linalg.solve(L, b)
	x = np.linalg.solve(L.T, y)
	return x

x = np.ones((n,))
b = H @ x
x_hat = solve_linear_system_chol(H, b)
relative_error = np.linalg.norm(x_hat - x) / np.linalg.norm(x)

print(f"Soluzione esatta: {x}")
print(f"Soluzione calcolata: {x_hat}")
print(f"Errore relativo: {relative_error}")

# Output:
"""
Soluzione esatta: [1. 1. 1.]
Soluzione calcolata: [1. 1. 1.]
Errore relativo: 3.555025891006744e-15
"""
```

L'errore relativo è abbastanza basso, la soluzione non è influenzata dal numero di condizione di $H$.

<u>Nota bene</u>: in questo caso _posso usare la fattorizzazione di Cholesky, in quanto la matrice di Hilbert è simmetrica e definita positiva_.

###### $n$ variabile
Proviamo ora a far crescere $n$, da $2$ a $15$, e a plottare il numero di condizione e l'errore relativo:
```python
conds = []
errors = []
max_n = 15
for n in range(2, max_n+1):
	H = scipy.linalg.hilbert(n)
	x = np.ones((n,))
	b = H @ x
	cond = np.linalg.cond(H)
	# Se non è definita positiva, non posso usare la decomposizione di Cholesky
	if cond > 1e17:
		x_hat = solve_linear_system_lu(H, b)
	else:
		x_hat = solve_linear_system_chol(H, b)
	relative_error = np.linalg.norm(x_hat - x) / np.linalg.norm(x)
	conds.append(cond)
	errors.append(relative_error)

plt.subplot(1, 2, 1)
plt.title(r"$k(A)$")
plt.plot(range(2, max_n+1), conds, 'b')
plt.yscale('log')
plt.subplot(1, 2, 2)
plt.title(r"$err_{rel}$")
plt.plot(range(2, max_n+1), errors, 'g')
plt.yscale('log')
plt.show()
```

<u>Nota bene</u>: utilizzo una _scala logaritmica per entrambi i grafici_, in quanto il numero di condizione e l'errore relativo crescono esponenzialmente con $n$. Inoltre _utilizzo la fattorizzazione LU per matrici con numero di condizione superiore a $10^{17}$_, perché _per un tale livello di malcondizionamento avviene che la matrice di Hilbert stessa non è più definita positiva_ (teoricamente lo è sempre, ma in memoria no), e quindi non posso usare la decomposizione di Cholesky.

Il codice produce i seguenti grafici:
![[calcolo-hw-1-sistema-lineare-2.png]]

Si osserva la crescita esponenziale (che su scala logaritmica appare come lineare), sia del numero di condizione che dell'errore relativo. Questo conferma che la _matrice di Hilbert, per definizione, è mal condizionata_.

E' interessante notare _anche in questo caso come la crescita regolare del numero di condizione non si rifletta in un aumento regolare dell'errore relativo_. Questo perché, come già discusso in precedenza, il numero di condizione non è una misura diretta dell'errore relativo. A differenza del caso precedente, però, **ci è possibile determinare una funzione di upperbound per l'errore relativo**.

Infatti la matrice di Hilbert è deterministica, e conoscendo la codifica floating-point di Python (_standard IEEE754_) _possiamo calcolare per ogni cella di $H$ l'errore assoluto di arrotondamento_, e quindi l'errore relativo di $H$ e conseguentemente di $b$. Questo ci consente di determinare l'errore inerente massimo.

Farlo "manualmente" richiederebbe uno sforzo notevole. Tuttavia, Python offre la libreria `fractions` che include la classe `Fraction`, con la quale possiamo rappresentare [[Numeri razionali|numeri razionali]], e quindi evitare errori di arrotondamento: possiamo avere $A$ "perfetta"! Definiamo allora una funzione `hilbert_exact` che restituisce la matrice di Hilbert esatta:
```python
from fractions import Fraction

def hilbert_exact(n):
	return np.array([[Fraction(1, i + j - 1) for j in range(1, n + 1)] for i in range(1, n + 1)], dtype=Fraction)
```

A questo punto, possiamo definire per ogni matrice di Hilbert $H_{n}$ una sua versione "esatta" e una sua versione codificata in floating-point, così da poter calcolare $\Delta H_{n}$. Allo stesso modo, possiamo calcolare una versione "esatta" (e quindi frazionaria) di $b_{n}$ e quindi, con la sua versione codificata in floating-point, anche $\Delta b_{n}$.
```python
H_exact = hilbert_exact(n)
H_float = np.array(H_exact, dtype=np.float64)
x = np.ones((n,), dtype=np.float64)
b_exact = np.array([sum(H_exact[i, j] * Fraction(x[j]) for j in range(n)) for i in range(n)], dtype=Fraction)
b_float = H_float @ x

delta_H = np.array([[H_exact[i, j] - Fraction(H_float[i, j]) for j in range(n)] for i in range(n)], dtype=Fraction)
delta_b = np.array([b_exact[i] - Fraction(b_float[i]) for i in range(n)], dtype=Fraction)
```

Bisogna osservare alcune cose:
- la codifica floating-point di riferimento per `H_float` e `b_float` è `np.float64`, che è molto simile a quella nativa di Python[^2];
- `b_exact` è calcolata con un prodotto righe per colonne "esatto", e non usando `H_exact @ x` --> solo in questo modo si garantisce che `b_exact` sia in forma frazionaria;
- `delta_H` e `delta_b` sono anch'esse in forma frazionaria, per poter mantenere un certo grado di precisione, e sono calcolate attraverso il seguente strategemma: _sottraggo al valore frazionario di $H$ "esatta" la conversione in frazione del valore in floating-point di $H$ "inesatta"_, perché **è solo in questo modo che catturo l'errore di arrotondamento**.

A questo punto, non ci resta che calcolare l'errore inerente massimo, che è dato da $k(H) \cdot \left( \frac{\|\Delta H\|}{\|H\|} + \frac{\|\Delta b\|}{\|b\|} \right)$:
```python
upperbound.append(cond * (np.linalg.norm(delta_H, ord=1) / np.linalg.norm(H_exact, ord=1) + np.linalg.norm(delta_b, ord=1) / np.linalg.norm(b_exact, ord=1)))
```

<u>Nota bene</u>: _utilizzo la norma 1_ (sapendo che qualunque norma va bene) perché è, sia nei vettori $\Delta H$ e $\Delta b$ che nelle matrici $H$ e $b$, la somma tutti i valori assoluti degli elementi, operazione definita per oggetti `Fraction`.

Quindi, insieme al grafico precedente, plottiamo l'_upperbound_ dell'errore inerente:
```python
plt.subplot(1, 2, 1)
plt.title(r"$k(A)$")
plt.plot(range(2, max_n+1), conds, 'b')
plt.yscale('log')
plt.subplot(1, 2, 2)
plt.title(r"$err_{rel}$")
plt.plot(range(2, max_n+1), errors, 'g')
plt.plot(range(2, max_n+1), upperbound, 'r--')
plt.yscale('log')
plt.show()
```
![[calcolo-hw-1-sistema-lineare-3.png]]

dove l'_upperbound_ è rappresentato dalla linea rossa tratteggiata.
Esattamente ciò che ci aspettavamo.

#### Conclusione
In conclusione, abbiamo mostrato come il problema dell'errore inerente si manifesti in maniera più evidente in matrici mal condizionate, come la matrice di Hilbert, rispetto a matrici ben condizionate. Conoscendo la codifica floating-point, infine, siamo stati in grado di calcolare un upperbound dell'errore inerente, verificando empiricamente la teoria.

### Minimi quadrati
#### Introduzione
In questo ultimo esercizio, si richiede di risolvere il [[Problema dei minimi quadrati|problema dei minimi quadrati]] ${\arg_{\min}}_{\alpha \in \mathbb{R}^{n}} {\|A\alpha - y\|_{2}}^{2}$ per una matrice $A \in M_{m \times n}(\mathbb{R})$ (generata randomicamente) con $m > n$ (fissati) e un vettore $y \in \mathbb{R}^{m}$. In particolare, una volta costruito un problema test della forma
$$y = A\alpha + v$$
dove $v$ è un vettore di numeri casuali con una varianza $\sigma \in [0.01, 0.1]$, si richiede di risolvere il problema ai minimi quadrati mediante:
- _il sistema normale_ (con la fattorizzazione di Cholesky);
- _[[Fattorizzazione ai valori singolari|decomposizione ai valori singolari]]_.

Infine si richiede un confronto tra le due soluzioni calcolate, e la norma 2 del residuo $r = A\alpha - y$ per entrambi i casi.

<u>Nota bene</u>: il motivo per cui il problema test prevede l'aggiunta del vettore casuale $v$, è per _evitare di risolvere il problema triviale $A\alpha = y$_. In tal caso, il problema dei minimi quadrati si riduce nella soluzione di un sistema lineare, _cui residuo è nullo_. Quindi con $v$ andiamo a spostare il vettore $y$ così che non esista un $\alpha$ tale che $A\alpha = y$.

#### Sviluppo
##### Codice
Vogliamo intanto generare il problema test. Partiamo col definire le costanti $m, n: m > n$. Fissiamo $m = 7$ e $n = 5$, e generiamo la matrice $A$ usando la funzione `numpy.random.normal()` con una varianza $\sigma$ variabile per ora pari a $0.1$:
```python
import numpy as np

np.random.seed(42)
M = 7
N = 5
sigma = 0.1

A = np.random.normal(scale=sigma, size=(M, N))
print(A)

"""
Output:
[[ 0.04967142 -0.01382643  0.06476885  0.15230299 -0.02341534]
 [-0.0234137   0.15792128  0.07674347 -0.04694744  0.054256  ]
 [-0.04634177 -0.04657298  0.02419623 -0.19132802 -0.17249178]
 [-0.05622875 -0.10128311  0.03142473 -0.09080241 -0.14123037]
 [ 0.14656488 -0.02257763  0.00675282 -0.14247482 -0.05443827]
 [ 0.01109226 -0.11509936  0.0375698  -0.06006387 -0.02916937]
 [-0.06017066  0.18522782 -0.00134972 -0.10577109  0.08225449]]
"""
```

Ora creiamo il problema test considerando $\alpha = (1, \cdots, 1)$ e $v$ un vettore di numeri casuali:
```python
A = np.random.normal(scale=sigma, size=(M, N))
alpha_true = np.ones((N,))
v = np.random.normal(scale=sigma, size=(M,))
y = A @ alpha_true + v

print("A: ", A)
print("alpha_true: ", alpha_true)
print("v: ", v)
print("y: ", y)

"""
Output:
A:  [[ 0.04967142 -0.01382643  0.06476885  0.15230299 -0.02341534]
 [-0.0234137   0.15792128  0.07674347 -0.04694744  0.054256  ]
 [-0.04634177 -0.04657298  0.02419623 -0.19132802 -0.17249178]
 [-0.05622875 -0.10128311  0.03142473 -0.09080241 -0.14123037]
 [ 0.14656488 -0.02257763  0.00675282 -0.14247482 -0.05443827]
 [ 0.01109226 -0.11509936  0.0375698  -0.06006387 -0.02916937]
 [-0.06017066  0.18522782 -0.00134972 -0.10577109  0.08225449]]
alpha_true:  [1. 1. 1. 1. 1.]
v:  [-0.12208436  0.02088636 -0.19596701 -0.1328186   0.01968612  0.07384666
  0.01713683]
y:  [ 0.10741712  0.23944598 -0.62850534 -0.49093851 -0.0464869  -0.08182388
  0.11732766]
"""
```

Ora che abbiamo gli ingredienti, possiamo cominciare a risolvere il problema dei minimi quadrati
$${\arg_{\min}}_{\alpha \in \mathbb{R}^{n}} {\|A\alpha - y\|_{2}}^{2}$$
usando la fattorizzazione di Cholesky (per il sistema normale) e la decomposizione ai valori singolari.

##### Sistema normale
Per poter passare alle equazioni normali, ci si deve assicurare che la matrice $A$ abbia rango massimo, ossia che $rk(A) = n$. Per farlo ci basta usare la funzione `numpy.linalg.matrix_rank()`:
```python
rk_A = np.linalg.matrix_rank(A)
print(rk_A == N)

# Output: True
```

Verificato questo, non ci resta che risolvere il sistema normale
$$A^{T}A \alpha = A^{T}y$$
risolvibile con la fattorizzazione di Cholesky in quanto $A^{T}A$ è simmetrica e definita positiva ($rk(A) = n$). Quindi ricicliamo la funzione `solve_linear_system_chol()` e la invochiamo passando come parametri $A^{T}A$ e $A^{T}y$:
```python
def solve_linear_system_chol(A: np.ndarray, b: np.ndarray) -> np.ndarray:
	L = np.linalg.cholesky(A)
	y = np.linalg.solve(L, b)
	x = np.linalg.solve(L.T, y)
	return x

alpha_chol = solve_linear_system_chol(A.T@A, A.T@y)
print(alpha_chol)

# Output: [1.16201705 0.10757469 1.14261069 0.43674174 2.94686945]
```

Come interpretiamo il risultato? Il vettore `alpha_chol` ottenuto è la soluzione che minimizza ${\|A\alpha - y\|_{2}}^{2}$, ossia ${\|r\|_{2}}^{2}$. Questo **residuo**, ricordiamo, **non può essere uguale a 0**, perché abbiamo aggiunto il vettore casuale $v$ a $y$, o meglio: è uguale a 0 $\iff$ $v = \underline{0}$.
Calcoliamo allora il residuo e la sua norma 2:
```python
r = A @ alpha_chol - y
norm_r_sqrd = np.linalg.norm(r, ord=2) ** 2
print("Residuo: ", r)
print("Norma 2 al quadrato del residuo: ", norm_r_sqrd)

# Output:
"""
Residuo:  [ 0.02033525 -0.0225954   0.0054205  -0.00523418 -0.00056233  0.01306842
  0.02733522]
Norma 2 al quadrato del residuo:  0.0018991667528066494
"""
```

##### SVD
Passiamo ora alla decomposizione ai valori singolari. Sappiamo dalla teoria, infatti, che _la soluzione al problema dei minimi quadrati con la SVD è indipendente dal rango $k$ di $A$_ (può essere usata sia per $k \leq n$ che per $k = n$). Una volta fattorizzata $A$ in $U \Sigma V^{T}$, la formula per risolvere il problema dei minimi quadrati diventa
$$\alpha = \sum\limits_{i=1}^{k} \frac{u_{i}^{T}y}{\sigma_{i}}v_{i}$$

Definiamo quindi la funzione `solve_least_squared_svd()` nel seguente modo:
```python
def solve_least_squared_svd(A: np.ndarray, b: np.ndarray) -> np.ndarray:
	rk = np.linalg.matrix_rank(A)
	U, s, VT = np.linalg.svd(A)
	x = sum(((U[:, i].T @ b) / s[i]) * VT[i, :] for i in range(rk))
	return x
```
e la invochiamo passando come parametri $A$ e $y$:
```python
alpha_svd = solve_least_squared_svd(A, y)
print(alpha_svd)

# Output: [1.16201705 0.10757469 1.14261069 0.43674174 2.94686945]
```

Il _risultato è il medesimo della soluzione con la fattorizzazione di Cholesky_, come ci aspettavamo. Il residuo, di conseguenza, sarà lo stesso.

##### Confronto
I due risultati sono assolutamente equivalenti, sia in termini di soluzione $\alpha$ che, conseguentemente, di residuo. E' ovviamente giusto che sia così, tuttavia si possono fare delle considerazioni in merito alla scelta dell'algoritmo da utilizzare: il numero di condizionamento di $A$ è $\approx 5$, per cui il condizionamento della matrice del sistema normale $A^{T}A$ è $\approx 25$: il problema è ben posto, per cui Cholesky funziona bene. Siamo però a conoscenza del fatto che _la SVD, in casi di matrici mal condizionate, è più stabile e robusta rispetto alla fattorizzazione di Cholesky_.

E' interessante invece notare il ruolo che gioca la varianza $\sigma$ nel problema: _essa influenza direttamente il residuo_. Proviamo a far decrescere $\sigma$ fino a $0.01$ e a plottare il residuo in funzione di essa (risolvendo con le equazioni normali). Nel farlo adottiamo le seguenti regole:
- facciamo variare la varianza solo per $v$, e non per $A$, altrimenti si "annullerebbero" le modifiche;
- visto che $\sigma$ rappresenta l'"ampiezza" di $v$, avendo necessità di mantenere lo stesso $v$ per ogni $\sigma$, possiamo semplicemente moltiplicare $v$ per $\frac{\sigma_{new}}{\sigma_{old}}$, dove $\sigma_{old} = 0.1$.

```python
rs = []
n = 100
A = np.random.normal(scale=0.1, size=(M, N))
vv = np.random.normal(scale=0.1, size=(M,))
sigmas = np.linspace(0.1, 0.01, n)
for sigma in sigmas:
	alpha_true = np.ones((N,))
	v = vv*sigma/0.1
	y = A @ alpha_true + v
	
	alpha_chol = solve_linear_system_chol(A.T@A, A.T@y)
	r = A @ alpha_chol - y
	norm_r_sqrd = np.linalg.norm(r, ord=2) ** 2
	
	rs.append(norm_r_sqrd)

plt.plot(range(n), rs)
plt.grid()
plt.show()
```
![[calcolo-hw-1-minimi-quadrati.png]]

Il risultato è un grafico che mostra la discesa del residuo al diminuire della varianza $\sigma$, perfettamente in linea con ciò che ci aspettavamo.

#### Conclusione
In conclusione, abbiamo risolto il problema dei minimi quadrati con due differenti algoritmi, la fattorizzazione di Cholesky e la decomposizione ai valori singolari, ottenendo risultati equivalenti. Abbiamo inoltre verificato empiricamente come la varianza $\sigma$ influenzi il residuo del problema test.

## Referenze
[^1]: informazione presa da [qui](https://my.liuc.it/MatSup/2009/Y90000/N3.doc) e [qui](https://lemesurierb.people.charleston.edu/elementary-numerical-analysis-python/notebooks/newtons-method-convergence-rate.html)
[^2]: come si può leggere [qui](https://numpy.org/devdocs/user/basics.types.html#extended-precision)