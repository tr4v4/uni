---
tags:
  - category/homework
  - status/finished
  - topic/calcolo-numerico
date: 26-12-2024 13:10:40
---
# Calcolo numerico - HW. 3
---
## Esercizi
### Problemi inversi
#### Introduzione
In questo esperimento si vuole, a partire da un [[Problemi inversi|problema inverso]] lineare [[Problema test|test]]:
- visualizzare le _[[Condizioni discrete di Picard|condizioni discrete di Picard]]_;
- calcolare la _soluzione naive_ (con [[Fattorizzazione ai valori singolari|SVD]]) e visualizzarla in un grafico;
- calcolare la _soluzione [[Regolarizzazione|regolarizzata]] con [[Fattorizzazione ai valori singolari troncata|TSVD]]_ e visualizzarla in un grafico (scegliendo il parametro $k$ usando le condizioni discrete di Picard);
- calcolare la _soluzione regolarizzata con [[Regolarizzazione alla Tikhonov|Tikhonov]]_ e visualizzarla in un grafico, scegliendo il parametro $\lambda$ usando il [[Principio di massima discrepanza|principio di massima discrepanza]] e con _trial and error_.

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

Sembra proprio che _per $\lambda = 0.5$ l'errore relativo sia (circa) il minore_.

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

Dal [[#^c90f12|grafico mostrato in precedenza]] **si può notare che per $\lambda = 0.5$ il valore dell'errore relativo è minore che per $\lambda \approx 0.88$**: anzi, **per $\lambda = 0.5$ l'errore relativo è (circa) al minimo globale**.

Questo dimostra che **il principio di massima discrepanza non garantisce, se rispettato, la scelta del parametro di regolarizzazione ottimale**, ma **solo una scelta ragionevole, basata sul rapporto tra dati e rumore**.

##### Variazione del rumore
Per concludere, ripetiamo tutti i passaggi precedenti variando il livello del rumore $\delta$ nell'intervallo $[0, 0.1]$. In particolare, scegliamo i seguenti 4 valori
$$[0, 0.033, 0.066, 0.1]$$
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

Se portiamo $k$ a $4$, invece, cominciano a verificarsi i primi sintomi di approssimazione (soprattutto nella parte iniziale della soluzione):
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

###### Livello $= 0.1$
Concludiamo con il caso in cui il rumore ha un livello pari a $0.1$. Ci si aspetta un "inasprimento" di tutti i fenomeni visti nel caso precedente.

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
e invece non è così! **Il PSNR, nella soluzione calcolata con il principio di massima discrepanza, è leggermente più basso rispetto a quello calcolato con il minimo errore assoluto**. C'è da dire, però, che invece **il SSIM** (indice su cui fare più affidamento) **è leggermente più alto**.

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

Detto ciò, prima di determinare il valore di $\lambda$ ottimale per la variazione totale (mediante il minimo errore assoluto), possiamo provare a calcolare la soluzione regolarizzata con $\lambda = 0.001$:
```python
lmbda = 0.001
beta = 1e-3
x0 = np.zeros_like(x)
maxit = int(1e+6)
tolx = 1e-6
tolf = 1e-6

gd_tv_solver = solvers.GDTotalVariation(A)
x_tv, obj_val, grad_norm = gd_tv_solver.solve(y_delta, lmbda, x0, kmax=maxit, tolf=tolf, tolx=tolx)

plt.figure(figsize=(10, 7))
plt.imshow(x_tv, cmap='gray')
plt.axis('off')
plt.show()
```

<u>Nota bene</u>: è stato necessario aumentare il valore delle tolleranze `tolx` e `tolf` a $10^{-6}$ (da $10^{-8}$) per via della lentissima convergenza del metodo di discesa del gradiente.

La soluzione calcolata è la seguente:
![[calcolo-hw-3-imaging-reg-tv1.png]]

Ricordando che l'immagine posta in input è
![[calcolo-hw-3-imaging-test3.png]]
possiamo notare, come previsto, che _la variazione totale tenda a privilegiare la fedeltà dei contorni_.

Detto ciò, procediamo con il calcolo del $\lambda$ ottimale per la variazione totale, mostrando il grafico dell'errore assoluto al variare di $\lambda$:
```python
lmbdas = np.linspace(1e-5, 1e-4, 100)
beta = 1e-3
x0 = np.zeros_like(x)
maxit = int(1e+6)
tolx = 1e-4
tolf = 1e-4

abs_err = []
for lmbda in lmbdas:
	gd_tv_solver = solvers.GDTotalVariation(A, beta)
	x_tv, obj_val, grad_norm = gd_tv_solver.solve(y_delta, lmbda, x0, kmax=maxit, tolf=tolf, tolx=tolx)
	abs_err.append(np.linalg.norm(x_tv - x))

plt.figure(figsize=(10, 7))
plt.plot(lmbdas, abs_err)
plt.xlabel(r"$\lambda$")
plt.ylabel(r"$\|x_{\lambda} - x\|_2$")
plt.grid()
plt.show()
```

<u>Nota bene</u>: è stata necessaria un'ulteriore riduzione delle tolleranze `tolx` e `tolf` a $10^{-4}$ per garantire una convergenza dell'algoritmo in tempi ragionevoli.

<u>Attenzione</u>: l'intervallo di $\lambda$ scelti $[0.00001, 0.0001]$ è estremamente diverso da quelli scelti per Tikhonov. Purtroppo, infatti, **per valori di $\lambda$ superiori a $\approx 0.004$ il metodo di discesa del gradiente ci mette troppo tempo a convergere**.

Il risultato è il seguente:
![[calcolo-hw-3-imaging-reg-tv2.png]]
il che purtroppo ci mostra che il minimo assoluto non si trova nell'intervallo $[0.00001, 0.0001]$. Tuttavia, l'esecuzione dell'algoritmo per valori di $\lambda$ inferiori, ad esempio $0.000001$, richiede tantissimo tempo per poter uscire con una tolleranza sufficientemente bassa come $10^{-4}$.

Volendo evitare di aumentare ulteriormente la tolleranza (per esempio a $10^{-2}$), possiamo "accontentarci" del risultato per $\lambda = 0.00001$. La soluzione calcolata con esso è la seguente:
```python
lmbda = 1e-5
beta = 1e-3
x0 = np.zeros_like(x)
maxit = int(1e+6)
tolx = 1e-4
tolf = 1e-4

gd_tv_solver = solvers.GDTotalVariation(A, beta)
x_tv, obj_val, grad_norm = gd_tv_solver.solve(y_delta, lmbda, x0, kmax=maxit, tolf=tolf, tolx=tolx)

plt.figure(figsize=(10, 7))
plt.imshow(x_tv, cmap='gray')
plt.axis('off')
plt.show()
```
![[calcolo-hw-3-imaging-reg-tv3.png]]

Le metriche di valutazione per questa soluzione sono le seguenti:
```python
err_rel = utilities.rel_err(x_tv, x)
psnr = utilities.psnr(x_tv, x)
ssim = utilities.ssim(x_tv, x)

print(f"Relative error: {err_rel}")
print(f"PSNR: {psnr}")
print(f"SSIM: {ssim}")

# Output:
"""
Relative error: 0.127673109664017
PSNR: 27.284441149698736
SSIM: 0.5268766011878699
"""
```
che confrontate con quelle ottenute minimizzando l'errore assoluto con Tikhonov:
```python
"""
Relative error: 0.1275434011246021
PSNR: 27.293269999775816
SSIM: 0.5326987972710322
"""
```
sono _leggermente meno buone_.

C'è da notare che probabilmente la minimizzazione dell'errore assoluto non è una tecnica perfetta nell'identificazione del $\lambda$ ottimale. Lo si capisce dal **quantitativo di rumore presente nell'immagine** appena calcolata: **è più evidente rispetto a quella calcolata con Tikhonov** (posta di seguito).
![[calcolo-hw-3-imaging-reg-minabs3.png]]
Infatti la parte inferiore dell'immagine, nel caso della variazione totale, _è sporcata dal rumore_.

Questo è un **effetto che non ci si aspetta dalla variazione totale**, che è conosciuta per la sua efficacia nella rimozione del rumore. Le cause dietro a questo fenomeno possono essere molteplici, in primis _il fatto che l'immagine `y_delta` è decisamente più sfocata che rumorosa_.

Per poter testare meglio la variazione totale, è sufficiente nei paragrafi successivi _aumentare il livello del rumore e diminuire la sfocatura della PSF_.

##### Variazione del rumore
Proviamo quindi adesso a ripetere tutti i passi precedenti variando il livello del rumore su 3 differenti valori nel range $[0, 0.01]$. In particolare scegliamo $0$, $0.0025$ e $0.01$.

Procediamo nel seguente modo: per ogni passaggio variamo il livello del rumore.

###### Soluzione naive
Per il livello $0$, ossia $y^{\delta} = y$, il problema si riduce trivialmente alla risoluzione del sistema lineare
$$Ax = y^{\delta} = y$$
Vale a dire che se consideriamo $A$ come la PSF, e $y$ come il semplice risultato della PSF applicata a $x$, allora _anche la CGLS "naive" (ossia senza regolarizzazione) dovrebbe restituire la soluzione esatta_.

Costruiamo però prima il problema test:
```python
np.random.seed(42)
x = skimage.io.imread("sky-gray.jpg", as_gray=True)

kernel_size = 11
sigma = 3
noise_level = 0

kernel = utilities.gaussian2d_kernel(k=kernel_size, sigma=sigma)
A = operators.ConvolutionOperator(kernel)
y = A(x)
y_delta = y + utilities.gaussian_noise(y, noise_level=noise_level)

plt.figure(figsize=(10, 7))
plt.imshow(y_delta, cmap='gray')
plt.axis('off')
plt.show()
```
![[calcolo-hw-3-imaging-noise1.png]]

Quindi, calcoliamo la soluzione naive come:
```python
x0 = np.zeros_like(x)
maxit = 1000
tolx = 1e-8
tolf = 1e-8

cgls_solver = solvers.CGLS(A)
x_cgls = cgls_solver.solve(y_delta, x0, kmax=maxit, tolf=tolf, tolx=tolx)
```

<u>Nota bene</u>: anche in questo caso `maxit` è stato impostato a `1000` per garantire l'uscita dell'algoritmo in tempi ragionevoli. Tecnicamente _essendo il rumore nullo l'algoritmo uscirebbe tranquillamente anche per tolleranza nulla_, ma il tempo di esecuzione sarebbe troppo lungo...

Il risultato quindi dopo solo 1000 iterazioni è il seguente:
![[calcolo-hw-3-imaging-noise2.png]]

**Praticamente perfetto**! Lo confermano le metriche di valutazione:
```python
"""
Relative error: 0.07619964657064103
PSNR: 31.76737073740737
SSIM: 0.7584309988821635
"""
```

Se aumentiamo il livello del rumore anche solo a $0.0025$, come sappiamo dalla teoria dei problemi inversi, il risultato dovrebbe cambiare drasticamente. L'immagine $y^{\delta}$ diventa:
![[calcolo-hw-3-imaging-noise3.png]]
poco differente dall'immagine senza rumore.
Tuttavia, la soluzione naive calcolata sempre solo per 1000 iterazioni è la seguente:
![[calcolo-hw-3-imaging-noise4.png]]
con metriche di valutazioni pari a:
```python
"""
Relative error: 1.2415889198133696
PSNR: 7.526873313361171
SSIM: 0.09203119916361342
"""
```

Come ci aspettavamo, quindi, **l'aggiunta di un rumore, seppur minimo, ha un impatto significativo sulla qualità della soluzione calcolata**. Tra l'altro la soluzione naive, in questo caso, è troncata a 1000 iterazioni, ma _più iterazioni non farebbero altro che amplificare il rumore_.

Infine, per un livello di rumore $0.01$, l'immagine $y^{\delta}$ è la seguente:
![[calcolo-hw-3-imaging-noise5.png]]

Ci aspettiamo che, all'aumentare del livello del rumore, la qualità della soluzione calcolata senza regolarizzazione (a parità di numero di iterazioni) peggiori:
![[calcolo-hw-3-imaging-noise6.png]]
con metriche di valutazione pari a:
```python
"""
Relative error: 5.139923986868728
PSNR: -4.812704049887618
SSIM: 0.056991245987136285
"""
```

###### Soluzione regolarizzata con Tikhonov
Per la regolarizzazione alla Tikhonov, _per ogni livello del rumore dovremmo calcolare il $\lambda$ che minimizza l'errore assoluto e quello che rispetta il principio di massima discrepanza_.

Partiamo con il livello di rumore $0$. Come abbiamo già potuto notare nel [[Calcolo numerico - HW. 2|secondo homework]], **l'effetto della regolarizzazione può essere estremamente positivo anche in casi in cui**, teoricamente, **non ce ne sarebbe bisogno**.
Per vedere se questo ragionamento si estende anche all'imaging, mostriamo l'andamento degli errori assoluti al variare di $\lambda$ in $[0.001, 1]$:
![[calcolo-hw-3-imaging-noise7.png]]

Il grafico ci conferma che il $\lambda$ ottimale, per problemi inversi che non presentano rumore (ossia sistemi lineari banali), è $0$. Non possiamo verificarlo empiricamente, dati i tempi richiesti per calcolare gli errori assoluti per $\lambda < 0.001$.

In altri termini, **il problema non ha bisogno della regolarizzazione per essere risolto, per cui qualunque valore di $\lambda$ rallenta la convergenza verso la soluzione esatta**.
Tuttavia, se consideriamo come valido $\lambda = 0.001$, la soluzione calcolata è la seguente:
![[calcolo-hw-3-imaging-noise8.png]]
con metriche di valutazione:
```python
"""
Relative error: 0.07305163903314789
PSNR: 32.133830587631195
SSIM: 0.777717690444783
"""
```

Tutte sono, anche se di poco, migliori rispetto a quelle calcolate senza regolarizzazione. Questo miglioramento **non è causato da $\lambda$, ma dal fatto che la soluzione naive è stata troncata dopo 1000 iterazioni, e non è uscita per tolleranza come invece fa la regolarizzazione**. _Se si avesse il tempo di calcolare la soluzione naive tale da farla uscire per tolleranza, il risultato con regolarizzazione produrrebbe sempre risultati peggiori_.

Per quanto riguarda il $\lambda$ che garantisce l'uguaglianza del principio di massima discrepanza, per lo stesso ragionamento, _non ha senso calcolarlo per un livello di rumore nullo_. Infatti questo sarebbe $\lambda = 0$, ossia la soluzione naive.


Portiamo quindi il livello del rumore a $0.0025$. Il grafico dell'errore assoluto al variare di $\lambda$ è il seguente:
![[calcolo-hw-3-imaging-noise9.png]]

In questo caso, quindi, sì che esiste un $\lambda$ ottimale $\neq 0$: $\lambda = 0.011$, che produce come risultato
![[calcolo-hw-3-imaging-noise10.png]]
con metriche di valutazione:
```python
"""
Relative error: 0.11901591070581936
PSNR: 27.894329394095372
SSIM: 0.5532061808744412
"""
```

Ovviamente il risultato è migliore su ogni aspetto della soluzione calcolata in precedenza con livello del rumore $0.005$:
![[calcolo-hw-3-imaging-reg-minabs3.png]]
D'altronde in questo caso il $\lambda$ scelto era ben 3 volte più piccolo.

Sempre per lo stesso livello del rumore, determiniamo adesso il $\lambda$ che rispetta il principio di massima discrepanza. Il risultato dell'algoritmo (omesso in quanto già scritto in precedenza), è $\lambda = 0.023$, che produce l'immagine:
![[calcolo-hw-3-imaging-noise11.png]]
con metriche di valutazione:
```python
"""
Relative error: 0.12083380882361452
PSNR: 27.762660573927022
SSIM: 0.5707912823373233
"""
```

Anche in questo caso, come per quello del livello del rumore $0.005$, _il principio di massima discrepanza sembra produrre un risultato significativamente migliore solo per quanto riguarda la metrica SSIM_.


Infine, portiamo il livello del rumore a $0.01$. Ci aspettiamo, in questo caso, che per entrambi i $\lambda$ calcolati, il loro valore sia tendenzialmente più alto rispetto ai precedenti per poter far fronte al nuovo livello di rumore.
Il grafico dell'errore assoluto al variare di $\lambda$ è il seguente:
![[calcolo-hw-3-imaging-noise12.png]]

Il $\lambda$ che minimizza l'errore assoluto è $\lambda = 0.05$, in effetti maggiore di quello precedente. Questo produce la seguente soluzione:
![[calcolo-hw-3-imaging-noise13.png]]
con metriche di valutazione:
```python
"""
Relative error: 0.1343265973599103
PSNR: 26.843189602714613
SSIM: 0.49962643781642013
"""
```

Invece, il $\lambda$ che rispetta il principio di massima discrepanza è $\lambda = 0.053$, che produce la seguente soluzione:
![[calcolo-hw-3-imaging-noise14.png]]
con metriche di valutazione:
```python
"""
Relative error: 0.1343696604455208
PSNR: 26.84040548346156
SSIM: 0.5017667571437991
"""
```

Curiosamente, in questo caso _il $\lambda$ ottimale calcolato con il principio di massima discrepanza è molto simile a quello calcolato minimizzando l'errore assoluto_.

###### Soluzione regolarizzata con variazione totale
Infine, proviamo a calcolare la soluzione regolarizzata con variazione totale per i 3 livelli di rumore.

Per il livello $0$, ci aspettiamo come per Tikhonov che il $\lambda$ ottimale sia $0$.
![[calcolo-hw-3-imaging-noise15.png]]

In effetti, vale la regola $\lambda \to 0 \implies err_{abs} \to 0$. Se consideriamo $\lambda = 0.0001$ come quello ottimale, la soluzione calcolata è la seguente:
![[calcolo-hw-3-imaging-noise16.png]]
con metriche di valutazione:
```python
"""
Relative error: 0.13665610279035226
PSNR: 26.69384925355249
SSIM: 0.5017781480832492
"""
```

Introducendo il livello di rumore $0.0025$, il grafico dell'errore assoluto al variare di $\lambda$ è il seguente:
![[calcolo-hw-3-imaging-noise17.png]]

Anche in questo caso, il $\lambda$ ottimale non rientra nell'intervallo di riferimento, e sarebbe troppo costoso eseguire l'algoritmo per $\lambda$ più piccoli. Per cui, di fatto, _risulta che il $\lambda$ ottimale è lo stesso del caso senza rumore_, ovvero $\lambda = 0.0001$... Ovviamente non è questa la realtà dei fatti, ma _gli strumenti a mia disposizione mi impediscono di ottenere risultati in tempi accettabili_.

Possiamo sperare solo nel caso in cui il livello del rumore sia $0.01$, ipotizzando che per regolarizzare sia necessario un valore di $\lambda > 0.0001$. Il grafico dell'errore assoluto al variare di $\lambda$ è il seguente:
![[calcolo-hw-3-imaging-noise18.png]]

Niente... neanche in questo caso riusciamo a catturare il $\lambda$ che minimizza l'errore assoluto per la variazione totale. Quindi, vale sempre $\lambda = 0.0001$, ossia la stessa soluzione calcolata con rumore nullo e con rumore a $0.0025$.

Viene il dubbio che, a questo punto, sia la variazione totale ad essere sbagliata in qualche sua parte: _magari la tendenza di quella curva suggerisce che l'errore assoluto minimo si abbia per $\lambda = 0$_. Non è però questo il caso. Infatti la stessa ricerca del $\lambda$ ottimale sull'immagine con livello di rumore pari a $0.1$, si ottiene un grafico ben diverso:
![[calcolo-hw-3-imaging-noise19.png]]

Questo significa fondamentalmente che **la variazione totale è molto meno sensibile al rumore rispetto alla regolarizzazione di Tikhonov**. E' solo su rumori molto alti che la variazione totale richiede un $\lambda$ maggiore per poter regolarizzare.

##### Variazione dei parametri della PSF
Visto il comportamento dei vari metodi al variare del livello del rumore, è arrivato il momento di testarli modificando i parametri della PSF. In particolare, questi sono:
- `kernel_size`, per ora $11$;
- `sigma`, per ora $3$.

Il primo identifica la dimensione del _kernel di sfocatura_, ossia della matrice di convoluzione che rappresenta la PSF; il secondo, invece, rappresenta la _deviazione standard_ della gaussiana che genera il kernel, ossia la _"quantità" di sfocatura_.

Per comprendere meglio la funzione di questi parametri, visualizziamo il kernel con i valori standard (rispettivamente $11$ e $3$):
```python
kernel_size = 11
sigma = 3

kernel = utilities.gaussian2d_kernel(k=kernel_size, sigma=sigma)

plt.figure(figsize=(10, 7))
plt.imshow(kernel, cmap='hot')
plt.axis('off')
plt.show()
```
![[calcolo-hw-3-imaging-psf1.png]]

L'immagine mostra _il livello di sfocatura che viene applicato ad ogni singolo pixel dell'immagine originale_: il valore di ogni pixel diventa la somma dei valori dei $\frac{11-1}{2} = 5$ pixel adiacenti moltiplicati per i valori del kernel, che seguono una distribuzione gaussiana, causando un effetto di sfocatura. Il livello di distribuzione della sfocatura è determinato dal valore di `sigma`.

Quindi:
- **più il `kernel_size` è alto, più la sfocatura è estesa**;
- **più il `sigma` è alto, più la sfocatura è intensa**.

Se infatti proviamo ad aumentare `kernel_size` a $21$, otteniamo il seguente kernel:
![[calcolo-hw-3-imaging-psf2.png]]
tale che _il pixel centrale **sarà influenzato da più** pixel adiacenti_.

E se invece aumentiamo `sigma` a $5$, otteniamo il seguente kernel:
![[calcolo-hw-3-imaging-psf3.png]]
tale che _il pixel centrale **sarà più influenzato dai** pixel adiacenti_.

In generale possiamo dire che **se si aumentano entrambi i parametri, il risultato sarà un'immagine maggiormente sfuocata**, e viceversa **se si diminuiscono entrambi i parametri, il risultato sarà un'immagine meno sfuocata**.

L'immagine di partenza, con `kernel_size = 11` e `sigma = 3`, presentava un livello di sfocatura particolarmente alto:
![[calcolo-hw-3-imaging-test3.png]]

Per cui come primo passo riduciamo la dimensione del kernel a $5$ e la deviazione standard a $1$; come secondo passo, invece, tentiamo di recuperare informazioni da un'immagine estremamente sfocata, con `kernel_size = 21` e `sigma = 5`.
Ricapitolando:
1. `kernel_size = 5`, `sigma = 1` --> ![[calcolo-hw-3-imaging-psf4.png]]
2. `kernel_size = 21`, `sigma = 5` --> ![[calcolo-hw-3-imaging-psf5.png]]

<u>Nota bene</u>: il livello del rumore è stato ripristinato a $0.005$.

###### Soluzione naive
Per quanto riguarda il primo caso, anche se la sfocatura è minore il rumore è sempre presente: _ci aspettiamo che la soluzione naive si corrompa all'aumentare delle iterazioni_.
Se proviamo fissando `maxit = 30`, otteniamo:
![[calcolo-hw-3-imaging-psf6.png]]
un risultato estremamente buono, con metriche di valutazione ottime:
```python
"""
Relative error: 0.06363315642211945
PSNR: 33.33276055214781
SSIM: 0.7693311558437717
"""
```

Tuttavia, già ponendo `maxit = 100`, si cominciano a vedere i segni del rumore:
![[calcolo-hw-3-imaging-psf7.png]]
lo si capisce dall'omogeneizzazione dei colori, e ovviamente dall'abbassamento dei valori delle metriche:
```python
"""
Relative error: 0.15818522394529452
PSNR: 25.4231116037218
SSIM: 0.5259779850327585
"""
```

Chiaramente, per 1000 iterazioni il risultato è ancora peggiore:
![[calcolo-hw-3-imaging-psf8.png]]
(ometto le metriche).

Per quanto riguarda il secondo caso, ci aspettiamo un generale abbassamento delle metriche di valutazione. Infatti **ci vogliono più iterazioni per "deblurrare", ma più iterazioni significano più rumore**. Di fatti, con `maxit = 30` otteniamo:
![[calcolo-hw-3-imaging-psf9.png]]
con metriche di valutazione:
```python
"""
Relative error: 0.14805558608012087
PSNR: 25.997933921428917
SSIM: 0.43148530222006953
"""
```

Per `maxit = 100`:
![[calcolo-hw-3-imaging-psf10.png]]
con metriche di valutazione peggiorate:
```python
"""
Relative error: 0.1779464479039951
PSNR: 24.400643413117557
SSIM: 0.3209416799752856
"""
```

E infine, per `maxit = 1000`:
![[calcolo-hw-3-imaging-psf11.png]]
(ometto le metriche).

###### Soluzione regolarizzata con Tikhonov
Ancora una volta, _per ogni caso di PSF dovremmo cercare il $\lambda$ che minimizza l'errore assoluto e quello che rispetta il principio di massima discrepanza_.

Partendo dal primo, il grafico dell'errore assoluto al variare di $\lambda$ appare come:
![[calcolo-hw-3-imaging-psf12.png]]

Il $\lambda$ ottimale, in particolare, risulta essere $\lambda = 0.051$. La soluzione calcolata con esso è la seguente:
![[calcolo-hw-3-imaging-psf13.png]]
con metriche di valutazione:
```python
"""
Relative error: 0.060320989480786014
PSNR: 33.7970607392052
SSIM: 0.7901986272726474
"""
```

Si tratta a tutti gli effetti del **risultato migliore ottenuto finora**. C'è da notare che il $\lambda$ ottenuto è maggiore di quello calcolato con la PSF standard e stesso livello del rumore (era $0.03$): questo probabilmente perché essendo la sfocatura minore, _il rumore è più evidente e quindi serve un $\lambda$ maggiore per regolarizzare_.

Il $\lambda$ ottimale che rispetta il principio di massima discrepanza, invece, è $\lambda = 0.055$, che produce la soluzione:
![[calcolo-hw-3-imaging-psf14.png]]
con metriche di valutazione:
```python
"""
Relative error: 0.06081279758775622
PSNR: 33.726530220580656
SSIM: 0.791854248482379
"""
```

Come sempre, _il risultato ottenuto con il principio di massima discrepanza è leggermente migliore solo per quanto riguarda il SSIM_.


Per il secondo caso, il grafico dell'errore assoluto al variare di $\lambda$ dovrebbe, al contrario, presentare un $\lambda$ ottimale minore rispetto al caso precedente. Questo perché _la sfocatura è maggiore, e quindi il rumore è meno evidente_. Il grafico è il seguente:
![[calcolo-hw-3-imaging-psf15.png]]

Di fatti, il $\lambda$ ottimale è $\lambda = 0.021$, che produce la soluzione:
![[calcolo-hw-3-imaging-psf16.png]]
con metriche di valutazione:
```python
"""
Relative error: 0.145494534783263
PSNR: 26.149496273217693
SSIM: 0.4279730007692543
"""
```

Il $\lambda$ ottimale che rispetta il principio di massima discrepanza, invece, è $\lambda = 0.0276$, che produce la soluzione:
![[calcolo-hw-3-imaging-psf17.png]]
con metriche di valutazione:
```python
"""
Relative error: 0.14627854357557848
PSNR: 26.102817324815817
SSIM: 0.43352510042036735
"""
```

Ancora una volta, _il risultato ottenuto con il principio di massima discrepanza è migliore solo per il SSIM_.

###### Soluzione regolarizzata con variazione totale
Infine, proviamo a calcolare la soluzione regolarizzata con variazione totale per i 2 diversi parametri della PSF.

Partendo dal primo caso, mostriamo il grafico dell'errore assoluto al variare di $\lambda$:
![[calcolo-hw-3-imaging-psf18.png]]

Ovviamente il minimo è inferiore per $\lambda < 0.0001$. Non approfondiamo la ricerca su $\lambda$ minori, ma come già fatto consideriamo come ottimale $\lambda = 0.0001$. La soluzione calcolata con esso è la seguente:
![[calcolo-hw-3-imaging-psf19.png]]
con metriche di valutazione:
```python
"""
Relative error: 0.06608012869039775
PSNR: 33.00501227543421
SSIM: 0.7854447272677959
"""
```

Il risultato è simile a quello ottenuto, nello stesso caso di PSF, con Tikhonov, anche se leggermente inferiori.


Per il secondo caso, il grafico dell'errore assoluto al variare di $\lambda$ è il seguente:
![[calcolo-hw-3-imaging-psf20.png]]

C'è da notare, ovviamente, che in generale gli errori assoluti sono più alti. Il $\lambda$ "ottimale", è sempre $\lambda = 0.0001$, che produce stavolta la soluzione:
![[calcolo-hw-3-imaging-psf21.png]]
con metriche di valutazione:
```python
"""
Relative error: 0.15114575555675583
PSNR: 25.818510759001732
SSIM: 0.42453481015915107
"""
```

#### Confronti
Per concludere, si vogliono raccogliere i risultati ottenuti per mostrare, attraverso opportuni grafici, pregi e difetti delle tecniche studiate nell'imaging, al variare del livello del rumore e dei parametri della PSF.

Nella fattispecie, per ogni caso di studio, confrontiamo le metriche di valutazione ottenute con:
- la _soluzione naive_;
- la _soluzione regolarizzata con Tikhonov_ (minimizzando l'errore assoluto e rispettando il principio di massima discrepanza);
- la _soluzione regolarizzata con variazione totale_ (minimizzando l'errore assoluto).

Per ognuna delle 3 tecniche, ovviamente, selezioniamo il $\lambda$ ottimale (per la naive, invece, sempre 1000 iterazioni).

Per quanto riguarda i **livelli del rumore**, se consideriamo i 4 valori studianti $0, 0.0025, 0.005, 0.01$, i risultati sono i seguenti:
![[calcolo-hw-3-imaging-comparison1.png]]
![[calcolo-hw-3-imaging-comparison2.png]]
![[calcolo-hw-3-imaging-comparison3.png]]

<u>Attenzione</u>: i **valori della variazione totale**, come già anticipato, in realtà **non sono "validi"**. I $\lambda$ calcolati non sono quelli ottimali, per cui **i risultati ottenuti non sono attendibili**.

Possiamo trarre le seguenti osservazioni:
- la **soluzione naive, all'aumentare del livello del rumore, peggiora drasticamente**, secondo tutti gli indici di valutazione;
- le **soluzioni regolarizzate, all'aumentare del livello del rumore, peggiorano ma mantenendo una certa stabilità**;
- ma soprattutto, **secondo l'errore relativo e il PSNR** la regolarizzazione alla Tikhonov secondo **minimizzazione dell'errore assoluto è la migliore in assoluto**, mentre la **SSIM** valuta come **migliore quella secondo il principio di massima discrepanza**.

Per quanto riguarda i **parametri della PSF**, se consideriamo le 3 coppie di valori studiate $(5, 1), (11, 3), (21, 5)$, i risultati sono i seguenti:
![[calcolo-hw-3-imaging-comparison4.png]]
![[calcolo-hw-3-imaging-comparison5.png]]
![[calcolo-hw-3-imaging-comparison6.png]]

Anche in questo caso **i valori della variazione totale non sono attendibili**.

Possiamo trarre le seguente osservazione:
- anche variando i parametri della PSF, la **SSIM valuta sempre meglio la regolarizzazione alla Tikhonov secondo il principio di massima discrepanza**, mentre **l'errore relativo e il PSNR valutano sempre meglio la regolarizzazione alla Tikhonov secondo minimizzazione dell'errore assoluto**;
- invece, per quanto riguarda la **soluzione naive**, si osserva un fenomeno interessante --> **l'andamento delle metriche non è monotono**, e in particolare **tutte e 3 raggiungono un picco negativo** (minimo o massimo a seconda della metrica) **per la PSF $(11, 3)$**, **mentre per gli altri due casi presentano valori migliori**; questo **probabilmente è causato dal bilanciamento tra sfocatura e rumore della configurazione $(11, 3)$**, tale che _per valori più bassi di sfocatura sia più facile per la soluzione naive "deblurrare" l'immagine senza amplificare il rumore, mentre che per valori più alti il rumore sia meno evidente rispetto alla sfocatura e quindi il risultato ottenuto sia migliore_.

#### Conclusioni
In conclusione, in questo esperimento abbiamo potuto osservare l'_effetto della regolarizzazione in problemi di imaging_ e del _loro comportamento al variare del livello del rumore e dei parametri della PSF_.

In particolare, abbiamo notato una differenza sostanziale tra i due tipi di regolarizzazione alla Tikhonov: **minimizzare l'errore assoluto è più efficace per l'errore relativo e il PSNR**, mentre **rispettare il principio di massima discrepanza è più efficace per la SSIM**.

Inoltre, abbiamo osservato che **la variazione totale è meno sensibile al rumore rispetto alla regolarizzazione di Tikhonov**, e che, quindi, per livelli di rumore molto bassi ci vorrebbero dei $\lambda$ estremamente piccoli per minimizzare l'errore assoluto.

Infine, abbiamo congetturato alcune ragioni dietro al fatto che **le metriche di valutazione della soluzione naive, al variare dei parametri della PSF, possano comportarsi in modo non monotono**.

## Referenze
