---
tags:
  - category/homework
  - status/pending
  - topic/calcolo-numerico
date: 26-12-2024 13:10:40
---
# Calcolo numerico - HW. 3
---
## Esercizi
### Problemi inversi
#### Introduzione
In questo esperimento si vuole, a partire da un [[Problemi inversi|problema inverso]] lineare [[Problema test| test]]:
- visualizzare le _[[Condizioni discrete di Picard|condizioni discrete di Picard]]_;
- calcolare la _soluzione naive_ (con [[Fattorizzazione ai valori singolari|SVD]]) e visualizzarla in un grafico;
- calcolare la _soluzione [[Regolarizzazione|regolarizzata]] con [[Fattorizzazione ai valori singolari troncata|TSVD]]_ e visualizzarla in un grafico (scegliendo il parametro $k$ usando le condizioni discrete di Picard);
- calcolare la _soluzione regolarizzata con [[Regolarizzazione alla Tikhonov|Tikhonov]]_ e visualizzarla in un grafico, scegliendo il parametro $\lambda$ usando il [[Principio di massima discrepanza|principio di massima discrepanza]] (e con _trial and error_).

Quindi, si vogliono ripetere questi punti _variando i livelli del rumore_ (3/4 volte) nell'intervallo $[0, 0.1]$.

#### Sviluppo

##### Problema test
Vogliamo creare il problema test della forma
$$Ax = y^{\delta}$$
dove:
- $A \in \mathbb{R}^{n \times n}$ è una matrice generata casualmente;
- $x \in \mathbb{R}^{n}$ è il vettore incognito;
- $y^{\delta} \in \mathbb{R}^{n}$ è il vettore osservato con rumore, ossia $y^{\delta} = y + \delta$.

Per fare ciò ci serviamo della libreria data in dotazione `ProblemiInversi`, usando la funzione `gravity` del file `examples.py`. In particolare, inizializziamo la dimensione del problema inverso lineare a $n = 30$, mentre il livello del rumore $\delta$ iniziale alla metà tra $0$ e $0.1$, ossia $0.05$:
```python
from ProblemiInversi import examples, operators, solvers, utilities
import numpy as np

np.random.seed(42)

n = 30
noise_level = 0.05

A, x = examples.gravity(n)
y = A @ x
y_delta = y + utilities.gaussian_noise(y, noise_level)
```

<u>Nota bene</u>: imposto un `seed` a `np.random` per la _riproducibilità dei risultati_.

A questo punto, prima di cominciare a risolvere il problema inverso, visualizziamo $x$, $y$ e $y^{\delta}$:
```python
import matplotlib.pyplot as plt

plt.plot(x)
plt.plot(y)
plt.plot(y_delta)

plt.legend(["$x$", "$y$", "$y^{\delta}$"])
plt.grid()
plt.show()
```
![[calcolo-hw-3-inverse-test1.png]]

Nonostante il rumore abbia un livello pari a $0.05$, si può notare come $y^{\delta}$ sia abbastanza diversa da $y$. Questo è **ciò che maggiormente influirà sulla risoluzione del problema inverso** se non gestito correttamente, ossia attraverso metodi di regolarizzazione.

Un altro caratteristico e importante aspetto del problema, è il condizionamento di $A$. Per come è stata costruita (dalla funzione `gravity`), nonostante la dimensione (solo $n = 30$) **la matrice $A$ è estremamente mal condizionata**:
```python
print(np.linalg.cond(A))

# Output: 737775839.5770929
```

##### Condizioni discrete di Picard
Visualizziamo quindi le condizioni discrete di Picard, per vedere fondamentalmente _l'influenza del rumore sulla sommatoria $x^{*} = \sum\limits_{i=1}^{n} \frac{u_{i}^{T}y^{\delta}}{\sigma_{i}} v_{i}$ della soluzione naive_ proposta successivamente.

Per farlo è prima necessario scomporre $A$ tramite SVD (decomposizione ai valori singolari) in $A = U\Sigma V^{T}$; successivamente, sullo stesso grafico si vogliono visualizzare:
- i _valori singolari_ $\sigma_{i}$;
- i _coefficienti di Fourier_ $u_{i}^{T}y^{\delta}$;
- i _coefficienti della soluzione_ $\frac{u_{i}^{T}y^{\delta}}{\sigma_{i}}$.

<u>Nota bene</u>: plottiamo tali valori su scala logaritmica per una migliore visualizzazione.

```python
U, s, VT = np.linalg.svd(A)
fourier = np.abs(U.T @ y_delta)
sol = fourier / s

plt.plot(s, 'bd')
plt.plot(fourier, 'ro-')
plt.plot(sol, 'ko-')

plt.xlabel(r"$i$")
plt.legend([r"$\sigma_{i}$", r"$|u_{i}^{T} y^{\delta}|$", r"$\frac{|u_{i}^{T} y^{\delta}|}{\sigma_{i}}$"])
plt.yscale("log")
plt.grid()
plt.show()
```
![[calcolo-hw-3-inverse-picard1.png]]

Possiamo notare che:
- i _valori singolari $\sigma_{i}$ decrescono esponenzialmente_ (considerando che il grafico è in scala logaritmica);
- i _coefficienti di Fourier decrescono più velocemente dei valori singolari fino a $i = 5$_, per poi oscillare nel range $[10^{-1}, 10^{1}]$;
- i _coefficienti della soluzione_, proprio come ci aspettavamo, per $i > 5$ _crescono esponenzialmente_.

In breve, **le condizioni discrete di Picard sono soddisfatte fino a $i = 5$**. In realtà il grafico fa partire $i$ da 0, quando nella formula della sommatoria parte da $1$: **in realtà allora le condizioni valgono fino a $i = 6$**.

Per mostrare l'influenza del rumore sulle condizioni discrete di Picard, mostriamo il grafico solo per $y$, ossia considerando solo la prima delle due sommatorie
$$x^{*} = \sum\limits_{i=1}^{n} \frac{u_{i}^{T}y}{\sigma_{i}}v_{i} + \sum\limits_{i=1}^{n} \frac{u_{i}^{T}\delta}{\sigma_{i}}v_{i}$$
```python
...
fourier = np.abs(U.T @ y)
...
```
![[calcolo-hw-3-inverse-picard2.png]]

Si nota come i coefficienti di Fourier decrescano _sempre_ più velocemente dei valori singolari: **le condizioni discrete di Picard sono sempre soddisfatte**.

##### Soluzione naive
Possiamo ora procedere a calcolare la soluzione naive del problema inverso. Se consideriamo il [[Problema dei minimi quadrati|problema ai minimi quadrati]] associato
$$\min_{x} {\|Ax - y^{\delta}\|_{2}}^{2}$$
allora la soluzione tramite decomposizione ai valori singolari risulta essere la semplice sommatoria
$$x^{*} = \sum\limits_{i=1}^{n} \frac{u_{i}^{T}y^{\delta}}{\sigma_{i}} v_{i}$$
che non tiene in considerazioni le condizioni discrete di Picard.
```python
tsvd_solver = solvers.TSVD(A)
x_star = tsvd_solver.solve(y_delta, k=n)

plt.plot(x)
plt.plot(x_star)
plt.plot(y_delta)
plt.legend(["$x$", "$x^{*}$", "$y^{\delta}$"])

plt.grid()
plt.show()
```
![[calcolo-hw-3-inverse-naive1.png]]
che in scala logaritmica appare come
![[calcolo-hw-3-inverse-naive2.png]]

Un risultato ovviamente inaccettabile: la soluzione $x^{*}$ è completamente diversa da $x$, e _caratterizzata da forti oscillazioni_. Queste sono il risultato di alti coefficienti della soluzione per $i \gg 6$, che **moltiplicando i vettori singolari destri $v_{i}$, di fatto delle oscillazioni, ingigantiscono queste ultime**.

##### Soluzione regolarizzata con TSVD
Per risolvere correttamente il problema inverso, una delle tecniche di regolarizzazione adottate è la TSVD, la _decomposizione ai valori singolari troncata_. Questa consiste nel _tagliare_ la sommatoria $x^{*}$ a un certo valore $k < n$, solitamente scelto in base alle condizioni discrete di Picard.

Nel nostro caso queste condizioni sono soddisfatte fino a $i = 6$, per cui se scegliamo $k = 6$ dovremmo ottenere una soluzione non condizionata dalla presenza del rumore.

<u>Attenzione</u>: scegliendo un valore di $k < n$ e quindi _troncando la sommatoria_, ovviamente la soluzione calcolata sarà un'**approssimazione** di quella reale.
```python
...
x_star = tsvd_solver.solve(y_delta, k=6)
...
```
![[calcolo-hw-3-inverse-tsvd1.png]]

Ovviamente la soluzione, ora, è molto più vicina a quella reale, e le oscillazioni sono _quasi_ del tutto scomparse. Ancora però è possibile notare un _andamento oscillatorio, che potrebbe essere ridotto ulteriormente_: infatti sono stato troppo ottimista, e riguardando bene il grafico delle condizioni discrete di Picard, **queste sono soddisfatte fino a $i = 4$** ($3+1$ perché parte da 0). Già _all'iterazione successiva i coefficienti di Fourier decrescono meno velocemente dei valori singolari_, invalidando le condizioni discrete di Picard.
Se proviamo a calcolare la soluzione con $k = 4$ otteniamo infatti un risultato migliore:
![[calcolo-hw-3-inverse-tsvd2.png]]

Se aumentiamo $k$ anche solo a $7$, le oscillazioni ricompaiono istantaneamente:
![[calcolo-hw-3-inverse-tsvd3.png]]

Viceversa, diminuendo $k$ a $2$, la soluzione calcolata risulta troppo approssimata:
![[calcolo-hw-3-inverse-tsvd4.png]]

A questo punto, definito $k=4$ come valore migliore, calcoliamo l'errore relativo tra la soluzione calcolata $x^{*}$ e quella reale $x$, per poter confrontare i risultati con le successive tecniche di regolarizzazione:
```python
err = utilities.rel_err(x_star, x)
print(err)

# Output: 0.10271233511446931
```

##### Soluzione regolarizzata con Tikhonov
Un'altra tecnica di regolarizzazione molto utilizzata è la _regolarizzazione alla Tikhonov_, che consiste nel modificare il problema dei minimi quadrati associato al problema inverso nella forma
$$\min_{x} {\|Ax - y^{\delta}\|_{2}}^{2} + \lambda {\|Lx\|_{2}}^{2}$$

A questo punto, decomposta $A$ in $A = U\Sigma V^{T}$, la soluzione $x^{*}$ del problema regolarizzato viene calcolata come
$$x^{*} = \sum\limits_{i=1}^{n} f_{i} \frac{u_{i}^{T}y^{\delta}}{\sigma_{i}} v_{i}$$
dove $f_{i}$, detti _fattori di filtro_, sono
$$f_{i} = \frac{\sigma_{i}^{2}}{\sigma_{i}^{2} + \lambda}$$

Il parametro di regolarizzazione $\lambda$ è scelto in base a quanto si vuole regolarizzare la soluzione. Per sceglierlo, useremo due metodologie:
- _trial and error_ --> si sceglie $\lambda$ randomicamente e a seconda del grafico prodotto e dell'errore relativo si decide se aumentare o diminuire il valore;
- _principio di massima discrepanza_ --> si sceglie $\lambda$ tale che vengano uguagliati i termini ${\|Ax - y^{\delta}\|_{2}}^{2}$ e $\nu {\|\delta\|_{2}}^{2}$, dove $\nu$ è un valore di tolleranza (solitamente $1.01$ o $1.001$).

###### Trial and error
Cominciamo allora impostando il parametro $\lambda$ a $0.01$:
```python
lmbda = 0.01
tikhonov_solver = solvers.Tikhonov(A)
x_star = tikhonov_solver.solve(y_delta, lmbda=lmbda)
```
![[calcolo-hw-3-inverse-tik1.png]]

E' ancora possibile vedere delle oscillazioni, aumentiamo allora $\lambda$ a $0.1$:
![[calcolo-hw-3-inverse-tik2.png]]

Ancora troppo oscillante, aumentiamo $\lambda$ a $1$:
![[calcolo-hw-3-inverse-tik3.png]]

Ora le oscillazioni sono scomparse, ma la soluzione è troppo approssimata. Proviamo con $\lambda = 0.5$:
![[calcolo-hw-3-inverse-tik4.png]]

Sembra essere un valore abbastanza accettabile, ma forse ancora troppo alto. Proviamo con $\lambda = 0.3$:
![[calcolo-hw-3-inverse-tik5.png]]

Tornano le oscillazioni, per cui $\lambda = 0.5$ sembra essere il valore migliore.

Per dimostrarlo, calcoliamo l'errore relativo tra la soluzione calcolata $x^{*}$ e quella reale $x$ al variare di $\lambda$ da $0.1$ a $1$:
```python
lmbdas = np.linspace(0.1, 1)
tikhonov_solver = solvers.Tikhonov(A)

errs = []
for lmbda in lmbdas:
	x_star = tikhonov_solver.solve(y_delta, lmbda=lmbda)
	errs.append(utilities.rel_err(x_star, x))

plt.plot(lmbdas, errs)
plt.xlabel(r"$\lambda$")
plt.ylabel(r"$\frac{||x - x^{*}||}{||x||}$")

plt.grid()
plt.show()
```
![[calcolo-hw-3-inverse-tik6.png]] ^c90f12

Sembra proprio che _per $\lambda = 0.5$ l'errore relativo sia il minore_.

Oltretutto si ottiene un valore dell'errore relativo minore di quello ottenuto con la TSVD:
```python
err = utilities.rel_err(x_star, x)
print(err)

# Output: 0.09407174656358783
```

###### Principio di massima discrepanza
Per scegliere il parametro di regolarizzazione $\lambda$ usando il principio di massima discrepanza, è necessario prima calcolare la [[Norma vettoriale|norma 2]] del rumore $\delta$ (che noi abbiamo in quanto siamo in un problema test):
```python
delta_norm = np.linalg.norm(y_delta - y)
print(delta_norm)

# Output: 1.2810090098019478
```

A questo punto non ci resta che scegliere il $\lambda$ che soddisfi la relazione
$${\|Ax_{\text{tik}} - y^{\delta}\|_{2}}^{2} = \nu {\|\delta\|_{2}}^{2}$$

Per farlo, fissato $\nu = 1.01$, **sfruttiamo il fatto che dalla teoria sappiamo che una soluzione a questa equazione esiste ed è unica** (perché il residuo ${\|Ax_{\text{tik}} - y^{\delta}\|_{2}}^{2}$ varia con continuità rispetto alla scelta di $\lambda$): possiamo quindi **usare un [[Algoritmi per il calcolo delle radici di una funzione|metodo numerico per trovare la soluzione]]**, come ad esempio il [[Algoritmo di bisezione|metodo di bisezione]].

Considerata $f(\lambda) = {\|Ax_{\text{tik}} - y^{\delta}\|_{2}}^{2} - \nu {\|\delta\|_{2}}^{2}$, ci è sufficiente trovare due punti $a$ e $b$ tali che $f(a) \cdot f(b) < 0$.
```python
nu = 1.01
delta_norm = np.linalg.norm(y - y_delta)
tikhonov_solver = solvers.Tikhonov(A)

def f(lmbda):
	x_star = tikhonov_solver.solve(y_delta, lmbda=lmbda)
	return np.linalg.norm(A @ x_star - y_delta)**2 - nu * delta_norm**2

print(f(0.01))
print(f(1))

# Output:
"""
-0.649353870470535
0.13807920732034695
"""
```

Abbiamo i due punti, quindi definiamo l'algoritmo di bisezione
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
ed invochiamolo su $f$, $a = 0.01$, $b = 1$ e $n = 1000$:
```python
lmbda = bisection(f, 0.01, 1, 1000)
print(lmbda)

# Output: 0.8827773555990632
```

Sembra che la soluzione sia $\lambda = 0.8827773555990632$. Se vogliamo essere certi di ciò, possiamo plottare $f$ sul range $[0.01, 1]$:
```python
lmbda = bisection(f, 0.01, 1, 100)
lmbdas = np.linspace(0.01, 1)
fs = [f(lmbda) for lmbda in lmbdas]

plt.plot(lmbdas, fs)
plt.plot(lmbda, f(lmbda), 'ro')
plt.xlabel(r"$\lambda$")
plt.ylabel(r"$f(\lambda)$")
plt.grid()
plt.show()
```
![[calcolo-hw-3-inverse-tik7.png]]

Se modifichiamo $\nu$ a $1.001$, invece, otteniamo come soluzione $\lambda = 0.8696197082621395$.

Non ci rimane che vedere come si comporta la soluzione calcolata con il $\lambda$ trovato:
![[calcolo-hw-3-inverse-tik8.png]]

Dal [[#^c90f12|grafico mostrato in precedenza]] **si può notare che per $\lambda = 0.5$ il valore dell'errore relativo è minore che per $\lambda \approx 0.88$**: anzi, **per $\lambda = 0.5$ l'errore relativo è al minimo globale**.

Questo dimostra che **il principio di massima discrepanza non garantisce, se rispettato, la scelta del parametro di regolarizzazione ottimale**, ma **solo una scelta ragionevole, basata sul rapporto tra dati e rumore**.

##### Variazione del rumore
Per concludere, ripetiamo tutti i passaggi precedenti variando il livello del rumore $\delta$ nell'intervallo $[0, 0.1]$. In particolare, scegliamo i seguenti 4 valori
$$[0, 0.033, 0.066, 1]$$
e per ognuno di essi ripercorriamo i punti precedenti.

###### Livello $= 0$
Il caso banale in cui il rumore è nullo, ossia $y^{\delta} = y$, prevede che:
- le **condizioni discrete di Picard siano sempre rispettate**;
- la **soluzione naive sia uguale a quella reale**;
- la **soluzione TSVD sia uguale a quella reale**, in quanto $k=n \implies$ TSVD = SVD;
- la soluzione Tikhonov calcolata sia con _trial and error_ che con il _principio di massima discrepanza_ produca **$\lambda = 0$ come migliore parametro di regolarizzazione**.

Modifichiamo intanto il problema test tale da avere un rumore nullo:
```python
n = 30
noise_level = 0

A, x = examples.gravity(n)
y = A @ x
y_delta = y + utilities.gaussian_noise(y, noise_level)
```

Quindi mostriamo le condizioni discrete di Picard:
```python
U, s, VT = np.linalg.svd(A)
fourier = np.abs(U.T @ y_delta)
sol = fourier / s

plt.plot(s, 'bd')
plt.plot(fourier, 'ro-')
plt.plot(sol, 'ko-')

plt.xlabel(r"$i$")
plt.legend([r"$\sigma_{i}$", r"$|u_{i}^{T} y|$", r"$\frac{|u_{i}^{T} y|}{\sigma_{i}}$"])
plt.yscale("log")
plt.grid()
plt.show()
```
![[calcolo-hw-3-inverse-noise1.png]]

Come già detto, le condizioni discrete di Picard sono sempre rispettate.

Quindi l'algoritmo SVD naive produce una soluzione corretta:
```python
tsvd_solver = solvers.TSVD(A)
x_star = tsvd_solver.solve(y_delta, k=n)

plt.plot(x)
plt.plot(x_star)
plt.plot(y_delta)
plt.legend(["$x$", "$x^{*}$", "$y^{\delta}$"])
plt.grid()
plt.show()
```
![[calcolo-hw-3-inverse-noise2.png]]

<u>Attenzione</u>: la soluzione naive è uguale a quella reale, per cui _il grafico delle due curve è sovrapposto_.

La soluzione con TSVD allora è automaticamente calcolata, in quanto $k = n$. Invece, per quanto riguarda la regolarizzazione alla Tikhonov, cominciamo impostando il problema regolarizzato con $\lambda = 0.5$ (come fatto in precedenza):
```python
lmbda = 0.5
tikhonov_solver = solvers.Tikhonov(A)
x_star = tikhonov_solver.solve(y_delta, lmbda=lmbda)
...
```
![[calcolo-hw-3-inverse-noise3.png]]

Notiamo che la **regolarizzazione**, in questo caso, ha un **effetto addirittura negativo sulla soluzione calcolata**. Finisce per _approssimarla_, quando quella calcolata senza regolarizzazione sarebbe già perfetta.

Se per esempio poniamo $\lambda = 1$, otteniamo una soluzione ancora più approssimata:
![[calcolo-hw-3-inverse-noise4.png]]

Ora, variamo $\lambda$ da $0.01$ a $1$, e calcoliamo l'errore relativo tra la soluzione calcolata e quella reale. Sappiamo che per $\lambda = 0$ l'errore relativo è nullo, per questo partiamo da $0.01$:
```python
lmbdas = np.linspace(0.01, 1)
errs = []
for lmbda in lmbdas:
	x_star = tikhonov_solver.solve(y_delta, lmbda=lmbda)
	err = utilities.rel_err(x_star, x)
	errs.append(err)

plt.plot(lmbdas, errs)
plt.xlabel(r"$\lambda$")
plt.ylabel(r"$\frac{||x - x^{*}||}{||x||}$")
plt.grid()
plt.show()
```
![[calcolo-hw-3-inverse-noise5.png]]

Risulta abbastanza chiaro come l'_errore relativo non faccia che crescere all'aumentare di $\lambda$_.

Se applichiamo il principio di massima discrepanza con $\delta = \underline{0}$, significa che stiamo cercando il $\lambda$ tale che il residuo dei minimi quadrati sia nullo:
$${\|Ax_\text{tik} - y^{\delta}\|_{2}}^{2} = \underline{0}$$

E siamo sicuri del fatto che questo $\lambda$, trattandosi di un problema test e sapendo che $y^{\delta} = y = Ax$, sia $\lambda = 0$.

###### Livello $= 0.033$
Ora concentriamoci ad analizzare il caso in cui il rumore ha un livello di $0.033$.
Per quanto riguarda le condizioni discrete di Picard, ci aspettiamo che siano rispettate più a lungo del caso con livello del rumore pari a $0.05$. Verifichiamo se è effettivamente così (ometto il codice):
![[calcolo-hw-3-inverse-noise6.png]]

In effetti, in questo caso le condizioni discrete di Picard sembrano essere rispettate _completamente_ fino a $i = 5 + 1 = 6$, ossia ben 2 valori in più rispetto al caso precedente.

La soluzione naive, teoricamente, _seppur scorretta e oscillante dovrebbe essere leggermente migliore_ rispetto al caso del livello di rumore pari a $0.05$:
![[calcolo-hw-3-inverse-noise7.png]]
che in scala logaritmica appare come
![[calcolo-hw-3-inverse-noise8.png]]

In effetti, le oscillazioni raggiungono un massimo di $3 \times 10^{6}$, contro i $4 \times 10^{6}$ del caso precedente.

La soluzione per TSVD, considerando $k = 6$, risulta essere:
![[calcolo-hw-3-inverse-noise9.png]]

Anche in questo caso forse siamo stati troppo ottimisti, e $k = 5$ sarebbe stato un valore migliore:
![[calcolo-hw-3-inverse-noise10.png]]

L'errore relativo, in questo caso, è $0.09151738982686286$.

Se portiamo $k$ a $4$, invece, cominciano a verificarsi i primi sintomi di approssimazione:
![[calcolo-hw-3-inverse-noise11.png]]

Procediamo quindi con la regolarizzazione alla Tikhonov. Per quanto riguarda il _trial and error_, ci aspettiamo che il valore di $\lambda$ ottimale (che minimizza l'errore relativo) sia inferiore a $0.5$. Verifichiamo plottando l'errore relativo al variare di $\lambda$ (ometto il codice):
![[calcolo-hw-3-inverse-noise12.png]]

Infatti sembrerebbe proprio che in questo caso il $\lambda$ ottimale cada su $0.3$. Tra l'altro, l'errore relativo prodotto è inferiore al minimo che si otteneva nel caso con livello del rumore a $0.05$.
Mostriamo la soluzione calcolata con $\lambda = 0.3$:
![[calcolo-hw-3-inverse-noise13.png]]
con errore relativo pari a $0.07398552101051747$, _anche in questo caso inferiore al minimo ottenuto con la TSVD_.

Per quanto riguarda il _principio di massima discrepanza_, anche in questo caso procediamo risolvendo l'equazione $f(\lambda) = 0$ dove $f(\lambda) = {\|Ax_{\text{tik}} - y^{\delta}\|_{2}}^{2} - \nu {\|\delta\|_{2}}^{2}$, tramite l'algoritmo di bisezione. Otteniamo come risultato $\lambda = 0.5594090592810059$, comunque inferiore a quello precedentemente calcolato ($\approx 0.88$). Questa produce la soluzione
![[calcolo-hw-3-inverse-noise14.png]]
e ha un errore relativo di $0.08121178110659376$: anche in questo caso, il $\lambda$ calcolato con il _principio di massima discrepanza_ produce un errore relativo maggiore di quello calcolato tramite _trial and error_.

###### Livello $= 0.066$
A questo punto, nel caso in cui il livello del rumore sia di $0.066$, ci aspettiamo gli effetti opposti rispetto al caso precedente:
- le **condizioni discrete di Picard saranno rispettate per un numero di valori inferiore a $4$**;
- la **soluzione naive sarà ancora più oscillante**;
- la **soluzione TSVD**, avendo $k < 4$, sarà **ancora più approssimata**;
- la **soluzione con Tikhonov richiederà un $\lambda > 0.5$**, sia per la soluzione calcolata con _trial and error_ che con il _principio di massima discrepanza_.

Iniziamo a verificare le condizioni discrete di Picard:
![[calcolo-hw-3-inverse-noise15.png]]

Risulta molto più netta la definizione delle condizioni, che non si verificano più a partire da $i = 4+1 = 5$. Quindi sono rispettate fino a $i = 4$ (compreso).

La soluzione naive, come previsto, è ancora più oscillante:
![[calcolo-hw-3-inverse-noise16.png]]

Difatti il picco raggiunge il valore $6 \times 10^{6}$.

Per cui procediamo con la TSVD per $k = 4$:
![[calcolo-hw-3-inverse-noise17.png]]

In questo caso erano più esplicite le condizioni di Picard, infatti $k=4$ sembra essere il valore migliore. L'errore relativo prodotto da questa soluzione è $0.11305758025767368$, che considerando il livello del rumore aumentato è un valore buono.

Per quanto riguarda la regolarizzazione alla Tikhonov, plottiamo l'andamento dell'errore relativo al variare di $\lambda$ per scegliere quello migliore secondo il _trial and error_:
![[calcolo-hw-3-inverse-noise18.png]]
Ecco che il minimo sembra essersi spostato a $\lambda = 0.59$, con errore relativo $0.11152017677665496$: sempre leggermente inferiore alla soluzione con TSVD. La soluzione calcolata con $\lambda = 0.59$ è la seguente:
![[calcolo-hw-3-inverse-noise19.png]]
che non sembra minimamente migliore di quella calculata con TSVD per $k=4$, anzi... A quanto pare **l'errore relativo rimane una misura poco affidabile per confrontare soluzioni a questo genere di problemi**.

Ci aspettiamo che anche il valore di $\lambda$ calcolato con il _principio di massima discrepanza_ sia superiore a quello per livello del rumore pari a $0.05$, ossia $\approx 0.88$. Risolvendo l'equazione con l'algoritmo di bisezione, otteniamo infatti $\lambda = 1.2029007018148157 \gg 0.88$, che produce come soluzione:
![[calcolo-hw-3-inverse-noise20.png]]

L'errore relativo di questa soluzione è $0.1258102379637712$, ma nonostante ciò è molto simile a quella calcolata con $\lambda = 0.59$.

###### Livello $= 1$
Concludiamo con il caso in cui il rumore ha un livello pari a $1$. Ci si aspetta un "inasprimento" di tutti i fenomeni visti nel caso precedente.

In particolare, le condizioni discrete di Picard saranno rispettate per meno valori di $i$:
![[calcolo-hw-3-inverse-noise21.png]]
e invece, le condizioni vengono rispettate sempre per i primi 4 valori, per cui $k=4$ è ancora il valore migliore.

La soluzione naive dovrebbe produrre risultati ancora più oscillanti:
![[calcolo-hw-3-inverse-noise22.png]]

In effetti il picco della soluzione $x^{*}$ arriva quasi a $10^{7}$.

La soluzione TSVD, considerando $k=4$, è la seguente:
![[calcolo-hw-3-inverse-noise23.png]]
con un errore relativo pari a $0.13989281218872532$.

Per quanto riguarda la regolarizzazione alla Tikhonov, plottiamo sempre l'errore relativo al variare di $\lambda$:
![[calcolo-hw-3-inverse-noise24.png]]

Il minimo cade all'incirca su $\lambda = 0.8$, cui soluzione associata è
![[calcolo-hw-3-inverse-noise25.png]]
con errore relativo $0.14711541548315837$. **Per la prima volta notiamo che l'errore relativo è maggiore di quello calcolato con TSVD**!

Quindi **Tikhonov ha dei limiti**, e _sembrerebbe che questi si raggiungano man mano che il livello del rumore aumenta_ (mostreremo di seguito dei risultati più approfonditi).

Infine, calcoliamo il $\lambda$ ottimale secondo il _principio di massima discrepanza_. Il risultato è $\lambda = 1.9207227358188246$:
![[calcolo-hw-3-inverse-noise26.png]]
con errore relativo $0.1650459971800084$. Anche in questo caso l'errore relativo è maggiore di quello calcolato con TSVD e con Tikhonov _trial and error_.

###### Resoconto
Vogliamo adesso raccogliere i risultati calcolati sui vari livelli di rumore per ogni metodo utilizzato. In particolare, escludendo la soluzione naive, vogliamo confrontare TSVD, Tikhonov _trial and error_ e Tikhonov _principio di massima discrepanza_ su:
- **soluzioni calcolate $x^{*}$**,
- **$k$ e $\lambda$ ottimali**,
- **errori relativi**,

al variare del livello del rumore (escludendo quello nullo).

Partiamo con il confronto visivo delle soluzioni calcolate, per ogni livello di rumore (_assumendo di scegliere gli iperparametri migliori per ogni metodo_):
![[calcolo-hw-3-inverse-confr1.png]]
![[calcolo-hw-3-inverse-confr2.png]]
![[calcolo-hw-3-inverse-confr3.png]]

Possiamo facilmente osservare che all'aumentare del livello del rumore, **le soluzioni calcolate tramite TSVD risultano più fedeli alla _ground truth_**, mentre **le soluzioni calcolate tramite Tikhonov risultano sempre più influenzate dal rumore**. E aumentando il parametro di regolarizzazione $\lambda$, non migliora la situazione! I $\lambda$ selezionati sono gli "ottimali" in quel campo della regolarizzazione: per il _trial and error_ sono quelli che minimizzano l'errore relativo; per il _principio di massima discrepanza_ sono quelli che uguagliano i residui dei minimi quadrati e del rumore. **Il problema, quindi, sta proprio in Tikhonov**! E' la tecnica stessa che, **per livelli di rumore molto grandi, non sembra risultare adatta**. Questo avviene per via del fatto che **i fattori di filtro $f_{i}$ di Tikhonov considerano sempre, anche in minima parte, gli ultimi coefficienti della soluzione, che per via del rumore sono molto alti**. Più il rumore aumenta, più le oscillazioni si fanno sentire, anche su $\lambda$ alti.

Ora, partendo dalla TSVD, mostriamo l'andamento dei $k$ per cui le condizioni discrete di Picard sono rispettate al variare del rumore:
![[calcolo-hw-3-inverse-confr4.png]]

Si potrebbe ipotizzare che l'_andamento del valore di $k$ sia quasi-iperbolico rispetto al livello del rumore_, tale che
$$\eta \longrightarrow +\infty \implies k \longrightarrow 1$$
e viceversa che
$$\eta \longrightarrow 0 \implies k \longrightarrow n$$

Invece, adesso, mostriamo l'andamento dei $\lambda$ ottimali calcolati con il _trial and error_ e con il _principio di massima discrepanza_ al variare del livello del rumore $\eta$:
![[calcolo-hw-3-inverse-confr5.png]]

Come già avevamo potuto notare, all'aumentare del rumore, **il principio di massima discrepanza tende a scegliere $\lambda$ più alti rispetto al trial and error**.

Ma veniamo al dunque, ossia al confronto tra gli errori relativi prodotti dai vari metodi al variare del livello del rumore:
![[calcolo-hw-3-inverse-confr6.png]]

Chiaramente i dati sono insufficienti per trarre delle conclusioni definitive, ma dal grafico si può osservare come, in questo specifico caso di studio:
- la **TSVD**, **per livelli di rumore molto alti**, è la **tecnica che produce il minor errore relativo**;
- la **Tikhonov**, sia con _trial and error_ che con il _principio di massima discrepanza_, **all'aumentare del livello del rumore produce un errore relativo maggiore rispetto alla TSVD**;
- il **principio di massima discrepanza** sembra sempre determinare come ottimali dei **valori di $\lambda$ che producono un errore relativo maggiore rispetto al trial and error**.

#### Conclusioni
In conclusione, in questo esperimento abbiamo potuto osservare noi stessi come, **nonostante la perdita di informazioni della TSVD, questa risulti essere la tecnica migliore per risolvere problemi lineari inversi con livelli di rumore molto alti**, ma per livelli bassi rischia di approssimare troppo la soluzione.

Viceversa, **la regolarizzazione alla Tikhonov garantisce risultati più precisi in presenza di basso rumore**, mentre per rumori alti non è in grado di produrre una regolarizzazione efficace, _a prescindere dalla scelta di $\lambda$_.

Inoltre abbiamo osservato come **il principio di massima discrepanza non garantisce la scelta del parametro di regolarizzazione ottimale in senso globale** (che minimizzi l'errore relativo), ma **solo una scelta ragionevole basata sul rapporto tra dati e rumore**.

### Imaging
#### Introduzione
In quest'ultima esercitazione, ci occuperemo di una delle maggiori applicazioni dei problemi inversi: l'[[Imaging|imaging]]. In particolare, scelta un'immagine in scala di grigi, _il nostro intento sarà quello di studiare il problema lineare inverso associato alla sua acquisizione tramite un sistema di imaging_, con lo scopo di _ricostruire l'immagine originale_.

Nel dettaglio, seguiremo i seguenti passi:
- _creazione del problema test_, ovvero applicazione della [[PSF]] e del [[Rumore bianco|rumore bianco]] all'immagine, con iperparametri (come dimensione e sfocatura del [[Matrice di convoluzione|kernel]] e livello del rumore) scelti arbitrariamente;
- _calcolo della soluzione naive_, attraverso [[CGLS]] applicata direttamente al problema dei minimi quadrati associato;
- _calcolo della soluzione regolarizzata alla Tikhonov_, con $\lambda$ scelto sia tramite _principio di massima discrepanza_ che come quello che _minimizza l'errore assoluto_;
- _calcolo della soluzione regolarizzata con [[Variazione totale|variazione totale]]_, con $\lambda$ scelto come quello che _minimizza l'errore assoluto_.

Quindi, ripeteremo tutti i passaggi per 3/4 diversi livelli di rumore (tra $0$ e $0.01$), e 2 diversi valori dei parametri del nucleo gaussiano della PSF.

Per ogni risultato ottenuto, calcoreremo la qualità del risultato secondo le 3 metriche principali studiate:
- _errore relativo_,
- _PSNR_,
- _SSIM_.

##### Immagine
Prima di cominciare con i passaggi, vorrei fare qualche precisazione sull'immagine scelta:
![[sky-gray.jpg]]

L'immagine è stata scelta sulla base di 4 criteri:
- **dimensione**, che non fosse troppo grande per evitare tempi di calcolo eccessivi --> di fatto è _$600 \times 450$ pixels_, molto simile alla $512 \times 512$ pixels del cameraman;
- **colori**, tale che solo una parte dell'immagine fosse praticamente nera, per poter osservare meglio l'effetto delle [[Matrice estesa#Condizioni al bordo|condizioni di bordo]] sulla PSF --> in questo caso _la parte inferiore dell'immagine ha toni molto scuri_;
- **dettagli**, tali da confonderli con il rumore per mettere alla prova le tecniche di regolarizzazione --> _le stelle dell'immagine servono a questo_;
- **contorni**, che fossero ben definiti in certe zone dell'immagine --> _le scritte sui cartelli stradali sono perfette per questo_.

#### Sviluppo
##### Problema test
Possiamo quindi cominciare a definire il problema test, partendo dalla visualizzazione dell'immagine stessa. Usiamo in particolare la libreria `skimage` per caricare l'immagine, e `matplotlib` per visualizzarla:
```python
import matplotlib.pyplot as plt
import skimage

x = skimage.io.imread("sky-gray.jpg", as_gray=True)

plt.figure(figsize=(10, 7))
plt.imshow(x, cmap='gray')
plt.axis('off')
plt.show()
```
![[calcolo-hw-3-imaging-test1.png]]

<u>Nota bene</u>: il passaggio `x = x / x.max()`, che normalmente servirebbe per normalizzare i valori dei pixel dell'immagine tra $[0, 1]$ da quelli di partenza tra $[0, 255]$, non è necessario l'immagine è già normalizzata se importata con il flag `as_gray=True`.

Ora possiamo impostare gli iperparametri principali e creare il problema test:
- _dimensione del kernel della PSF_ --> _$11 \times 11$_;
- _deviazione standard del kernel della PSF_ --> $3$;
- _livello del rumore_ --> $0.005$ (a metà tra $0$ e $0.01$).

```python
from ProblemiInversi import examples, operators, solvers, utilities
import numpy as np

np.random.seed(42)

kernel_size = 11
sigma = 3
noise_level = 0.005

kernel = utilities.gaussian2d_kernel(k=kernel_size, sigma=sigma)
A = operators.ConvolutionOperator(kernel)
y = A(x)
y_delta = y + utilities.gaussian_noise(y, noise_level=noise_level)
```

<u>Nota bene</u>: inizializzo `np.random.seed` sempre per garantire la _riproducibilità dei risultati_.

Mostriamo quindi il risultato della sola PSF, ossia `y`:
```python
plt.figure(figsize=(10, 7))
plt.imshow(y, cmap='gray')
plt.axis('off')
plt.show()
```
![[calcolo-hw-3-imaging-test2.png]]

Possiamo notare che la sfocatura è molto evidente, e chiaramente molti dettagli dell'immagine sono andati persi. Inoltre, le condizioni al bordo di tipo **zero padding** sono piuttosto visibili: _l'immagine è circondata da un alone nero_.

E infine mostriamo il risultato finale aggiungendo il rumore, ossia `y_delta`:
```python
plt.figure(figsize=(10, 7))
plt.imshow(y_delta, cmap='gray')
plt.axis('off')
plt.show()
```
![[calcolo-hw-3-imaging-test3.png]]

E' quasi impercettibile, ma il rumore è presente. Come abbiamo avuto modo di sperimentare nell'esercitazione precedente, **anche se il livello del rumore è basso, può avere un impatto significativo sulla qualità della soluzione calcolata** (senza regolarizzazione).

##### Soluzione naive
Possiamo procedere con il calcolo della soluzione naive, che prevede di _applicare direttamente la CGLS al problema dei minimi quadrati_
$$\min_{x} {\|Ax - y^{\delta}\|_{2}}^{2}$$
dove:
- $Ax = K * x$, e $K$ è il kernel della PSF mentre $x$ è l'immagine (come vettore tramite [[Riordinamento lessicografico|riordinamento lessicografico]]);
- $y^{\delta}$ è l'immagine acquisita con il rumore.

Per farlo ci è sufficiente usare le classi del file `solvers.py` della libreria `ProblemiInversi`, fissando i seguenti iperparametri:
- `x0 = np.zeros_like(x)`, ossia il vettore di partenza dell'algoritmo sarà un vettore di zeri;
- `maxit = 1000`, o un valore tale da garantire l'uscita dell'algoritmo per tolleranza (`tolx` o `tolf`);
- `tolx = 1e-8`;
- `tolf = 1e-8`.

<u>Attenzione</u>: in realtà, solo per questo tipo di soluzione, _è consentita l'uscita dell'algoritmo per numero di iterazioni_. Questo perché, in quanto naive, _ad ogni iterazione il "vettore immagine" $x^{*}$ sarà sempre più condizionato dal rumore_, e quindi non ha senso continuare oltre un certo numero di iterazioni aspettando l'uscita per tolleranza.

Proprio per questo motivo, allora, proviamo ad eseguire l'algoritmo su valori di `maxit` piuttosto bassi, che ci permettano di ottenere una soluzione in tempi ragionevoli. In particolare proveremo con `10`, `30`, `100` e `200` iterazioni:
```python
x0 = np.zeros_like(x)
maxit = 10
tolx = 1e-8
tolf = 1e-8

cgls_solver = solvers.CGLS(A)
x_cgls = cgls_solver.solve(y_delta, x0, kmax=maxit, tolf=tolf, tolx=tolx)

plt.figure(figsize=(10, 7))
plt.imshow(x_cgls, cmap='gray')
plt.axis('off')
plt.show()
```

Quindi, il risultato per `maxit = 10` è:
![[calcolo-hw-3-imaging-naive1.png]]

Per `maxit = 30`:
![[calcolo-hw-3-imaging-naive2.png]]

Per `maxit = 100`:
![[calcolo-hw-3-imaging-naive3.png]]

E per `maxit = 200`:
![[calcolo-hw-3-imaging-naive4.png]]

###### Osservazioni
Possiamo analizzare il risultato tramite soluzione naive secondo diversi aspetti.
In particolare, all'aumentare di `maxit` avvengono 2 fenomeni:
- **la soluzione diventa più nitida**, con contorni più riconoscibili e definiti --> _la sfocatura della PSF viene attenuata_;
- **la soluzione diventa più rumorosa**, con l'aggiunta di dettagli che non erano presenti nell'immagine originale --> _il rumore presente nell'immagine acquisita viene amplificato_.

Nel dettaglio, possiamo notare che partendo dall'immagine originale
![[calcolo-hw-3-imaging-test3.png]]
da cui **non è assolutamente possibile leggere le scritte sui cartelli stradali**, la **soluzione naive anche dopo sole 100 iterazioni riesce a recuperarle**, producendo l'immagine
![[calcolo-hw-3-imaging-naive3.png]]
da cui è facilmente possibile leggere le scritte "_STOP_" e "_MILKY WAY_".

Tuttavia, sempre a partire dall'immagine prodotta dopo 100 iterazioni, **si cominciano a palesare gli effetti di un rumore mal gestito**: si notano bene nella parte inferiore dell'immagine, dove _ciò che dovrebbe essere nero sembra invece essere costellato da "biscioline" grigie_.
Questo effetto peggiora ulteriormente aumentando il numero di iterazioni, come si può notare nell'immagine prodotta dopo 200 iterazioni.

Detto questo, le vere metriche di valutazione della qualità della soluzione sono quelle calcolate tramite errore relativo, PSNR e SSIM. Se consideriamo il _risultato ottenuto dopo 100 iterazioni come il migliore tra quelli ottenuti_, allora il risultato delle metriche sarà il seguente:
```python
err_rel = utilities.rel_err(x_cgls, x)
psnr = utilities.psnr(x_cgls, x)
ssim = utilities.ssim(x_cgls, x)

print(f"Relative error: {err_rel}")
print(f"PSNR: {psnr}")
print(f"SSIM: {ssim}")

# Output:
"""
Relative error: 0.18023452730385733
PSNR: 24.289670040063285
SSIM: 0.3767979121752091
"""
```

Considerando l'aumentare dell'effetto del rumore, per `maxit = 200` il PSNR (Peak Signal-to-Noise Ratio) dovrebbe diminuire molto:
```python
"""
Relative error: 0.2966409018243997
PSNR: 19.961809221892942
SSIM: 0.25773231395365276
"""
```
Di fatti, considerando la scala logaritmica del PSNR, **una diminuzione di 4 dB è molto significativa** (l'unità di misura è in decibel).

##### Soluzione regolarizzata con Tikhonov
Passiamo ora alla soluzione regolarizzata con Tikhonov. Ricordiamo che il problema da risolvere, attraverso regolarizzazione, viene modificato in:
$$\min_{x} {\|Ax - y^{\delta}\|_{2}}^{2} + \lambda {\|Lx\|_{2}}^{2}$$
dove:
- $\lambda$ è il _parametro di regolarizzazione_;
- $L$ è la _matrice di regolarizzazione_, solitamente $= I$.

Ciò che influenza quindi la regolarizzazione della soluzione è il parametro $\lambda$, che andiamo a scegliere secondo 2 criteri:
- _minimo errore assoluto_, ossia il $\lambda$ che minimizza l'errore assoluto tra la soluzione calcolata e quella reale;
- _principio di massima discrepanza_, ossia il $\lambda$ che eguaglia il residuo dei minimi quadrati e il rumore.

Anzitutto, prima di scegliere algoritmicamente il $\lambda$ ottimale, possiamo provare a calcolare la soluzione regolarizzata con $\lambda = 0.5$, e vedere il risultato ottenuto:
```python
x0 = np.zeros_like(x)
maxit = 10000
tolx = 1e-8
tolf = 1e-8
L = operators.Identity()
lmbda = 0.5
ybar_delta = np.pad(y_delta, ((0, 450), (0, 0)))

M = operators.TikhonovOperator(A, L, lmbda)
cgls_tikh_solver = solvers.CGLS(M)
x_tikh = cgls_tikh_solver.solve(ybar_delta, x0, kmax=maxit, tolf=tolf, tolx=tolx)

plt.figure(figsize=(10, 7))
plt.imshow(x_tikh, cmap='gray')
plt.axis('off')
plt.show()
```

<u>Attenzione</u>: la riga `ybar_delta = np.pad(y_delta, ((0, 450), (0, 0)))` serve per estendere l'immagine `y_delta` con degli zeri nella parte inferiore, raddoppiando di fatto la sua altezza. Questo perché la classe `TikhonovOperator` concatena `Ax` con `Lx` verticalmente (`return np.concatenate([Ax, Lx], axis=0)`), per cui _l'operatore/matrice `M` avrà la dimensione dell'altezza raddoppiata rispetto a quella di `y_delta`_.

<u>Nota bene</u>: in questo caso, la _CGLS regolarizzata dovrà uscire obbligatoriamente per tolleranza_, per cui impostiamo un valore di `maxit` (tipo `10000`) tale che ciò avvenga. Per verificare effettivamente che l'algoritmo sia uscito per tolleranza, modifichiamo il codice di `solvers.CGLS()` nel seguente modo:
```python
...
if k < kmax:
	print(f"Algoritmo terminato per condizione su tolx o tolf.")

return x
```
![[calcolo-hw-3-imaging-reg-cgls1.png]]

Effettivamente, $\lambda = 0.5$ è un valore piuttosto alto, che comporta quindi una maggiore regolarizzazione a scapito della fedeltà alla soluzione reale: il risultato è un cambiamento minimo rispetto all'immagine di partenza:
![[calcolo-hw-3-imaging-test3.png]]

Se proviamo adesso a diminuire $\lambda$ a $0.05$, per esempio, dovremmo notare un miglioramento della soluzione calcolata:
![[calcolo-hw-3-imaging-reg-cgls2.png]]

Detto questo, possiamo partire con il calcolo del $\lambda$ ottimale secondo i due criteri sopra citati.

###### Minimo errore assoluto
Per scegliere il $\lambda$ che minimizza l'errore assoluto, possiamo procedere come fatto nell'esercitazione precedente, ossia _calcolando l'errore assoluto al variare di $\lambda$ e scegliendo il minimo_. Per questioni di tempo, limitiamo la ricerca di $\lambda$ nell'intervallo $[0.001, 1]$ per 100 valori:
```python
x0 = np.zeros_like(x)
maxit = 1e+6
tolx = 1e-8
tolf = 1e-8
L = operators.Identity()
lmbdas = np.linspace(0.001, 1, 100)
ybar_delta = np.pad(y_delta, ((0, 450), (0, 0)))

abs_err = []
for lmbda in lmbdas:
	M = operators.TikhonovOperator(A, L, lmbda)
	cgls_tikh_solver = solvers.CGLS(M)
	x_tikh = cgls_tikh_solver.solve(ybar_delta, x0, kmax=maxit, tolf=tolf, tolx=tolx)
	abs_err.append(np.linalg.norm(x_tikh - x))

plt.figure(figsize=(10, 7))
plt.plot(lmbdas, abs_err)
plt.xlabel(r"$\lambda$")
plt.ylabel(r"$||x_{\lambda} - x||_2$")
plt.grid()
plt.show()
```

<u>Nota bene</u>: ho aumentato `maxit` a $10^{6}$ per garantire che l'algoritmo termini per tolleranza su ogni valore di $\lambda$.

Il risultato è il seguente:
![[calcolo-hw-3-imaging-reg-minabs1.png]]

Per cui il $\lambda$ che minimizza l'errore assoluto si trova tra $0$ e $0.1$. Quindi, per ottenere un risultato più preciso, restringiamo l'intervallo di ricerca a $[0, 0.1]$:
![[calcolo-hw-3-imaging-reg-minabs2.png]]

Sembra che il $\lambda$ ottimale sia circa $0.03$. Stampiamo allora il risultato ottenuto con questo valore:
![[calcolo-hw-3-imaging-reg-minabs3.png]]

Se lo confrontiamo con la soluzione naive
![[calcolo-hw-3-imaging-naive3.png]]
e con l'immagine originale
![[calcolo-hw-3-imaging-test1.png]]
possiamo notare meglio l'effetto della regolarizzazione:
- **i contorni sono sicuramente meglio definiti nella soluzione senza regolarizzazione**, infatti le scritte sui cartelli sono più nitide;
- **il rumore è molto meno presente nella soluzione regolarizzata**, infatti la parte inferiore dell'immagine è molto più scura, ergo più simile all'originale;
- nonostante i dettagli siano meno definiti, **nella soluzione regolarizzata** (in quanto meno affetta dal rumore) **la saturazione dei colori è più fedele all'originale** --> sono _più distinguibili i chiari/scuri del cielo_.

Calcoliamo infine le metriche di valutazione:
```python
err_rel = utilities.rel_err(x_tikh, x)
psnr = utilities.psnr(x_tikh, x)
ssim = utilities.ssim(x_tikh, x)

print(f"Relative error: {err_rel}")
print(f"PSNR: {psnr}")
print(f"SSIM: {ssim}")

# Output:
"""
Relative error: 0.1275434011246021
PSNR: 27.293269999775816
SSIM: 0.5326987972710322
"""
```
che confrontate con quelle senza regolarizzazione
```python
"""
Relative error: 0.18023452730385733
PSNR: 24.289670040063285
SSIM: 0.3767979121752091
"""
```
mostrano un **miglioramento significativo**!

###### Principio di massima discrepanza
Procediamo ora con il calcolo del $\lambda$ ottimale secondo il principio di massima discrepanza. Si vuole trovare il $\lambda$ tale che venga rispettata l'uguaglianza
$${\|Ax_{\text{tik}} - y^{\delta}\|_{2}}^{2} = \nu {\|\delta\|_{2}}^{2}$$
dove $\nu$ è una costante di tolleranza, solitamente $1.01$ (o $1.001$).

Dalla teoria sappiamo che quest'uguaglianza esiste ed è rispettata per un solo valore di $\lambda$: in altri termini _la funzione $f(\lambda) = {\|Ax_{\text{tik}} - y^{\delta}\|_{2}}^{2} - \nu {\|\delta\|_{2}}^{2}$ ha un solo zero_. Per trovarlo, possiamo procedere quindi nuovamente con l'algoritmo di bisezione:
```python
...

def bisection(f, a: float, b: float, n: int) -> float:
	c = None
	for _ in range(n):
		c = (a+b) / 2
		if f(a) * f(c) < 0:
			b = c
		else:
			a = c
	return c

...
nu = 1.01
delta_norm = np.linalg.norm(y_delta - y)

def f(lmbda):
	M = operators.TikhonovOperator(A, L, lmbda)
	cgls_tikh_solver = solvers.CGLS(M)
	x_star = cgls_tikh_solver.solve(ybar_delta, x0, kmax=maxit, tolf=tolf, tolx=tolx)
	return np.linalg.norm(A @ x_star - y_delta)**2 - nu * delta_norm**2

lmbda = bisection(f, 0.03, 0.1, 10)
print(lmbda)
M = operators.TikhonovOperator(A, L, lmbda)
cgls_tikh_solver = solvers.CGLS(M)
x_tikh = cgls_tikh_solver.solve(ybar_delta, x0, kmax=maxit, tolf=tolf, tolx=tolx)

plt.figure(figsize=(10, 7))
plt.imshow(x_tikh, cmap='gray')
plt.axis('off')
plt.show()

# Output: 0.035947265624999995
```

<u>Nota bene</u>: mi sono assicurato che $f(0.03) \cdot f(0.1) < 0$.

Quindi, il $\lambda$ ottimale calcolato con il principio di massima discrepanza è $\approx 0.036$. Il risultato ottenuto con questo valore è il seguente:
![[calcolo-hw-3-imaging-reg-maxdisc1.png]]

Come ci aspettavamo dai risultati dell'esperimento precedente, **il $\lambda$ ottenuto con il principio di massima discrepanza è più alto di quello ottenuto con il minimo errore assoluto**.
Si nota, infatti, come _la sfocatura sia più presente, mentre il rumore è meno evidente_.

Non resta che calcolare le metriche di valutazione, per il quale ci aspettiamo che almeno nella PSNR il valore sia più elevato:
```python
"""
Relative error: 0.12854925368007566
PSNR: 27.22503868542981
SSIM: 0.5336362609654446
"""
```
rispetto a quelle ottenute con il minimo errore assoluto:
```python
"""
Relative error: 0.1275434011246021
PSNR: 27.293269999775816
SSIM: 0.5326987972710322
"""
```
e invece non è così! **Il PSNR, nella soluzione calcolata con il principio di massima discrepanza, è leggermente più basso rispetto a quella calcolata con il minimo errore assoluto**. C'è da dire, però, che invece **il SSIM** (indice su cui fare più affidamento) **è leggermente più alto**.

Anche portando $\nu$ a $1.001$ otteniamo un risultato sulle metriche simili.

##### Soluzione regolarizzata con variazione totale
L'altra tecnica molto utilizzata per regolarizzare, in particolare nell'imaging, è la variazione totale. Mentre con Tikhonov si cerca di minimizzare la norma dell'immagine stessa (se $L = I$), **con la variazione totale si vuole minimizzare la norma 1 del suo gradiente**. In particolare, il problema da risolvere diventa:
$$\min_{x} {\|Ax - y^{\delta}\|_{2}}^{2} + \lambda TV^{\beta}(x)$$
dove:
- $TV^{\beta}(x)$ è la **variazione totale dell'immagine $x$** con parametro $\beta$, calcolata come $$TV^{\beta}(x) = \sum\limits_{i=1}^{M}\sum\limits_{j=1}^{N} \sqrt{(x_{i+1,j} - x_{i,j})^{2} + (x_{i,j+1} - x_{i,j})^{2} + \beta^{2}}$$;
- $\lambda$ è il **parametro di regolarizzazione**.

Quindi, $TV(x) = \|\nabla x\|_{1}$, ossia $\sum\limits_{i=1}^{M}\sum\limits_{j=1}^{N} \sqrt{(x_{i+1,j} - x_{i,j})^{2} + (x_{i,j+1} - x_{i,j})^{2}}$: **minimizzare la variazione totale significa minimizzare la somma delle differenze tra pixel adiacenti**. Il parametro $\beta$ è necessario per rendere differenziabile la funzione, e solitamente è nell'ordine di $10^{-3}$.

Il problema regolarizzato può essere risolto, come nel nostro caso, attraverso il [[Metodo di discesa del gradiente|metodo di discesa del gradiente]], che _richiede di conoscere fondamentalmente il gradiente della funzione ${\|Ax - y^{\delta}\|_{2}}^{2} + \lambda TV^{\beta}(x)$_. Lo _step-size_ $\alpha$, solitamente, viene determinato tramite _backtracking_ (secondo le condizioni di Armijo).

<u>Nota bene</u>: la funzione `backtracking` implementata all'interno della classe `GDTotalVariation` ha come condizioni di uscita la **formula errata** `self.f(x - alpha * df, y, lmbda) > self.f(x, y, lmbda) + c * alpha * np.linalg.norm(df) ** 2`, che dovrebbe avere il `-` prima di `c`. Questo errore è stato corretto.

Detto ciò, prima di determinare il valore di $\lambda$ ottimale per la variazione totale (mediante il minimo errore assoluto), possiamo provare a calcolare la soluzione regolarizzata con $\lambda = 0.5$:
```python

```
![[calcolo-hw-3-imaging-reg-tv1.png]]

##### Variazione del rumore
##### Variazione dei parametri della PSF

#### Conclusioni

## Referenze
