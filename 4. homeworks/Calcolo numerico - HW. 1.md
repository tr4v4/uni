---
tags:
  - category/homework
  - status/ongoing
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
E' da notare come dalla 61° iterazione in poi l'algoritmo si fissi sulla soluzione $-0.7034674224983632$. Non vengono aggiunte più cifre decimali, né modificate quelle calcolate. Questo è causato dai _limiti dei calcolatori_ (memoria finita) e dalla _[[Codifica floating-point|codifica floating-point]]_ adottata. In particolare Python usa lo standard _IEEE754_, una codifica floating point che prevede una _precisione macchina_ $\beta$ pari circa a $10^{-16}$. Significa che $\beta$ è il numero più piccolo che sommato a $1$ produce un numero $> 1$ appartenente alla codifica. Il numero $-0.7034674224983632$ ha esattamente 16 cifre dopo lo 0, quindi qualunque modifica calcolata dall'algoritmo dell'ordine inferiore a $10^{-16}$ non viene presa in considerazione.

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

Per farlo velocemente possiamo plottare entrambi i grafici per un intervallo iniziale di $[-1, 1]$, facendo attenzione a mantenere le proporzioni giuste tra ascisse e ordinate (con `plt.axis('scaled'))`:
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

E' facile capire che _solo $g_{1}$ è una mappa nell'[[Intorno|intorno]] di $x^{*}$_, mentre $g_{2}$ non sarà una mappa contenente $x^{*}$ per nessun dominio possibile. Se cade questa ipotesi, **non possiamo applicare il teorema per il quale ogni mappa contrattiva ha esattamente un punto fisso nel dominio**, nonostante sappiamo che $g_{2}$ ha $x^{*}$ come punto fisso (dalla sua definizione).

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
$$g_{1}(-0.8) = 1 - e^{\frac{-0.8}{2}}\left(\frac{1}{2}e^{-0.8} + \frac{1}{2}(-0.8)^{2} - 2(-0.8)\right) = -0.4376 \ldots$$

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

Risulta qui più immediato l'influenza del fattore di contrazione $C$.

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
Per implementare l'algoritmo di Newton è necessario prima di tutto calcolare la derivata prima di $f$, e definita $g$ come
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
	y = np.linalg.solve(L, P @ b)
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
A: [[ 0.49671415 -0.1382643   0.64768854  1.52302986 -0.23415337 -0.23413696
   1.57921282  0.76743473 -0.46947439  0.54256004]
 [-0.46341769 -0.46572975  0.24196227 -1.91328024 -1.72491783 -0.56228753
  -1.01283112  0.31424733 -0.90802408 -1.4123037 ]
 [ 1.46564877 -0.2257763   0.0675282  -1.42474819 -0.54438272  0.11092259
  -1.15099358  0.37569802 -0.60063869 -0.29169375]
 [-0.60170661  1.85227818 -0.01349722 -1.05771093  0.82254491 -1.22084365
   0.2088636  -1.95967012 -1.32818605  0.19686124]
 [ 0.73846658  0.17136828 -0.11564828 -0.3011037  -1.47852199 -0.71984421
  -0.46063877  1.05712223  0.34361829 -1.76304016]
 [ 0.32408397 -0.38508228 -0.676922    0.61167629  1.03099952  0.93128012
  -0.83921752 -0.30921238  0.33126343  0.97554513]
 [-0.47917424 -0.18565898 -1.10633497 -1.19620662  0.81252582  1.35624003
  -0.07201012  1.0035329   0.36163603 -0.64511975]
 [ 0.36139561  1.53803657 -0.03582604  1.56464366 -2.6197451   0.8219025
   0.08704707 -0.29900735  0.09176078 -1.98756891]
 [-0.21967189  0.35711257  1.47789404 -0.51827022 -0.8084936  -0.50175704
   0.91540212  0.32875111 -0.5297602   0.51326743]
 [ 0.09707755  0.96864499 -0.70205309 -0.32766215 -0.39210815 -1.46351495
   0.29612028  0.26105527  0.00511346 -0.23458713]]
b: [ 4.48061112 -7.90658235 -2.21843565 -3.10106666 -2.52822173  1.99441428
 -0.15056991 -0.47736123  1.01447432 -1.49191393]
Numero di condizione: 22.966778083194132

Soluzione calcolata: [ 0.51767993 -0.36499841  1.05619957 -3.93522785 -1.13832414 -0.90347745
  2.37839944 -0.81107005  6.32280319  2.3176568 ]
Soluzione reale: [1. 1. 1. 1. 1. 1. 1. 1. 1. 1.]
Errore relativo: 2.643852399605065
"""
```
ovviamente un risultato inaccettabile. In questo caso il numero di condizione è $\approx 23$.

##### Matrice di Hilbert

#### Conclusione

## Referenze
[^1]: informazione presa da [qui](https://my.liuc.it/MatSup/2009/Y90000/N3.doc) e [qui](https://lemesurierb.people.charleston.edu/elementary-numerical-analysis-python/notebooks/newtons-method-convergence-rate.html)