---
tags:
  - category/homework
  - status/finished
  - topic/calcolo-numerico
date: 07-12-2024 15:01:20
---
# Calcolo numerico - HW. 2
---
## Esercizi
### Approssimazione
#### Introduzione
In questo esperimento si vogliono applicare le tecniche di [[Approssimazione di dati|approssimazione di dati]] studiate su un [[Problema test|problema test]] di cui (almeno inizialmente) non si conoscono gli _iperparametri_ esatti.

In particolare, caricato il _dataset_ e fatte delle stime sul polinomio approssimante $f$ (e in particolare sul suo grado $d$), si vogliono trovare i coefficienti $\alpha$ risolvendo ai [[Approssimazione ai minimi quadrati|minimi quadrati]] mediante [[Fattorizzazione di Cholesky|Cholesky]], [[Fattorizzazione ai valori singolari|SVD]] e [[CGLS]], e poi applicare tecniche di [[Regolarizzazione|regolarizzazione]] ([[Regolarizzazione alla Tikhonov|Tikhonov]]) per risolvere l'[[Overfit|overfit]] per un certo grado $d$ ($=6$).

Infine, svelati gli iperparametri e i parametri esatti, si vogliono confrontare i risultati ottenuti con quelli reali, _calcolando gli errori relativi_.

#### Sviluppo
##### Stime
Attraverso il seguente codice andiamo ad estrapolare i vettori $x$ e $y$ dal file `data_hw.csv`, usando la libreria `pandas`, e visualizziamo i punti $(x_{i}, y_{i}) \ \ i=1, \cdots, n$ su un grafico con `matplotlib`.
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

data_path = "./data_hw.csv"
dataset = pd.read_csv(data_path)
x = np.array(dataset["x"])
y = np.array(dataset["y"])

plt.plot(x, y, 'bo')
plt.xlabel(r"$x$")
plt.ylabel(r"$y$")
plt.grid()
plt.show()
```
![[calcolo-hw-2-approx-stime.png]]

E' possibile osservare che l'andamento dei dati, seppur complesso, sembra coerente con quello di una **[[Polinomio|funzione polinomiale]] di 4° grado, con coefficiente $a_{4}$ negativo**:
- _sembrano esserci 3 picchi di funzione_ (un massimo su $0.2$, un minimo/flesso su $0.4$ e un ultimo massimo su $0.8$) --> se assumiamo che si tratti di un polinomio, la potenza minima per poter sostenere 3 picchi (e quindi il suo grado minimo), dev'essere 4;
- _la curva sembra essere concava_ (rivolta verso il basso) --> se assumiamo che si tratti di un polinomio di grado pari, allora il coefficiente della potenza di $x$ più alta dev'essere negativo.

Chiaramente _si tratta di stime fatte esclusivamente sulla base del grafico_, per cui è possibile che siano errate. E questo non dipende solo dal grado sconosciuto del polinomio; anzi, non conoscendo a priori il valore della _varianza $\sigma$_ con cui sono stati prodotti i dati, _$f$ potrebbe essere anche una retta_!

##### Minimi quadrati
Impostiamo allora il problema ai minimi quadrati, scegliendo $d=4$ e codificando in codice Python il problema di ottimizzazione
$$\min_{\alpha \in \mathbb{R}^{d+1}} {\|X \alpha - y\|_{2}}^{2}$$
dove:
- $\alpha \in \mathbb{R}^{d+1}$ rappresenta il vettore $(a_{0}, \cdots, a_{d})$ dei coefficienti;
- $X \in \mathbb{R}^{n \times (d+1)}$ è la [[Matrice di Vandermonde|matrice di Vandermonde]], ovvero la matrice del tipo $\begin{bmatrix}x_{1}^{0} & \cdots & x_{1}^{d} \\ \vdots & \ddots & \vdots \\ x_{n}^{0} & \cdots & x_{n}^{d} \end{bmatrix}$;
- $y \in \mathbb{R}^{n}$ rappresenta la colonna dei termini noti $(y_{1}, \cdots, y_{n})$.

In codice:
```python
d = 4
X = np.vander(x, d+1, increasing=True)
```

Per completezza, verifichiamo il [[Numero di condizione|numero di condizione]] di $X$:
```python
print(np.linalg.cond(X))

# Output: 642.6673571219791
```

Non è basso, e in più se aumento il valore di $d$ tende a salire esponenzialmente. C'è una spiegazione: _la matrice di Vandermonde è costruita come una sorta di [[Matrice di Hilbert|matrice di Hilbert]] riflessa sulla diagonale secondaria_, ossia con valori che (esclusa la prima colonna composta da soli 1) partono dal basso e crescono su ogni diagonale. E' possibile (non ho gli strumenti matematici per verificarlo), che sia questa somiglianza a determinare il fenomeno. Ad ogni modo manteniamo il grado del polinomio approssimante in un range che va da $0$ a $8$, per cui non ci dovrebbero essere problemi legati al malcondizionamento della matrice.

Possiamo quindi procedere con la risoluzione del problema passando alle _equazioni normali_
$$X^{T}X \alpha = X^{T}y$$

###### Cholesky
Possiamo usare la decomposizione di Cholesky sul sistema delle equazioni normali a patto che _$X$ abbia rango massimo_: sapendo che $n \gg d+1$, allora il rango massimo di $X$ è $rk(X) = d+1$. Per verificare ciò usiamo la funzione `numpy.linalg.matrix_rank()`:
```python
print(np.linalg.matrix_rank(X) == d+1)

# Output: True
```

Quindi definiamo la funzione che risolve un sistema lineare usando la fattorizzazione di Cholesky
```python
def solve_linear_system_chol(A: np.ndarray, b: np.ndarray) -> np.ndarray:
	L = np.linalg.cholesky(A)
	y = np.linalg.solve(L, b)
	x = np.linalg.solve(L.T, y)
	return x
```
e la invochiamo su $X^{T}X$ e $X^{T}y$, tenendo traccia del tempo impiegato:
```python
import time

start = time.time()
alpha_chol = solve_linear_system_chol(X.T @ X, X.T @ y)
end = time.time()
print(f"{alpha_chol}\nCalcolato in {end-start} secondi")

# Output:
"""
[ -0.16232963   3.24903618  -7.85010467  17.03510471 -11.51696295]
Calcolato in 0.00015687942504882812 secondi
"""
```

Reiterando un po' di volte il codice **il tempo impiegato è rimasto nell'ordine di $10^{-4}$ secondi**.
Verifichiamo la correttezza della soluzione plottando il grafico del polinomio descritto da dai coefficienti `alpha_chol`, usando la funzione `numpy.polyval()`:
```python
n = 50
x_chol = np.linspace(0, 1, n)
y_chol = np.polyval(alpha_chol[: : -1], x_chol)

plt.plot(x, y, 'bo')
plt.plot(x_chol, y_chol, 'r-')
plt.xlabel(r"$x$")
plt.ylabel(r"$y$")
plt.legend(["dataset", "Cholesky"])
plt.grid()
plt.show()
```

<u>Nota bene</u>: nella funzione `polyval` _devo passare `alpha_chol` invertito_ (tramite `[: : -1]`) perché moltiplica, per ogni `x` appartenente a `x_chol`, i coefficienti $\alpha$ partendo dalla potenza più alta ($x^{4}, x^{3}, \cdots, x, 1$), mentre `alpha_chol` va dal coefficiente per $1$ fino a quello per $x^{4}$.

Ad ogni modo, il grafico risultante è il seguente:
![[calcolo-hw-2-approx-chol.png]]

###### SVD
Per risolvere il problema dei minimi quadrati tramite decomposizione ai valori singolari, è sufficiente, una volta decomposta $X$ in $U \Sigma V^{T}$, calcolare $\alpha$ secondo la sommatoria
$$\alpha = \sum\limits_{i=1}^{k} \frac{u_{i}^{T} y}{\sigma_{i}}v_{i}$$
con $k = rk(X)$.
In codice è sufficiente definire una funzione `solve_least_squared_svd()` che restituisca il valore di tale sommatoria
```python
def solve_least_squared_svd(X: np.ndarray, y: np.ndarray) -> np.ndarray:
	U, s, VT = np.linalg.svd(X)
	return sum(((U[:, i].T @ y) / s[i]) * VT[i, :] for i in range(np.linalg.matrix_rank(X)))
```
e di invocarla su $X$ e $y$, tenendo conto del tempo:
```python
start = time.time()
alpha_svd = solve_least_squared_svd(X, y)
end = time.time()
print(f"{alpha_svd}\nCalcolato in {end-start} secondi")

n = 50
x_svd = np.linspace(0, 1, n)
y_svd = np.polyval(alpha_svd[::-1], x_svd)

plt.plot(x, y, 'bo')
plt.plot(x_svd, y_svd, 'g-')
plt.xlabel(r"$x$")
plt.ylabel(r"$y$")
plt.legend(["dataset", "SVD"])
plt.grid()
plt.show()

# Output:
"""
[ -0.16232963   3.24903618  -7.85010467  17.03510471 -11.51696295]
Calcolato in 0.0005121231079101562 secondi
"""
```

<u>Nota bene</u>: **ci mette 5 volte tanto Cholesky**! E il risultato è il medesimo.

Il grafico prodotto è il seguente:
![[calcolo-hw-2-approx-svd.png]]

###### CGLS
La CGLS, a differenza dei due precedenti metodi, **risolve i minimi quadrati in modo iterativo, e non diretto**. Si tratta di fatto dell'applicazione della [[Metodo dei gradienti coniugati|discesa dei gradienti coniugati]] (a sua volta una forma del [[Metodo di discesa del gradiente|metodo di discesa del gradiente]]) nella ricerca dei minimi quadrati, e quindi di un [[Algoritmo iterativo|algoritmo iterativo]] che necessita di specifici criteri di arresto.

In particolare, l'algoritmo prevede di specificare il numero massimo di iterazioni `maxit`, e un valore di tolleranza `tol` tale che l'algoritmo termini se
$$\|r_{k}\|_{2} < \text{tol} \cdot \|r_{0}\|_{2}$$
dove:
- $r_{k}$ è il residuo alla $k$-esima iterazione;
- $r_{0}$ è il residuo iniziale ($A^{T}(y - Ax_{0})$).

Tra le più importanti proprietà dell'algoritmo, sia ha quello della convergenza: **se $X \in \mathbb{R}^{n \times (d+1)}$, allora l'algoritmo convergerà alla soluzione esatta del problema ai minimi quadrati in al massimo $d+1$ iterazioni**. E considerando che il valore del grado del polinomio è estremamente basso ($4$), _abbiamo la certezza teorica che in $5$ iterazioni l'algoritmo convergerà alla soluzione esatta_.

L'algoritmo è implementato dalla seguente funzione:
```python
def cgls(A, y, tol=1e-5, maxit=100):
    # Inizializzazione
    x = np.zeros(A.shape[1])  # x0 = 0
    r = r0 = A.T @ (y - A @ x)     # residuo iniziale
    p = r.copy()              # direzione iniziale
    
    for k in range(maxit):
        # Calcolo valori richiesti
        q = A @ p
        alpha = np.linalg.norm(r)**2 / np.linalg.norm(q)**2

        # Aggiornamento di x e di r
        x = x + alpha * p
        r_new = r - alpha * A.T @ q
        
        # Criterio di arresto
        if np.linalg.norm(r_new) < tol * np.linalg.norm(r0):
            print(f'Convergenza raggiunta in {k+1} iterazioni.')
            break
        
        # Aggiornamento dei parametri
        beta = np.linalg.norm(r_new)**2 / np.linalg.norm(r)**2
        p = r_new + beta * p
        r = r_new
    
    return x
```

Non ci resta che richiamarlo su $X$, $y$ e specificando `tol=1e-9` (per ottenere la stessa precisione delle soluzioni precedenti) e `maxit = 10` (per ora):
```python
start = time.time()
alpha_cgls = cgls(X, y, tol=1e-9, maxit=10)
end = time.time()
print(f"{alpha_cgls}\nCalcolato in {end-start} secondi")

n = 50
x_cgls = np.linspace(0, 1, n)
y_cgls = np.polyval(alpha_cgls[::-1], x_cgls)

plt.plot(x, y, 'bo')
plt.plot(x_cgls, y_cgls, 'y-')
plt.xlabel(r"$x$")
plt.ylabel(r"$y$")
plt.legend(["dataset", "CGLS"])
plt.grid()
plt.show()

# Output:
"""
Convergenza raggiunta in 7 iterazioni.
[ -0.16232963   3.24903618  -7.85010467  17.03510471 -11.51696295]
Calcolato in 0.00021910667419433594 secondi
"""
```

Ci aspettavamo che la convergenza avvenisse in al massimo $5$ iterazioni, e _invece ce ne sono volute $7$ per raggiungere la soluzione esatta_. Il motivo è dovuto a piccole perturbazioni generate da [[Errore di arrotondamento|errori di arrotondamento]] e propagati come [[Errore algoritmico|errori algoritmici]], che **spostano anche di pochissimo le "direzioni coniugate" causando un "ritardo" nella convergenza**[^1].

Detto questo, la soluzione è stata calcolata correttamente, in **circa il doppio del tempo impiegato da Cholesky**. Il grafico prodotto è il seguente:
![[calcolo-hw-2-approx-cgls.png]]

Notare che se aumentassi la tolleranza dell'algoritmo, la convergenza richiederebbe meno iterazioni, ma il risultato sarebbe meno preciso. Per esempio, _se aumento la tolleranza a `1e-3`, l'algoritmo raggiunge la convergenza in 4 iterazioni_, producendo come grafico:
![[calcolo-hw-2-approx-cgls-2.png]]

###### Confronti
Non ci rimane che confrontare i risultati dei 3 algoritmi. Sappiamo in realtà che i valori dei coefficienti ottenuti sono identici, per cui ci aspettiamo 3 funzioni sovrapposte.
```python
n = 50
xx = np.linspace(0, 1, n)

start = time.time()
alpha_chol = solve_linear_system_chol(X.T @ X, X.T @ y)
end = time.time()
print(f"Cholesky: {alpha_chol}\nCalcolato in {end-start} secondi\n")
y_chol = np.polyval(alpha_chol[: : -1], xx)

start = time.time()
alpha_svd = solve_least_squared_svd(X, y)
end = time.time()
print(f"SVD: {alpha_svd}\nCalcolato in {end-start} secondi\n")
y_svd = np.polyval(alpha_svd[: : -1], xx)

start = time.time()
alpha_cgls = cgls(X, y, tol=1e-9, maxit=10)
end = time.time()
print(f"CGLS: {alpha_cgls}\nCalcolato in {end-start} secondi")
y_cgls = np.polyval(alpha_cgls[: : -1], xx)

plt.plot(x, y, 'bo')
plt.plot(xx, y_chol, 'r-')
plt.plot(xx, y_svd, 'g-')
plt.plot(xx, y_cgls, 'y-')
plt.xlabel(r"$x$")
plt.ylabel(r"$y$")
plt.legend(["dataset", "Cholesky", "SVD", "CGLS"])
plt.grid()
plt.show()

# Output
"""
Cholesky: [ -0.16232963   3.24903618  -7.85010467  17.03510471 -11.51696295]
Calcolato in 0.00011277198791503906 secondi

SVD: [ -0.16232963   3.24903618  -7.85010467  17.03510471 -11.51696295]
Calcolato in 0.0003399848937988281 secondi

Convergenza raggiunta in 7 iterazioni.
CGLS: [ -0.16232963   3.24903618  -7.85010467  17.03510471 -11.51696295]
Calcolato in 0.00022530555725097656 secondi
"""
```
![[calcolo-hw-2-approx-confronti.png]]

Per quanto riguarda i tempi, in ordine di velocità si ha:
1. _Cholesky_ --> $1 \times 10^{-4}$;
2. _CGLS_ --> $[3,5] \times 10^{-4}$;
3. _SVD_ --> $[1, 2] \times 10^{-4}$.

###### $d$ variabile
Proviamo adesso a ripetere i passaggi precedenti variando il grado del polinomio approssimante in un range da $0$ a $8$. In particolare, visualizzeremo 9 grafici ognuno dei quali plotterà il risultato dell'approssimazione dei tre metodi sulla base del valore di $d$; quindi un unico grafico finale in merito ai tempi di esecuzione dei metodi al variare di $d$.

Per $d = 0$, ci aspettiamo 3 rette parallele all'ascisse $x$ cui altezza è la media dei valori $y_{i} \ \ i = 1, \cdots, n$:
![[calcolo-hw-2-approx-d0.png]]

Per $d=1$, ci aspettiamo una _regressione lineare_:
![[calcolo-hw-2-approx-d1.png]]

Per $d=2$:
![[calcolo-hw-2-approx-d2.png]]

Per $d=3$:
![[calcolo-hw-2-approx-d3.png]]

Per $d=4$:
![[calcolo-hw-2-approx-d4.png]]

Per $d=5$:
![[calcolo-hw-2-approx-d5.png]]

Per $d=6$, _il polinomio approssimante comincia ad essere influenzato dal rumore_:
![[calcolo-hw-2-approx-d6.png]]

Per $d=7$:
![[calcolo-hw-2-approx-d7.png]]

Per $d=8$:
![[calcolo-hw-2-approx-d8.png]]

Possiamo concludere che _il polinomio che meglio approssima i dati è, come già avevamo stimato essere, quello di grado 4_. I precedenti non sono sufficientemente precisi; i successivi [[Interpolazione|interpolano]] il rumore. Anche quello di 5° grado, tuttavia, sembra piuttosto accettabile.

Per concludere questa sezione, mostriamo i tempi di esecuzione dei tre algoritmi al variare di $d$:
![[calcolo-hw-2-approx-tempi.png]]

Osserviamo che:
- _Cholesky rimane il metodo più veloce_, senza considerare il caso banale $d = 0$;
- _SVD impiega sempre almeno il doppio del tempo di Cholesky_;
- _CGLS tende a crescere esponenzialmente in tempo di esecuzione_, se si assume di voler mantenere la stessa tolleranza (infatti ho posto `maxit=100`).

Tuttavia:
- **la velocità di Cholesky si paga in malcondizionamento**, e già ponendo $d=12$ il malcondizionamento di $X^{T}X$ è tale da non risultare neanche definita positiva, rendendo il metodo inapplicabile;
- **l'SVD, seppure più lenta di Cholesky, si può usare sempre**, ma comincia a diventare un problema per matrici troppo grandi;
- **la lentezza della CGLS premia in termini di usabilità per matrici grandi e sparse**, infatti anche ponendo $d=49$ (il massimo possibile) si ottiene il risultato in un tempo sufficientemente breve ($\approx 0.005$ secondi).

##### Minimi quadrati regolarizzati
Impostiamo adesso il problema ai minimi quadrati regolarizzato alla Tikhonov per $d=6$
$$\min_{\alpha \in \mathbb{R}^{d+1}} \frac{1}{2} {\|X\alpha - y\|_{2}}^{2} + \frac{\lambda}{2} {\|L\alpha\|_{2}}^{2}$$

dove:
- $\lambda \in \mathbb{R}^{+}$ è il _parametro di regolarizzazione alla Tikhonov_;
- $L \in \mathbb{R}^{(d+1) \times n}$ è, almeno per il momento, la [[Matrice identità|matrice identità]] $I$.

In codice:
```python
d = 6
lmbda = 1e-2
L = np.eye(d+1)
X = np.vander(x, d+1, increasing=True)
```

<u>Nota bene</u>: `np.eye(n)` è la funzione per creare la matrice identità di dimensione `n`;

Possiamo quindi cominciare a risolvere il problema regolarizzato passando alle _equazioni normali regolarizzate_
$$(X^{T}X + \lambda L^{T}L) \alpha = X^{T}y$$

###### Cholesky
Per poter risolvere con Cholesky bisogna prima assicurari che il rango di $X^{T}X + \lambda L^{T}L$ sia massimo, ossia $=d+1$:
```python
print(np.linalg.matrix_rank(X.T @ X + lmbda * (L.T @ L)) == d+1)

# Output: True
```

Abbiamo il via libera per risolvere il sistema normale regolarizzato:
```python
alpha_chol = solve_linear_system_chol(X.T @ X + lmbda * (L.T @ L), X.T @ y)
print(alpha_chol)

# Output:
"""
[-0.08599562  1.55852847  0.81828962  0.58312561  0.04775328 -0.66445522
 -1.47598065]
"""
```

Il grafico per $\lambda = 10^{-2}$ è quindi il seguente:
![[calcolo-hw-2-approx-reg-chol1.png]]

un enorme cambiamento rispetto al grafico per $\lambda = 0$ (ossia senza regolarizzazione) sempre con $d=6$
![[calcolo-hw-2-approx-reg-chol2.png]]

###### SVD
Per quanto riguarda la decomposizione ai valori singolari, _è necessario adattare la sommatoria al problema regolarizzato_. Se consideriamo ancora $L=I$, allora possiamo scrivere la soluzione a
$$\min_{\alpha \in \mathbb{R}^{d+1}} \frac{1}{2} {\|X\alpha - y\|_{2}}^{2} + \frac{\lambda}{2} {\|L\alpha\|_{2}}^{2}$$
come
$$\alpha_{\lambda} = \sum\limits_{i=1}^{n} f_{i}\frac{u_{i}^{T}y^{\delta}}{\sigma_{i}} v_{i}$$
dove $f_{i}$ è detta _funzione di filtro_
$$f_{i} = \frac{\sigma_{i}^{2}}{\sigma_{i}^{2} + \lambda}$$
ed è _ciò che effettivamente realizza la regolarizzazione_.

Per implementare ciò, creiamo una nuova funzione `solve_least_squared_svd_tik()` che aggiunge tale fattore di filtro alla sommatoria
```python
def solve_least_squared_svd_tik(X: np.ndarray, y: np.ndarray, lmbda: float) -> np.ndarray:
	U, s, VT = np.linalg.svd(X)
	return sum((s[i]**2)/(s[i]**2 + lmbda) * ((U[:, i].T @ y) / s[i]) * VT[i, :] for i in range(np.linalg.matrix_rank(X)))
```
e la invochiamo su $X$, $y$ e $\lambda$ ($= 10^{-2}$)
```python
alpha_svd = solve_least_squared_svd_tik(X, y, lmbda)
print(alpha_svd)

# Output:
"""
[-0.08599562  1.55852847  0.81828962  0.58312561  0.04775328 -0.66445522
 -1.47598065]
"""
```
ottenendo i medesimi risultati di Cholesky, con grafico risultante:
![[calcolo-hw-2-approx-reg-svd.png]]

###### CGLS
Infine, per la CGLS, è necessario definire una nuova funzione `cgls_tikhonov()`, che risolve i minimi quadrati regolarizzati per qualunque matrice di Tikhonov $L$
```python
def cgls_tikhonov(A, y, L, lam, tol=1e-5, maxit=100):
    # Inizializzazione
    x = np.zeros(A.shape[1])
    r = r0 = y - A @ x
    p = A.T @ r - lam * (L.T @ (L @ x)) 
    z = p.copy() # z prende il posto di "p" come direzione

    for k in range(maxit):
        # Calcolo valori richiesti
        q = A @ p
        t = L @ p
        
        # Calcolo del coefficiente alpha
        alpha = (z.T @ z) / (q.T @ q + lam * (t.T @ t))
        
        # Aggiornamento di x
        x = x + alpha * p
        
        # Aggiornamento del residuo
        r = r - alpha * q
        
        # Verifica del criterio di arresto
        if np.linalg.norm(r) < tol * np.linalg.norm(r0):
	        print(f'Convergenza raggiunta in {k+1} iterazioni.')
            break
        
        # Calcolo della nuova direzione z
        z_new = A.T @ r - lam * (L.T @ (L @ x))
        
        # Calcolo del coefficiente beta
        beta = np.linalg.norm(z_new)**2 / np.linalg.norm(z)**2
        
        # Aggiornamento della direzione p
        p = z_new + beta * p
        z = z_new

    return x
```

che, per mantenere lo stesso grado di precisione dei casi precedenti, dovrà essere invocata specificando `tol=1e-9`:
```python
alpha_cgls = cgls_tikhonov(X, y, L, lmbda, tol=1e-9, maxit=10000)
print(alpha_cgls)

# Output:
"""
[-0.08599562  1.55852847  0.81828962  0.58312561  0.04775328 -0.66445522
 -1.47598065]
"""
```

<u>Nota bene</u>: nell'output non ometto la stringa `Convergenza raggiunta in {k+1} iterazioni.`, non viene proprio stampata. Questo nonostante l'alto numero di iterazioni massime passate (`10000`). Stampando infatti il _valore della norma del residuo_ ad ogni iterazione (`np.linalg.norm(r)`) ci si accorge che questo _oltre a una certa soglia non si abbassa_. Questo avviene sia per $\lambda > 0$ che per $\lambda = 0$. Ho testato altri algoritmi trovati online, che sono stati in grado di convergere alla soluzione esatta dopo 9 iterazioni, per cui ho pochi indizi su quali potrebbero essere le ragioni dietro a questo fenomeno. Ad ogni modo, _dopo anche `1000` iterazioni l'algoritmo converge alla soluzione esatta_, per cui mantengo `10000` come upperbound per gli esperimenti futuri. Non modifico invece il valore della tolleranza perché l'algoritmo comincia a terminare sulla base di questa da $10^{-3}$ in su (inaccettabile).

La soluzione trovata coincide con quelle dei due altri metodi. Il grafico prodotto, quindi, è il seguente:
![[calcolo-hw-2-approx-reg-cgls.png]]

###### $\lambda$ variabile
A questo punto, per ognuno dei 3 metodi, visualizziamo il risultato prodotto su differenti valori di $\lambda$. In particolare ci concentriamo su 6 valori
$$[10^{-7}, 10^{-6}, 10^{-3}, 1, 10, 100]$$

Per $\lambda = 10^{-7}$ ci aspettiamo che l'influenza della regolarizzazione sia molto bassa, e che quindi la soluzione soffra ancora di overfit:
![[calcolo-hw-2-approx-reg-lambda1.png]]

Per $\lambda = 10^{-6}$ il risultato è estremamente simile al [[Calcolo numerico - HW. 2#$d$ variabile|problema non regolarizzato ma con grado]] $d=4$:
![[calcolo-hw-2-approx-reg-lambda2.png]]

Per $\lambda = 10^{-3}$ si ha:
![[calcolo-hw-2-approx-reg-lambda3.png]]

Per $\lambda = 1$, invece, la CGLS produce `Overflow`. Questo perché dopo un certo numero di iterazioni comincia a divergere. Per poter ottenere un risultato almeno accettabile, riduco il numero massimo di iterazioni a `100`:
![[calcolo-hw-2-approx-reg-lambda4.png]]

Ponendo $\lambda = 10$ (e decrementando a `50` il numero massimo di iterazioni della CGLS), si ottiene:
![[calcolo-hw-2-approx-reg-lambda5.png]]

E infine, per $\lambda = 100$ si ha:
![[calcolo-hw-2-approx-reg-lambda6.png]]

In poche parole stiamo empiricamente verificando che, superata una certa soglia del parametro di regolarizzazione, viene gradualmente spostata la priorità sull'abbassamento di ${\|L\alpha\|_{2}}^{2}$ piuttosto che di ${\|X\alpha - y\|_{2}}^{2}$. Infatti nell'ultimo caso il valore di $\alpha$ (con tutti e 3 i metodi) è
```python
"""
[0.21013892 0.14988706 0.10763106 0.08099121 0.06326307 0.05086553
 0.04183671]
"""
```

Detto questo, il valore di $\lambda$ per il quale il polinomio approssimante meglio approssima i dati, valutando esclusivamente da un punto di vista visivo, è $\lambda = 10^{-6}$.

E' interessante notare il **comportamento dell'ultimo coefficiente di $\alpha$**, ossia quello che moltiplica $x^{6}$ e che determina la convessità/concavità della funzione. E' infatti **l'unico tra tutti che sembra salire all'aumentare di $\lambda$** (senza tendere a 0). Si nota dal momento in cui la concavità del polinomio approssimante si ribalta nel passaggio da $\lambda=1$ a $\lambda = 10$. Infatti:
- $\lambda = 1 \implies \alpha_{6} = -0.43761151$
- $\lambda = 10 \implies \alpha_{6} = 0.00309763$

Consideriamo allora 50 valori di $\lambda$ da $1$ a $200$, e plottiamo unicamente $\alpha_{6}$:
![[calcolo-hw-2-approx-reg-alpha6.png]]

La verità è che **non è l'unico coefficiente a comportarsi in questa maniera**. Lo dimostriamo plottando tutti i valori dei coefficienti all'aumentare di $\lambda$:
![[calcolo-hw-2-approx-reg-alphas.png]]

A parte $\alpha_{1}, \alpha_{2}, \alpha_{3}$, tutti gli altri coefficienti almeno inizialmente tendono a salire, per poi puntare a 0. Ognuno di questi compie questa virata con la sua velocità, da $\alpha_{0}$ che è il più veloce ad $\alpha_{6}$ che smette di salire per $\lambda \approx 30$.

Questo per valori di $\lambda$ da $1$ a $200$, ossia da escludere del tutto per quanto riguarda la regolarizzazione. Se invece facciamo lo stesso procedimento per $\lambda$ da $10^{-8}$ a $1$, e plottiamo il grafico in scala logaritmica sulle ascisse (per aumentare la leggibilità), otteniamo:
![[calcolo-hw-2-approx-reg-alphas2.png]]
dove il punto di convergenza degli $\alpha$ è a circa $\lambda = 5 \times 10^{-5}$
![[calcolo-hw-2-approx-reg-alphas3.png]]

Sembra proprio che _arrivati a tale valore di $\lambda$ si arresti la decrescita (in valore assoluto) dei coefficienti del polinomio_, o che meglio, da quel momento in poi non sia più esponenziale. Anzi, già sappiamo che non tutti i coefficienti continuano a decrescere per valori di $\lambda$ da $1$ a $100$.
Avviene quindi che il parametro di regolarizzazione abbassa i coefficienti in 3 separate fasi:
1. $0 < \lambda < k < 1$ --> _la discesa dei coefficienti (in valore assoluto) è esponenziale_;
2. $k < \lambda < p (> 1)$ --> _i coefficienti si assestano, oscillando su valori molto bassi_;
3. $\lambda > p$ --> _la discesa dei coefficienti (in valore assoluto) è logaritmica_.

La seconda fase è quella più interessante: _il valore di $\lambda$ è sufficientemente alto da tenere bassi i coefficienti, ma non abbastanza da "vincere" completamente sui minimi quadrati_. A causa di questo, avviene che _i coefficienti rimangono influenzati dall'approssimazione e cercano di compensare l'abbassamento generale di ${\|L\alpha\|_{2}}^{2}$ con la minimizzazione dei quadrati_.

###### $d$ variabile
Sulla falsa riga del caso senza regolarizzazione, variamo il grado $d$ del polinomio approssimante tra $0$ a $8$, ma questa volta in 2 modalità differenti:
- mantenendo uguale il valore di $\lambda$ considerato migliore ($10^{-6}$);
- modificando $\lambda$ sul set $\{10^{-7}, 10^{-3}, 5\}$;

Chiaramente per ogni caso plottiamo i polinomi calcolati da tutti e 3 i metodi. Il codice che produrrà i risultati è:
```python
chols = []
svds = []
cglss = []
for d in range(0, 9):
	L = np.eye(d+1) + np.diag([-1]*(d), k=1)
	X = np.vander(x, d+1, increasing=True)
	
	alpha_chol = solve_linear_system_chol(X.T @ X + lmbda * (L.T @ L), X.T @ y)
	y_chol = np.polyval(alpha_chol[: : -1], xx)
	chols.append(alpha_chol)
	
	alpha_svd = solve_least_squared_svd_tik(X, y, lmbda)
	y_svd = np.polyval(alpha_svd[: : -1], xx)
	svds.append(alpha_svd)
	
	alpha_cgls = cgls_tikhonov(X, y, L, lmbda, tol=1e-9, maxit=20)
	y_cgls = np.polyval(alpha_cgls[: : -1], xx)
	cglss.append(alpha_cgls)

for i in range(9):
	plt.subplot(3, 3, i+1)
	plt.plot(x, y, 'bo')
	plt.plot(xx, np.polyval(chols[i][::-1], xx), 'r-')
	plt.plot(xx, np.polyval(svds[i][::-1], xx), 'g-')
	plt.plot(xx, np.polyval(cglss[i][::-1], xx), 'y-')
	plt.title(f"$d={i}$")
	plt.grid()

plt.show()
```

Cominciamo considerando $\lambda = 10^{-6}$:
![[calcolo-hw-2-approx-reg-d.png]]
per il quale si può osservare che:
- _per i gradi più bassi_, come $0$ e $1$, l'_influenza della regolarizzazione è fondamentalmente nulla_ --> basta vedere il confronto con i [[Calcolo numerico - HW. 2#$d$ variabile|casi senza regolarizzazione]];
- _per i gradi più alti_, viceversa, la regolarizzazione è ben visibile.

A questo punto produciamo i grafici gli altri valori di $\lambda$, partendo da $10^{-7}$:
![[calcolo-hw-2-approx-reg-d1.png]]
per il quale le grandi differenze, chiaramente, si possono notare negli ultimi 3 grafici (gradi più alti).

Quindi procediamo su $\lambda = 10^{-3}$:
![[calcolo-hw-2-approx-reg-d2.png]]
per il quale notiamo una diffusa **omologazione dei gradi più alti**. In particolare, con un valore così alto di $\lambda$, _i polinomi dal 5° all'8° grado cominciano a "perdere di personalità"_. Facendo riferimento alle fasi dei parametri di regolarizzazione, qui si è nella situazione $k < \lambda < p$.

Infine, per $\lambda = 5$ si ottiene:
![[calcolo-hw-2-approx-reg-d3.png]]
dove è più facile notare l'influenza della regolarizzazione anche nei polinomi di grado più basso. In particolare la media di $y_{i} \ \ i=1, \cdots, n$ rappresentata da $d=0$, è più bassa dei casi precedenti; e in generale, tutti i polinomi di grado $>1$ sono molto simili alla retta $d=1$.

###### $L \neq I$
Consideriamo adesso come matrice di Tikhonov $L$ non più l'identità, ma
$$\begin{split}
  L = \begin{bmatrix} 
        1 & -1 & 0 & 0 & \dots & 0 \\
        0 & 1 & -1 & 0 & \dots & 0 \\ 
        0 & 0 & 1 & -1 & \dots & 0 \\ 
        0 & 0 & 0 & 1 & \dots & 0 \\ 
        \vdots & \vdots & \vdots & \vdots & \ddots & -1 \\ 
        0 & 0 & 0 & 0 & \dots & 1 
      \end{bmatrix},
  \end{split}$$

In codice ci è sufficiente anzitutto sommare a `np.eye(d+1)` la matrice `np.diag([-1]*(d), k=1)`, ossia una matrice che ha $-1$ su tutta la sovra-diagonale:
```python
L = np.eye(d+1) + np.diag([-1]*(d), k=1)
```

Bisogna poi adattare la SVD affinché prenda in considerazione la matrice $L \neq I$ (Cholesky e CGLS la supportano già). Questo passaggio non è immediato, infatti è difficile ricavare i fattori di filtro come nella regolarizzazione con $L=I$ (detta _regolarizzazione di Ridge_). Infatti _il metodo migliore consiste nel modificare il problema passando a un minimo quadrato regolarizzato equivalente_[^2]. In poche parole, risolvere questo
$$\min_{\alpha} \frac{1}{2} {\|X\alpha  - y\|_{2}}^{2} + \frac{\lambda}{2} {\|L\alpha\|_{2}}^{2}$$
è equivalente a risolvere
$$\min_{\hat{\alpha}} \frac{1}{2} {\|((XL^{-1})\hat{\alpha} - y\|_{2}}^{2} + \frac{\lambda}{2} {\|\hat{\alpha}\|_{2}}^{2}$$
dove $\hat{\alpha} = L\alpha$, e quindi $\alpha = L^{-1}\hat{\alpha}$.

Ci basta quindi definire una funzione `solve_least_squared_svd_tik_L()` che risolve il problema con la SVD regolarizzata "standard" facendo attenzione alla matrice di riferimento $XL^{-1}$ e al risultato finale $\alpha = L^{-1} \hat{\alpha}$:
```python
def solve_least_squared_svd_tik_L(X: np.ndarray, y: np.ndarray, L: np.ndarray, lmbda: float) -> np.ndarray:
	U, s, VT = np.linalg.svd(X @ np.linalg.inv(L))
	return np.linalg.inv(L) @ sum((s[i]**2)/(s[i]**2 + lmbda) * ((U[:, i].T @ y) / s[i]) * VT[i, :] for i in range(np.linalg.matrix_rank(X)))
```

Non ci resta che ripetere l'esperimento precedente con la $L$ modificata. Tuttavia, per poter mostrare in modo più evidente l'effetto di questo cambiamento, aggiungo ad ogni sotto-grafico il polinomio calcolato per $L=I$ (con Cholesky, considerando che è il più veloce).
```python
f_chols = []
chols = []
svds = []
cglss = []

for d in range(0, 9):
	L = np.eye(d+1) + np.diag([-1]*(d), k=1)
	X = np.vander(x, d+1, increasing=True)
	
	alpha_f_chol = solve_linear_system_chol(X.T @ X + lmbda * np.eye(d+1), X.T @ y)
	y_f_chol = np.polyval(alpha_f_chol[: : -1], xx)
	f_chols.append(alpha_f_chol)
	
	alpha_chol = solve_linear_system_chol(X.T @ X + lmbda * (L.T @ L), X.T @ y)
	y_chol = np.polyval(alpha_chol[: : -1], xx)
	chols.append(alpha_chol)
	
	alpha_svd = solve_least_squared_svd_tik_L(X, y, L, lmbda)
	y_svd = np.polyval(alpha_svd[: : -1], xx)
	svds.append(alpha_svd)
	
	alpha_cgls = cgls_tikhonov(X, y, L, lmbda, tol=1e-9, maxit=20)
	y_cgls = np.polyval(alpha_cgls[: : -1], xx)
	cglss.append(alpha_cgls)

for i in range(9):
	plt.subplot(3, 3, i+1)
	plt.plot(x, y, 'bo')
	plt.plot(xx, np.polyval(f_chols[i][: : -1], xx), 'k-')
	plt.plot(xx, np.polyval(chols[i][: : -1], xx), 'r-')
	plt.plot(xx, np.polyval(svds[i][: : -1], xx), 'g-')
	plt.plot(xx, np.polyval(cglss[i][: : -1], xx), 'y-')
	plt.title(f"$d={i}$")
	plt.grid()

plt.show()
```

In nero, quindi, si vede il risultato per $L=I$, mentre in giallo (ultimo colore plottato) si vede per $L \neq I$ (con stesso $\lambda$).

Partiamo quindi con $\lambda = 10^{-7}$:
![[calcolo-hw-2-approx-reg-L1.png]]
per il quale già per gradi alti (come $6$, $7$ e $8$), si notano delle differenze minime. Concentrandosi sul caso $d=6$, _l'impressione della curva gialla ($L \neq I$) è che sia più regolarizzata di quella nera ($L = I$)_. In particolare sembra seguire i cambi di direzione del polinomio con forza.

Per $\lambda = 10^{-3}$ si ha:
![[calcolo-hw-2-approx-reg-L2.png]]
dove l'effetto maggiore si nota per $d=3$, che sembra riconfermare l'idea precedente, ossia che la curva gialla sia generalmente più "piatta"/regolarizzata di quella nera.

<u>Nota bene</u>: è interessante notare che le differenze di $L$ si notino in questo caso su $d=3$, mentre in quello precedente su $d=6$.

Infine, per $\lambda = 5$ otteniamo:
![[calcolo-hw-2-approx-reg-L3.png]]
che invece ribalta ogni ipotesi! Qui per ogni grafico **la regolarizzazione con $L \neq I$ è meno influente rispetto a quella per $L = I$**. Ce lo suggerisce il fatto che per $d$ da $2$ a $6$ il coefficiente $\alpha_{0}$ è più alto (la curva è più in alto nelle ordinate), e che per $d=7$ e $d=8$ il polinomio in giallo segua maggiormente i dati rispetto a quello nero.

Se proviamo di fatti a porre sulla sovra-diagonale degli $1$ al posto di $-1$, otteniamo l'effetto contrario, ossia un'amplificazione dell'effetto della regolarizzazione:
![[calcolo-hw-2-approx-reg-L4.png]]

##### Problema test
Ci vengono ora svelati i parametri e gli iperparametri del problema test:
$$d_{true} = 4$$
$$\alpha_{true} = (0, 0, 4, 0, -3)$$

Per prima cosa, allora, plottiamo il polinomio _true_ insieme al dataset:
```python
d_true = 4
alpha_true = np.array([0, 0, 4, 0, -3])
y_true = np.polyval(alpha_true[::-1], xx)

plt.plot(x, y, 'bo')
plt.plot(xx, y_true, 'k-')
plt.legend(["dataset", "True"])
plt.grid()
plt.show()
```
![[calcolo-hw-2-approx-test1.png]]

Questo è il polinomio da cui è stato ricavato il dataset. E' effettivamente di 4° grado ($-3x^{4} + 4x^{2}$), ma _non sviluppa tutti i suoi flessi nell'intervallo $[0, 1]$_.

Non ci resta che confrontarlo con i risultati sopra ottenuti, partendo prima dalle soluzione con i minimi quadrati standard, e quindi con i regolarizzati.

###### Minimi quadrati
La soluzione calcolata con tutti e tre i metodi per $d=4$ è:
```python
"""
[ -0.16232963   3.24903618  -7.85010467  17.03510471 -11.51696295]
"""
```
che produce il grafico
![[calcolo-hw-2-approx-test2.png]]

Visivamente parlando _si tratta di una soluzione abbastanza distante da quella reale_, in particolare se si tengono in considerazione gli estremi dei polinomi: la **soluzione calcolata ha un valore assoluto della derivata molto più alto per $x=0$ e $x=1$**. Questo avviene perché **la potenza del polinomio approssimante è totalmente espressa nell'intervallo di riferimento**!
Per verificarlo ci è sufficiente mostrare i grafici di entrambe le funzioni per un range più ampio, per esempio $[-\frac{1}{2}, \frac{3}{2}]$:
```python
n = 500
xx = np.linspace(-0.5, 1.5, n)
...
```
![[calcolo-hw-2-approx-test3.png]]

Mentre il polinomio approssimante si sviluppa interamente nell'intervallo $[0, 1]$, quello reale si estende al di fuori di esso.

Ad ogni modo, è con il calcolo dell'errore relativo che otteniamo una veritiera stima della differenza tra i due polinomi:
$$e_{rel} = \frac{\|\alpha_{true} - \alpha\|_{2}}{\|\alpha_{true}\|_{2}}$$
```python
err_rel = np.linalg.norm(alpha_true - alpha) / np.linalg.norm(alpha_true)
print(err_rel)

# Output: 4.533171155874228
```

Si tratta infatti di un valore estremamente alto, considerando che è relativo.

Proviamo quindi, variando il grado di $d$, a vedere (solo visivamente) il rapporto tra il risultato e la soluzione reale.

Per $d=3$ otteniamo:
![[calcolo-hw-2-approx-test4.png]]
un risultato più simile al polinomio effettivo! Questo perché nell'intervallo $[0, 1]$ il polinomio reale sembra una funzione di 3° grado. Più allarghiamo il range, però, più dovremmo vedere il peggioramento dell'approssimazione:
![[calcolo-hw-2-approx-test5.png]]

Per $d=6$, dove cominciano a notarsi i primi segni di overfit, si ha:
![[calcolo-hw-2-approx-test6.png]]
molto differente dall'andamento della curva reale.

###### Minimi quadrati regolarizzati
Procediamo adesso con il confronto dei polinomi per gli stessi valori di $d$ precedenti ma nel caso dei minimi quadrati regolarizzati.

Cominciamo con $d=4$, e variamo il parametro di regolarizzazione $\lambda$ tra i valori $[10^{-7}, 10^{-6}, 10^{-3}, 1, 10, 100]$. Per ognuno di questi quindi produciamo un grafico e calcoliamo anche l'errore relativo.
```python
d = 4
lmbdas = [1e-7, 1e-6, 1e-3, 1, 1e+1, 1e+2]
alphas = []
for lmbda in lmbdas:
	X = np.vander(x, d+1, increasing=True)
	alpha = solve_least_squared_svd_tik(X, y, lmbda)
	alphas.append(alpha)

for i, alpha in enumerate(alphas):
	plt.subplot(2, 3, i+1)
	plt.plot(x, y, 'bo')
	plt.plot(xx, y_true, 'k-')
	plt.plot(xx, np.polyval(alpha[: : -1], xx), 'r-')
	plt.title(rf"$\lambda$ = {lmbdas[i]}")
	plt.grid()

plt.show()
```
![[calcolo-hw-2-approx-test7.png]]

Possiamo notare che per valori sufficientemente alti di $\lambda$, come $10^{-3}$, la soluzione calcolata sembri ricalcare con maggiore precisione quella reale. Gli errori relativi sono i seguenti:
1. $\lambda = 10^{-7} \implies e_{rel} = 4.53090174172208$
2. $\lambda = 10^{-6} \implies e_{rel} = 4.510583190694112$
3. $\lambda = 10^{-3} \implies e_{rel} = 0.9013877445917304$
4. $\lambda = 1 \implies e_{rel} = 0.9052597504492328$
5. $\lambda = 10 \implies e_{rel} = 0.9753422330322017$
6. $\lambda = 100 \implies e_{rel} = 0.9920011873130807$

<u>Nota bene</u>: il motivo per cui, nonostante il primo valore di $\lambda$ sia decisamente più promettende dell'ultimo, l'errore relativo sui due ci dice l'opposto, è dovuto al fatto che _per $\lambda$ molto alti i coefficienti si abbassano, e $\alpha_{true}$ è costituito per la maggior parte da coefficienti pari a 0_. Non si tratta in effetti di un criterio ottimale su cui basarsi per valutare la validità di una soluzione.

Produciamo quindi un grafico dell'errore relativo al variare di $\lambda$ su valori nell'intervallo $[10^{-7}, 1]$ (logaritmico sulle ascisse):
![[calcolo-hw-2-approx-test8.png]]

Abbiamo un minimo, tra $10^{-3}$ e $10^{-2}$.

Continuiamo variando adesso anche $d$, tra i valori $[2, 3, 5, 6, 7, 8]$:
![[calcolo-hw-2-approx-test9.png]]
![[calcolo-hw-2-approx-test10.png]]
![[calcolo-hw-2-approx-test11.png]]
![[calcolo-hw-2-approx-test12.png]]
![[calcolo-hw-2-approx-test13.png]]
![[calcolo-hw-2-approx-test14.png]]

Da questi grafici possiamo osservare due cose:
1. con gradi $d$ che provocano overfit, **la regolarizzazione** (per certi $\lambda$) **produce dei risultati pressoché molto simili a quelli che si otterrebbero con il grado $d_{true}$ senza regolarizzazione** --> la differenza è comunque visibile, e _il polinomio approssimante si irrigidisce molto come conseguenza della regolarizzazione_;
2. **la regolarizzazione ha un effetto estremamente positivo sul polinomio approssimante di grado $d_{true}$** --> questo perché "_rilassando_" il polinomio (i suoi coefficienti) _è come se "spalmassero" i suoi flessi anche al di fuori dell'intervallo_ di riferimento $[0, 1]$. Il risultato di ciò è un crollo dell'errore relativo, da $\approx 4.53$ a $\approx 0.90$.

#### Conclusioni
In conclusione, con questo esperimento, abbiamo avuto modo di _testare i 3 metodi studiati per risolvere il problema ai minimi quadrati_, confrontando _tempi_ e _risultati_. Inoltre abbiamo imparato _i molteplici benefici apportati dalla regolarizzazione, che può quindi essere usata sia per risolvere l'overfit che_ (nel caso si fosse a conoscenza del grado $d_{true}$) _per migliorare l'approssimazione_.

### Ottimizzazione
#### Introduzione
In questa esercitazione viene richiesto di utilizzare il [[Metodo di discesa del gradiente|metodo di discesa del gradiente]] per risolvere il problema di [[Ottimizzazione di dati|ottimizzazione]]
$$\min_{x \in \mathbb{R}^{n}} f(x)$$
su 3 differenti funzioni $f$.
Per ognuna di queste, in particolare, dovremo:
- confrontare le soluzioni ottenute con e senza _backtracking_ (per diversi valori dello _step-size_ $\alpha$);
- visualizzare la norma del [[Gradiente|gradiente]] ad ogni iterato $k \in \mathbb{N}$ (con e senza backtracking);
- visualizzare gli errori relativi (ci vengono fornite le soluzioni) (con e senza backtracking);
- fare un plot delle funzioni e del cammino dell'algoritmo (con e senza backtracking).

#### Sviluppo
Procediamo in parallelo sulle tre funzioni, vale a dire che per ogni punto ci occuperemo separatamente di tutte e 3 le funzioni.

##### Analisi
Per poter procedere con l'algoritmo, è prima necessario assicurarsi della validità di alcune _ipotesi che le 3 funzioni devono rispettare per poterne trovare il minimo globale_. In particolare si deve verificare che le funzioni siano sia [[Funzione convessa|convesse]] che [[Funzione coerciva|coercive]]: sono assunzioni che garantiscono da un lato l'**esistenza di almeno un punto di minimo** (coercività) e dall'altro il fatto che **ogni minimo è per forza globale** (convessità). Solo **dopo aver verificato queste due proprietà possiamo applicare il metodo di discesa del gradiente ed essere sicuri di una convergenza a un minimo globale**.

###### Convessità
Per verificare la convessità è sufficiente usare la sua caratterizzazione:
> Una funzione $f \in C^{2}(\mathbb{R}^{n})$[^1] è convessa $\iff$ la [[Matrice hessiana|matrice hessiana]] $H_{f}(x_{0}) = (\nabla^{2}f(x_{0}))_{i,j} \ \ \forall x_{0} \in \mathbb{R}^{n}$ è [[Classificazione forme quadratiche|semi-definita positiva]], ossia $\forall x \in \mathbb{R}^{n} \ \ \ x^{T}H_{f}(x_{0})x \geq 0$.

Della funzione
$$f_{1}(x_{1}, x_{2}) = (x_{1} - 3)^{2} + (x_{2} - 1)^{2}$$
si vuole quindi calcolare la matrice hessiana. Questa è della forma
$$Hf_{1}(x_{1}, x_{2}) = \begin{bmatrix} \partial_{x_{1}x_{1}}f_{1} & \partial_{x_{1}x_{2}}f_{1} \\ \partial_{x_{2}x_{1}}f_{1} & \partial_{x_{2}x_{2}}f_{1} \end{bmatrix}$$
ossia composta dalle 4 derivate parziali seconde (miste) di $f_{1}$.
Partiamo con il calcolo delle 2 derivate parziali $\partial_{x_{1}}, \partial_{x_{2}}$:
$$\partial_{x_{1}}f_{1} = 2(x_{1} - 3)$$
$$\partial_{x_{2}}f_{1} = 2(x_{2} - 1)$$
Quindi calcoliamo l'hessiana
$$Hf_{1}(x_{1}, x_{2}) = \begin{bmatrix} 2 & 0 \\ 0 & 2 \end{bmatrix}$$
che è _definita positiva_ in quanto i suoi [[Autovalore|autovalori]] $2$ e $2$ sono entrambi positivi. Di conseguenza è anche semi-definita positiva $\implies$ **$f_{1}$ è convessa**.

Procediamo nello stesso modo con
$$f_{2}(x_{1}, x_{2}) = 10(x_{1} - 1)^{2} + (x_{2} - 2)^{2}$$
per cui
$$\partial_{x_{1}}f_{2} = 20(x_{1} - 1)$$
$$\partial_{x_{2}}f_{2} = 2(x_{2} - 2)$$
e
$$Hf_{2}(x_{1}, x_{2}) = \begin{bmatrix} 20 & 0 \\ 0 & 2 \end{bmatrix}$$
che per lo stesso ragionamento precedente ci mostra la **convessità di $f_{2}$**.

La funzione
$$f_{3}(x) = x^{4} + x^{3} - 2x^{2} - 2x$$
è l'unica del tipo di dominio $\mathbb{R}$. Per verificarne la convessità basta pensare che _l'hessiana è solo una generalizzazione della derivata seconda di una funzione da $\mathbb{R}$ a $\mathbb{R}$_: ci basta vedere se la derivata seconda di $f_{3}$ è sempre positiva $\forall x$.
$$f_{3}'(x) = 4x^{3} + 3x^{2} - 4x - 2$$
$$f_{3}''(x) = 12x^{2} + 6x - 4$$

Ebbene, in questo caso, la derivata seconda ovviamente non è sempre positiva (si pensi per $x = 0$), per cui **la funzione $f_{3}$ non è convessa**. Questo implica che **se esistono minimi locali** (lo si vedrà con la coercività) **non è assicurato che si tratti anche di minimi globali**. Non solo: più in generale l'algoritmo di discesa del gradiente, che si basa sulle _condizioni necessarie del primo ordine_, **potrebbe convergere su un punto di sella** (perché è stazionario, per cui $\nabla f_{3}(x^{*}) = \underline{0}$).

###### Coercività
Per verificare la coercività, invece, dovremmo per ognuna delle 3 funzioni verificare il limite:
$$\lim_{\|x\| \to \infty} f(x) = +\infty$$
Tuttavia, almeno per quanto riguarda le prime due funzioni $f_{1}, f_{2}$, non è necessario risolvere un limite in due variabili. Basta notare che _ogni membro contenente le due variabili $x_{1}, x_{2}$ viene elevato al quadrato, e che i membri al quadrato sono sempre sommati tra di loro_: al crescere di $\|(x_{1}, x_{2})\|$, sicuramente cresce anche $f(x_{1}, x_{2})$. Quindi **$f_{1}, f_{2}$ sono coercive**.

Per quanto riguarda $f_{3}$, invece, si dimostra la coercività risolvendo i limiti per $x \to -\infty$ e per $x \to +\infty$: avendo $x^{4}$ come termine maggiore, in entrambe le direzioni di $x$ la funzione $f_{3}(x)$ sarà positiva, da cui la **coercività di $f_{3}$**.

Ora che abbiamo i presupposti teorici, possiamo partire con lo sviluppo dell'algoritmo di discesa del gradiente.

##### Discesa del gradiente
Prima di poter scrivere l'algoritmo, bisogna definire per ognuna delle funzioni le loro "funzioni informatiche" in Python, comprese quelle associate al loro gradiente:
```python
import numpy as np
import matplotlib.pyplot as plt
import time

def f1(x: np.ndarray) -> np.ndarray:
	return (x[0] - 3)**2 + (x[1] - 1)**2

def f2(x: np.ndarray) -> np.ndarray:
	return 10*(x[0] - 1)**2 + (x[1] - 2)**2

def f3(x: np.ndarray) -> np.ndarray:
	return x**4 + x**3 - 2*x**2 - 2*x

def df1(x: np.ndarray) -> np.ndarray:
	return np.array([2*(x[0] - 3), 2*(x[1] - 1)])

def df2(x: np.ndarray) -> np.ndarray:
	return np.array([20*(x[0] - 1), 2*(x[1] - 2)])

def df3(x: np.ndarray) -> np.ndarray:
	return 4*x**3 + 3*x**2 - 4*x - 2
```

L'algoritmo di discesa del gradiente risolve tutti i problemi di ottimizzazione del tipo
$$\min_{x \in \mathbb{R}^{n}} f(x)$$
purché $f$ sia _smooth_ ($\in C^{1}(\mathbb{R}^{n})$), e le 3 funzioni lo sono in quanto polinomiali. Per cui il codice è il medesimo in tutti i casi.
Cominciamo trovando il minimo delle 3 funzioni senza backtracking, ossia con l'algoritmo detto _a passo fisso_.

###### Passo fisso
Il codice dell'algoritmo è il seguente:
```python
def GD(f, df, x0, x_true, alpha, maxit=100, tolf=1e-6, tolx=1e-6):
	k = 0
	rel_err = np.zeros((maxit+1, ))
	obj_val = np.zeros((maxit+1, ))
	grad_norm = np.zeros((maxit+1, ))
	
	condizione = True
	while condizione:
		x = x0 - alpha * df(x0)
	
		rel_err[k] = np.linalg.norm(x - x_true) / np.linalg.norm(x_true)
		obj_val[k] = f(x)
		grad_norm[k] = np.linalg.norm(df(x))
		
		condizione = (k < maxit) and (np.linalg.norm(df(x)) > tolf) and (np.linalg.norm(x - x0) > tolx)
		
		if (np.linalg.norm(x - x0) <= tolx):
			print(f"Algoritmo terminato per condizione su tolx.")
		
		k = k + 1
		x0 = x
	
	if k < maxit:
		rel_err = rel_err[:k]
		obj_val = obj_val[:k]
		grad_norm = grad_norm[:k]

return x, rel_err, obj_val, grad_norm
```

E' importante tenere a mente quali sono le 2 condizioni di arresto dell'algoritmo (oltre al numero di iterazioni):
1. `np.linalg.norm(df(x)) > tolf`, che ferma l'algoritmo se la norma del gradiente `np.linalg.norm(df(x))` è più piccola della tolleranza `tolf` --> **indica la convergenza raggiunta dall'algoritmo**;
2. `np.linalg.norm(x - x0) > tolx`, che ferma l'algoritmo se il passo percorso alla $k$-esima iterazione è più piccolo della tolleranza `tolx` --> **indica l'"arresa" dell'algoritmo quando la funzione è troppo piatta**.

Lo invochiamo quindi sulle 3 funzioni, tenendo conto del tempo di esecuzione e della velocità di convergenza, su diversi valori dello step-size $\alpha$.
Partiamo con $\alpha = 0.07$:
```python
alpha = 0.07
x1_true = np.array([3, 1])
x2_true = np.array([1, 2])
x3_true = 0.922222

start = time.time()
x1, rel_err1, _, _ = GD(f1, df1, np.array([0, 0]), x1_true, alpha)
end = time.time()
print(f"Soluzione per f1: {x1}; reale {x1_true}")
print(f"Tempo di esecuzione per f1: {end-start}s")
print(f"Velocità di convergenza per f1: {len(rel_err1)} iter.")
print()

start = time.time()
x2, rel_err2, _, _ = GD(f2, df2, np.array([0, 0]), x2_true, alpha)
end = time.time()
print(f"Soluzione per f2: {x2}; reale {x2_true}")
print(f"Tempo di esecuzione per f2: {end-start}s")
print(f"Velocità di convergenza per f2: {len(rel_err2)} iter.")
print()

start = time.time()
x3, rel_err3, _, _ = GD(f3, df3, np.array([0]), x3_true, alpha)
end = time.time()
print(f"Soluzione per f3: {x3}; reale {x3_true}")
print(f"Tempo di esecuzione per f3: {end-start}s")
print(f"Velocità di convergenza per f3: {len(rel_err3)} iter.")
print()

# Output:
"""
Algoritmo terminato per condizione su tolx.
Soluzione per f1: [2.99999484 0.99999828]; reale [3 1]
Tempo di esecuzione per f1: 0.001950979232788086s
Velocità di convergenza per f1: 88 iter.

Algoritmo terminato per condizione su tolx.
Soluzione per f2: [1.         1.99999459]; reale [1 2]
Tempo di esecuzione per f2: 0.0019028186798095703s
Velocità di convergenza per f2: 85 iter.

Algoritmo terminato per condizione su tolx.
Soluzione per f3: [0.92222465]; reale 0.922222
Tempo di esecuzione per f3: 0.0006880760192871094s
Velocità di convergenza per f3: 13 iter.
"""
```

Possiamo fare le seguenti osservazioni:
- in tutti e 3 i casi l'algoritmo termina sulla condizione `tolx`, per cui _le funzioni vicino al minimo si appiattiscono così tanto da non consentire un sufficiente spostamento verso la direzione di discesa_;
- le soluzioni calcolate non sono esatte, o formalmente _sono affette dall'[[Errore di troncamento|errore di troncamento]]_ tipico degli [[Algoritmo iterativo|algoritmi iterativi]];
- la soluzione trovata per $f_{3}$ è la stessa indicata come reale, per cui _siamo stati fortunati e siamo partiti da un $x_{0}$_ ($=0$) _che consente all'algoritmo di convergere al minimo globale_ (e non ad uno locale o ad una sella).

Proviamo ora a diminuire $\alpha$ a $0.05$:
```python
"""
Soluzione per f1: [2.99992828 0.99997609]; reale [3 1]
Tempo di esecuzione per f1: 0.0024213790893554688s
Velocità di convergenza per f1: 101 iter.

Soluzione per f2: [1.         1.99995219]; reale [1 2]
Tempo di esecuzione per f2: 0.0023331642150878906s
Velocità di convergenza per f2: 101 iter.

Algoritmo terminato per condizione su tolx.
Soluzione per f3: [0.92222429]; reale 0.922222
Tempo di esecuzione per f3: 0.0024399757385253906s
Velocità di convergenza per f3: 21 iter.
"""
```

Nel caso di $f_{1}, f_{2}$, nonostante la precisione delle soluzioni, l'algoritmo è terminato per il raggiungimento del massimo numero di iterazioni `maxit` ($=100$). Invece, per $f_{3}$ il numero di iterazioni è aumentato solo di 8. Questo è causato dalla conformazione delle funzioni e dal punto di partenza $x_{0}$: _è molto probabile che $f_{3}$ in $x_{0}$ abbia un antigradiente sufficientemente alto da sopperire all'abbassamento di $\alpha$_.

Se abbassiamo $\alpha$ a $0.02$, però, otteniamo:
```python
"""
Soluzione per f1: [2.61009851 0.87003284]; reale [3 1]
Tempo di esecuzione per f1: 0.002197742462158203s
Velocità di convergenza per f1: 101 iter.

Soluzione per f2: [1.         1.74006567]; reale [1 2]
Tempo di esecuzione per f2: 0.005120038986206055s
Velocità di convergenza per f2: 101 iter.

Soluzione per f3: [0.92219236]; reale 0.922222
Tempo di esecuzione per f3: 0.010131597518920898s
Velocità di convergenza per f3: 101 iter.
"""
```
Lo step-size è troppo basso, e _in nessun caso l'algoritmo converge alla soluzione in 100 iterazioni_. Questo è un caso che si vuole evitare, ovviamente. 

Proviamo invece adesso a portare $\alpha$ a $0.1$:
```python
"""
Algoritmo terminato per condizione su tolx.
Soluzione per f1: [2.99999632 0.99999877]; reale [3 1]
Tempo di esecuzione per f1: 0.001371622085571289s
Velocità di convergenza per f1: 61 iter.

Soluzione per f2: [2. 2.]; reale [1 2]
Tempo di esecuzione per f2: 0.002219676971435547s
Velocità di convergenza per f2: 101 iter.

Algoritmo terminato per condizione su tolx.
Soluzione per f3: [0.92222484]; reale 0.922222
Tempo di esecuzione per f3: 0.0006670951843261719s
Velocità di convergenza per f3: 11 iter.
"""
```

Se $f_{1}, f_{3}$ hanno beneficiato di questo incremento di $\alpha$, in termini di tempo di esecuzione e di velocità di convergenza, _per $f_{2}$ è stata calcolata una soluzione sbagliata_. Il motivo è da trovarsi nel gradiente di $f_{2}$:
$$\nabla f_{2}(x_{1}, x_{2}) = [20(x_{1} - 1), 2(x_{2} - 2)]$$
La derivata parziale $\partial x_{1}$ ha un coefficiente per $x_{1}$ molto alto, nonostante venga decimato da $\alpha = 0.1$. Questo provoca una divergenza nel passo
$$x_{k+1} = x_{k} - \alpha \nabla f_{2}(x_{k})$$

Ci è sufficiente raddoppiare $\alpha$ ($=0.2$) per ottenere risultati disastrosi:
```python
"""
Algoritmo terminato per condizione su tolx.
Soluzione per f1: [2.99999889 0.99999963]; reale [3 1]
Tempo di esecuzione per f1: 0.0018014907836914062s
Velocità di convergenza per f1: 29 iter.

Soluzione per f2: [1.54613256e+48 2.00000000e+00]; reale [1 2]
Tempo di esecuzione per f2: 0.006291389465332031s
Velocità di convergenza per f2: 101 iter.

Soluzione per f3: [0.60695333]; reale 0.922222
Tempo di esecuzione per f3: 0.013980627059936523s
Velocità di convergenza per f3: 101 iter.
"""
```

E' importante notare che, sempre per $f_{2}$, il secondo membro $x_{2}$ viene calcolato correttamente. Significa che la _divergenza avviene solo e unicamente per $x_{1}$_: questo ci suggerisce che **la funzione in questione sia fondamentalmente schiacciata parallelamente all'asse $x_{2}$, tale che lo spostamento lungo $x_{1}$ sia estremamente ripido, mentre lungo $x_{2}$ sia più "morbido"**. Ci aspettiamo quindi che _le [[Insieme di livello|curve di livello]] di $f_{2}$ formino delle ellissi concentriche_.

Detto questo, l'algoritmo per $\alpha = 0.2$ consente solamente a $f_{1}$ di convergere. E' molto probabile che l'_antigradiente sia abbastanza basso da non permettere alcuna divergenza_, e ne è conferma il fatto che _continui a terminare per la condizione su `tolx`_ (funzione piatta).

Se aumentiamo gradualmente $\alpha$, notiamo uno strano comportamento di $f_{1}$: la velocità di convergenza aumenta sempre di più, raggiungendo il suo picco per $\alpha = 0.5$, dove converge in 1 sola iterazione; superato questo valore, il numero di iterazioni torna ad aumentare, raggiungendo la divergenza per $\alpha = 1$.

In realtà ogni funzione deve presentare un comportamento del genere, ma su scale di $\alpha$ possibilmente diverse (determinate dall'antigradiente e dal punto di partenza $x_{0}$). Lo dimostriamo provando a plottare il numero di iterazioni in funzione di $\alpha$ per ogni funzione $f$.

Partiamo proprio da $f_{1}$:
```python
alphas = np.linspace(0.01, 1, 1000)
iters = []
for alpha in alphas:
	start = time.time()
	x1, rel_err1, _, _ = GD(f1, df1, np.array([0, 0]), x1_true, alpha)
	end = time.time()
	iters.append(len(rel_err1))

plt.plot(alphas, iters, 'r-')
plt.xlabel(r"$\alpha$")
plt.ylabel("Iterazioni")
plt.grid()
plt.show()
```
![[calcolo-hw-2-ottimiz-gd1.png]] ^70c129

La curva descrive proprio il comportamento osservato in precedenza.

<u>Attenzione</u>: _se il numero di iterazioni è uguale a 101 allora la convergenza non è assicurata_. E' necessario _filtrare le soluzioni_, infatti, _in base all'errore relativo commesso_ (lo vedremo in seguito).

Per $f_{2}$ otteniamo un grafico estremamente diverso:
![[calcolo-hw-2-ottimiz-gd2.png]]

E se ci si concentra sull'intervallo $[0.05, 0.1]$:
![[calcolo-hw-2-ottimiz-gd3.png]]

L'_asimmetria del numero di iterazioni rispetto al valore di $\alpha$_ è causata dallo _schiacciamento provocato dal termine $10$ che moltiplica il primo membro della funzione_ $(x_{1} - 1)^{2}$.

Per $f_{3}$, infine, otteniamo:
![[calcolo-hw-2-ottimiz-gd4.png]]
con una serie di `RuntimeWarning` di _overflow_, sia su $f_{3}$ che su $f_{3}'$.
Oltre una certa soglia, il passo $\alpha$ è così alto da provocare overflow dopo poche iterazioni, con conseguente _errore nella valutazione delle condizioni di uscita_ (criteri di arresto). Per cui, i dati da considerare validi sono quelli che si trovano nell'intervallo $[0.01, 0.2]$:
![[calcolo-hw-2-ottimiz-gd5.png]]

Abbiamo valutato le velocità di convergenza dell'algoritmo al variare di $\alpha$ su tutte e 3 le funzioni. Facciamo lo stesso per quanto riguarda i tempi di esecuzione, tenendo a mente che sono influenzati dai processi in esecuzione sul [[Sistema operativo|sistema operativo]]. Per questo motivo, _per ogni valore dello step-size faccio una media dei tempi di 10 esecuzioni_.
Quello che ci aspettiamo dai successivi grafici, è una **relazione pressoché lineare tra numero di iterazioni e tempo di esecuzione**: il passo $\alpha$ è fisso, non bisogna calcolarlo ogni volta, per cui se il numero di iterazioni è basso allora lo sarà anche il tempo di esecuzione.

Per $f_{1}$:
```python
alphas = np.linspace(0.01, 1, 1000)
times = []
for alpha in alphas:
	iters = 0
	for _ in range(10):
		start = time.time()
		x1, rel_err1, _, _ = GD(f1, df1, np.array([0, 0]), x1_true, alpha)
		end = time.time()
		iters += end-start
	times.append(iters/10)

plt.plot(alphas, times, 'r-')
plt.xlabel(r"$\alpha$")
plt.ylabel("Tempo di esecuzione")
plt.grid()
plt.show()
```
![[calcolo-hw-2-ottimiz-gd6.png]]

A patto di eccezioni, l'andamento segue la curva delle iterazioni.

Per $f_{2}$:
![[calcolo-hw-2-ottimiz-gd7.png]]
che ingrandito nell'intervallo d'interesse $[0.05, 0.1]$ diventa
![[calcolo-hw-2-ottimiz-gd8.png]]
, non proprio in linea con il numero di iterazioni... ma c'è una spiegazione. **Ci mette meno tempo quando fa il massimo delle iterazioni (101) rispetto a quanto ce ne metterebbe se ne facesse meno, solo ed esclusivamente per la stampa sulla condizione di arresto di `tolx`**:
```python
if (np.linalg.norm(x - x0) <= tolx):
	print(f"Algoritmo terminato per condizione su tolx.")
```
Se _commento il `print`_ e come corpo dell'`if` scrivo `pass`, _il tempo si allinea, colmando la discrepanza con il numero di iterazioni_:
![[calcolo-hw-2-ottimiz-gd9.png]]

Procedo quindi per $f_{3}$:
![[calcolo-hw-2-ottimiz-gd10.png]]
che nell'intervallo d'interesse $[0.01, 0.2]$ diventa
![[calcolo-hw-2-ottimiz-gd11.png]]
in linea con il numero di iterazioni.

###### Backtracking
Modifichiamo l'algoritmo di discesa del gradiente tale che implementi, nella scelta dello step-size $\alpha$, l'_algoritmo di backtracking_ sulla base della [[Condizione di Armijo|condizione di Armijo]]:
```python
def backtracking(f, df, x, alpha=1, rho=0.5, c=1e-4):
	while f(x - alpha * df(x)) > f(x) - c * alpha * np.linalg.norm(df(x))**2:
		alpha *= rho
	return alpha


def GD_backtracking(f, df, x0, x_true, maxit=100, tolf=1e-6, tolx=1e-6):
	k = 0
	rel_err = np.zeros((maxit+1, ))
	obj_val = np.zeros((maxit+1, ))
	grad_norm = np.zeros((maxit+1, ))
	
	condizione = True
	while condizione:
		alpha = backtracking(f, df, x0, alpha=1)
		x = x0 - alpha * df(x0)
		
		rel_err[k] = np.linalg.norm(x - x_true) / np.linalg.norm(x_true)
		obj_val[k] = f(x)
		grad_norm[k] = np.linalg.norm(df(x))
		
		condizione = (k < maxit) and (np.linalg.norm(df(x)) > tolf) and (np.linalg.norm(x - x0) > tolx)
		
		if (np.linalg.norm(x - x0) < tolx):
			print(f"Algoritmo terminato per condizione su tolx.")
		
		k = k + 1
		x0 = x
	
	if k < maxit:
		rel_err = rel_err[:k]
		obj_val = obj_val[:k]
		grad_norm = grad_norm[:k]
	
	return x, rel_err, obj_val, grad_norm
```

Invochiamo `GD_backtracking` su tutte e 3 le funzioni, ottenendo:
```python
"""
Soluzione per f1: [3. 1.]; reale [3 1]
Tempo di esecuzione per f1: 0.0001633167266845703s
Velocità di convergenza per f1: 1 iter.

Algoritmo terminato per condizione su tolx.
Soluzione per f2: [1.00000031 1.99999816]; reale [1 2]
Tempo di esecuzione per f2: 0.0032567977905273438s
Velocità di convergenza per f2: 55 iter.

Algoritmo terminato per condizione su tolx.
Soluzione per f3: [0.92222458]; reale 0.922222
Tempo di esecuzione per f3: 0.005258083343505859s
Velocità di convergenza per f3: 18 iter.
"""
```
un netto miglioramento in termini di velocità di convergenza _solo per $f_{1}, f_{2}$_, considerando che per $\alpha = 0.07$ fisso si aveva
```python
"""
Algoritmo terminato per condizione su tolx.
Soluzione per f1: [2.99999484 0.99999828]; reale [3 1]
Tempo di esecuzione per f1: 0.001950979232788086s
Velocità di convergenza per f1: 88 iter.

Algoritmo terminato per condizione su tolx.
Soluzione per f2: [1.         1.99999459]; reale [1 2]
Tempo di esecuzione per f2: 0.0019028186798095703s
Velocità di convergenza per f2: 85 iter.

Algoritmo terminato per condizione su tolx.
Soluzione per f3: [0.92222465]; reale 0.922222
Tempo di esecuzione per f3: 0.0006880760192871094s
Velocità di convergenza per f3: 13 iter.
"""
```

Generalmente possiamo quindi osservare che:
- per $f_{1}$ il valore dimezzato di $\alpha$ (che partendo da $1$ va a $0.5$, perché il fattore di riduzione `rho=0.5`) consente una convergenza istantanea alla soluzione --> [[Calcolo numerico - HW. 2#^70c129|lo sapevamo già]];
- per $f_{2}$ il _numero di iterazioni è nettamente diminuito_, ma il _tempo di esecuzione sembra invece aumentato_;
- invece, per $f_{3}$ sia il _numero di iterazioni che il tempo di esecuzione è leggermente aumentato_;

Le ultime due osservazioni si giustificano se si considerano i valori ottimali di $\alpha$ delle due funzioni, tendenzialmente molto bassi: ricordiamo infatti che la potenza negativa del $2$ "migliore" come valore di $\alpha$ per $f_{2}$ è $\frac{1}{16}$, mentre per $f_{3}$ è $\frac{1}{8}$. Quindi, _tendenzialmente_, l'algoritmo di backtracking che parte da $\alpha = 1$ deve iterare:
- per $f_{2}$ --> $$\log_{2}\left(\frac{1}{16}\right) = 4$$
- per $f_{3}$ --> $$\log_{2}\left(\frac{1}{8}\right) = 3$$

volte.

Il punto è che l'**algoritmo di backtracking considera le condizioni di Armijo, che non per forza coincidono con gli $\alpha$ "migliori" per $f_{2}, f_{3}$**. Queste, se soddisfatte, _garantiscono la convergenza, cercando degli step-size sufficientemente grandi da consentire una rapida discesa, ma che allo stesso tempo non causino divergenza_. Tuttavia non sono gli $\alpha$ "perfetti", _a meno che non questi non coincidano tutti con delle potenze del $2$ negative_!

Questo spiega il motivo per cui per $f_{2}$ si ha un miglioramento in termini di velocità di convergenza mentre per $f_{3}$ no.

Infatti, il numero di iterazioni del backtracking per $f_{2}$ e $f_{3}$ girano intorno, rispettivamente, a $4$ e $3$, ma non sono sempre quei valori:
```python
"""
f2: 4 3 4 3 3 4 3 3 4 3 4 2 4 3 4 3 3 4 3 3 4 3 4 2 4 3 4 3 3 4 3 3 4 3 4 2 4 3 4 3 3 4 3 3 4 3 4 2 4 3 4 3 3 4 3

f3: 1 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3 3
"""
```

Per esempio, il primo valore di $\alpha$ per $f_{3}$ è $1$: significa che soddisfa le condizioni di Armijo per $x_{0} = 0$. **Sappiamo che sarebbe meglio se $\alpha$ fosse uguale a $0.07$ sempre** (ci metterebbe 5 iterazioni in meno), **ma finché soddisfa tali condizioni va bene**.

Per poter ottenere dei risultati più veritieri riguardanti i tempi di esecuzione, facciamo una loro media su 10 esecuzioni per ogni funzione:
```python
"""
Tempo di esecuzione MEDIO per f1: 0.00027048587799072266s
Tempo di esecuzione MEDIO per f2: 0.0069849491119384766s
Tempo di esecuzione MEDIO per f3: 0.0064263582229614254s
"""
```
che confrontati con i tempi medi per il passo fisso considerando gli $\alpha$ ottimali per ogni $f$
```python
"""
Tempo di esecuzione MEDIO per f1: 6.444454193115235e-05s
Tempo di esecuzione MEDIO per f2: 0.0025653839111328125s
Tempo di esecuzione MEDIO per f3: 0.0007040977478027343s
"""
```
possiamo osservare che _per tutti i casi si ha un netto vantaggio in termini di tempo nell'utilizzo del passo fisso_!
E' interessante addirittura notare che per $f_{2}$, con passo fisso ottimale, _il numero di iterazioni è $67$, maggiore dei $55$ del backtracking_. Nonostante questo, il tempo è nettamente inferiore: _il numero di cicli del `while` del backtracking influisce non poco sul risultato_.

<u>Attenzione</u>: **per "passo fisso ottimale", in realtà, si intende il passo fisso migliore per $x_{0}$, in ogni $f$**. Lo dimostra il fatto che _il numero di iterazioni per $f_{2}$ dell'algoritmo con backtracking sia inferiore rispetto a quello per passo fisso, nonostante $\alpha$ sia scelto come ottimale (minor numero di iterazioni)_.

###### Confronto
In conclusione, abbiamo sperimentato pregi e difetti di entrambi i metodi. In particolare:
- in termini di _velocità di convergenza_, non per forza il passo fisso produce risultati migliori del backtracking, e viceversa --> questo perché **da un lato il passo fisso è limitato da una scelta dello step-size che viene calcolata a partire da $x_{0}$**, infatti l'$\alpha$ ottimale (che fa convergere in meno iterazioni) è scelto staticamente; dall'altro **la dinamicità dell'algoritmo di backtracking non garantisce**, per le condizioni di Armijo, **la scelta di $\alpha$ ottimale**.
- in termini di _tempo di esecuzione_, almeno per quanto riguarda i casi visti finora, **l'algoritmo di discesa del gradiente con backtracking sembra essere sempre più lento di quello con passo fisso per $\alpha$ ottimale** --> per $f_{1}$ il valore di $\alpha$ dev'essere dimezzato una volta per raggiungere $0.5$, per cui rispetto al passo fisso ci sono 3 istruzioni in più da eseguire (2 controlli e un'operazione aritmetica); per $f_{2}, f_{3}$ l'algoritmo di backtracking richiede in media $\approx 3$ iterazioni per trovare l'$\alpha$ corretto, il che influisce molto sulle prestazioni generali dell'algoritmo.

##### Norma del gradiente
Si vuole adesso visualizzare, per ogni iterato $x_{k}$, il valore della norma del gradiente $\|\nabla f(x_{k})\|_{2}$, sia con passo fisso che con backtracking. Sulla base di questo, si vuole valutare la qualità dei metodi. Infatti _la norma del gradiente è_, tra i _criteri di arresto della discesa del gradiente_, sicuramente _quello più importante_: è il valore con il quale **si valuta la convergenza verso la soluzione**, _sfruttando la condizione necessaria del prim'ordine_.

Ci aspettiamo che _per $\alpha$ non ottimali, nel passo fisso, l'algoritmo termini o per tolleranza `tolx`, ossia che "si arrenda", oppure per numero di iterazioni_. Allo stesso modo, _con backtracking non è garantito che si giunga a una convergenza tale che il gradiente sia sufficientemente piccolo da far uscire l'algoritmo per tolleranza su `tolf`_: dipende molto anche dal punto di partenza $x_{0}$ e dalla forma della funzione $f$.

Ad ogni modo, _più velocemente il gradiente scende meglio è, perché significa che l'algoritmo converge in pochi passi alla soluzione_.

###### Passo fisso
Per la discesa con passo fisso, scegliamo i valori di $\alpha$ più significativi per le 3 funzioni:
$$[0.07, 0.08, 0.02, 0.1, 0.2, 0.4, 0.5]$$

Il codice è il seguente:
```python
alpha = 0.07
x1_true = np.array([3, 1])
x2_true = np.array([1, 2])
x3_true = 0.922222

x1, rel_err1, _, grad_norm1 = GD(f1, df1, np.array([0, 0]), x1_true, alpha)
x2, rel_err2, _, grad_norm2 = GD(f2, df2, np.array([0, 0]), x2_true, alpha)
x3, rel_err3, _, grad_norm3 = GD(f3, df3, np.array([0]), x3_true, alpha)

plt.title(rf"$\alpha = {alpha}$")
mg = max(len(grad_norm1), len(grad_norm2), len(grad_norm3))
plt.plot(range(mg), [1e-6]*mg, 'k--')
plt.plot(range(len(grad_norm1)), grad_norm1, 'r-')
plt.plot(range(len(grad_norm2)), grad_norm2, 'g-')
plt.plot(range(len(grad_norm3)), grad_norm3, 'b-')
plt.xlabel("Iterazioni")
plt.ylabel("Norma del gradiente")
plt.legend(["tolf", r"$f_1$", r"$f_2$", r"$f_3$"])
plt.grid()
plt.yscale("log")
plt.show()
```

<u>Nota bene</u>: stampiamo i grafici in scala logaritmica sulle ordinate, per migliore la visualizzazione dei risultati.

Per $\alpha = 0.07$ si ha:
![[calcolo-hw-2-ottimiz-grad1.png]]

Notiamo che _in nessuno dei 3 casi viene raggiunta la tolleranza sulla norma del gradiente_: tutti e 3 gli algoritmi terminano infatti su `tolx`.
Inoltre, vediamo che per $f_{3}$, nelle prime $\approx 2$ iterazioni, **la norma del gradiente sale**. Questo è con tutta certezza una conseguenza della non-convessità di $f_{3}$: **se la funzione fosse convessa non ci potrebbe essere un'oscillazione della norma del gradiente al variare di $x_{k}$, ma solo una sua discesa**, _per un $\alpha$ sufficientemente basso da non far divergere l'algoritmo_. In altre parole, l'algoritmo di discesa del gradiente su una funzione convessa può solo far diminuire la norma del gradiente, _se viene scelto un $\alpha$ appropriato_.

Per $\alpha = 0.08$, invece, abbiamo:
![[calcolo-hw-2-ottimiz-grad2.png]]

Di nuovo, $f_{1}$ e $f_{2}$ terminano per `tolx`, mentre _$f_{3}$ supera la tolleranza sulla norma del gradiente_. In realtà, per dirla tutta, anche $f_{3}$ termina per `tolx` (viene stampata la stringa a schermo): _semplicemente termina per entrambe le condizioni_.

Per $\alpha = 0.02$ si ha:
![[calcolo-hw-2-ottimiz-grad3.png]]
ossia un netto "peggioramento" per tutte e 3 le funzioni. Infatti:
- $f_{1}$ e $f_{2}$ terminano addirittura per numero di iterazioni;
- $f_{3}$ termina per `tolx` ma su un valore della norma del gradiente inferiore a quello per $\alpha = 0.07$.

In generale _si conferma che un abbassamento eccessivo dello step-size richiede un numero di iterazioni superiore per poter garantire una convergenza sulle tolleranze_.

Quindi proviamo adesso ad aumentare $\alpha$ a $0.1$:
![[calcolo-hw-2-ottimiz-grad4.png]]

Possiamo notare che:
- per $f_{3}$ si ha un risultato simile che per $\alpha = 0.08$ --> tale valore rientra comunque nel range di quelli "ottimali" (per $f_{3}$);
- $f_{1}$ migliora nella sua discesa uscendo per `tolx` su un valore della norma del gradiente più bassa rispetto ai casi precedenti --> anche $0.1$ rientra nei valori ottimali di $\alpha$ (per $f_{1}$);
- la _norma del gradiente di $f_{2}$, invece, rimane invariate per tutte le 100 iterazioni_ --> **abbiamo trovato un valore di $\alpha$ che fa alternare l'algoritmo tra due (o più!) punti di eguale valore della norma del gradiente**, senza mai farlo convergere.

Tutte _queste informazioni contribuiscono a suggerirci nuovi indizi sulle conformazioni delle funzioni_, che dalla sola velocità di convergenza e tempo di esecuzione non eravamo in grado di sapere.
Infatti, un altro particolare che si può notare, questa volta su **$f_{1}$, è che per tutti gli $\alpha$ testati la discesa della norma del suo gradiente è perfettamente logaritmica** (nel grafico lineare perché su scala logaritmica). Questo si spiega dall'equazione che descrive la funzione:
$$(x_{1}-3)^{2} + (x_{2}-1)^{2}$$
Questa è una **funzione radiale** meglio nota come **distanza quadratica**, _definita in curve di livello come cerchi concentrici di centro $(3, 1)$_ (punto di minimo). Non importa perciò il punto $x_{0}$ di partenza dell'algoritmo, ma più che altro il valore dello step-size $\alpha$: pensandoci (dal grafico del passo fisso), per valori nell'intervallo $[0.01, 0.5[$ e $]0.5, 0.8]$ ci sarà una convergenza logaritmica; per $\alpha = 0.5$ convergerà in 1 iterazione; sicuramente in $]0.8, +\infty[$ _esisterà un $\alpha$ tale che l'algoritmo si alterni tra due punti della funzione con stessa norma del gradiente_.

Per $\alpha = 0.2$ si ha:
![[calcolo-hw-2-ottimiz-grad5.png]]

In questo caso:
- sembra che abbiamo trovato per $f_{3}$ il valore di $\alpha$ che rende statica la norma del gradiente per tutte le 100 iterazioni;
- per $f_{2}$ ci stiamo avvicinando al valore $0.5$, per cui tende a convergere alla soluzione sempre in meno iterazioni e con maggiore precisione, ma ancora non supera la tolleranza `tolf`;
- infine già per $f_{3}$ abbiamo superato la soglia oltre il quale l'algoritmo diverge, producendo norme del gradiente sempre più grandi.

<u>Osservazione</u>: viene a questo punto da chiedersi _se per ogni funzione $f$ e ogni punto $x_{0}$ esista un $\alpha$ tale che l'algoritmo di discesa del gradiente finisca per alternarsi tra $n$ punti della funzione senza mai convergere né divergere_.

Per $\alpha = 0.4$ si confermano le tendenze previste nel caso precedente:
![[calcolo-hw-2-ottimiz-grad6.png]]

In particolare:
- $f_2$ continua a divergere;
- $f_{1}$ supera la soglia di `tolf`, terminando per tolleranza sulla norma del gradiente;
- $f_{3}$ sembra essere _caratterizzata da oscillazioni sulla norma del gradiente_ --> ricordando il grafico sul passo fisso (iterazioni al variare di $\alpha$), sembra che per $\alpha = 0.4$ l'algoritmo trovi un punto di equilibrio che effettivamente non faccia divergere il risultato (infatti non produce neanche i precedenti `RuntimeWarning` di _overflow_).

Infine, per $\alpha = 0.5$, si ha:
![[calcolo-hw-2-ottimiz-grad7.png]]

In questo caso, $f_{3}$ diverge istantaneamente, con una _crescita addirittura più veloce dell'esponenziale_, come nel caso di $f_{2}$. Il _grafico della norma del gradiente di $f_{1}$, invece, non appare perché la convergenza è istantanea_.

###### Backtracking
Non ci resta quindi che plottare l'unico grafico che si ottiene utilizzando il backtracking, e confrontarlo con i precedenti calcolati con passo fisso:
![[calcolo-hw-2-ottimiz-grad8.png]]

Notiamo che:
- il grafico per $f_{1}$ non appare, per le ragioni già conosciute;
- la norma del gradiente di $f_{3}$ scende con un andamento logaritmico, senza mostrare il picco del gradiente come avviene per il passo fisso --> avviene infatti che il primo valore di $\alpha$ calcolato dal backtracking è $0.5$, sufficientemente alto da "atterrare" in un punto $x_{1}$ di $f_{3}$ cui valore della norma del gradiente è inferiore a quello in $x_{0}$; tutti i successivi valori di $\alpha$ sono $2^{-3} = \frac{1}{8}$;
- la norma del gradiente di $f_{2}$, invece, non è minimamente stabile, e oscilla ad ogni iterazione da un valore più basso a uno più alto, ma generalmente scende fino ad uscire per `tolx` --> _siamo già a conoscenza della "ellitticità" di $f_{2}$, dal quale molto probabilmente deriva tale oscillazione_ (lo verificheremo nell'ultimo punto dell'homework).

###### Confronto
Se consideriamo come fattore di precisione l'uscita dell'algoritmo per tolleranza sulla norma del gradiente (assumendo di non essere in un problema test), allora risulta chiaro che **per $\alpha$ scelti appositamente** (gli "ottimali"), **il passo fisso produce risultati più precisi**. Infatti, tralasciando il caso speciale di $f_{1}$, **sia per $f_{2}$ che per $f_{3}$ la discesa del gradiente con backtracking termina su tolleranza `tolx`**.

Ma non solo! Sempre per $\alpha$ appositi, **l'algoritmo con passo fisso produce risultati più precisi in meno iterazioni**. In altri termini, per l'algoritmo con passo fisso **la velocità di convergenza e la precisione sembrano non essere proprietà "inversamente proporzionali"**: non c'è un _trade-off_ tra queste due proprietà!
Già ce lo suggeriva il fatto che per $\alpha = 0.5$, l'algoritmo su $f_{1}$ convergesse in $1$ iterazione alla soluzione esatta (gradiente pari a 0).

Di conseguenza, la discesa del gradiente con **backtracking non è sinonimo di maggiore velocità né di maggiore precisione**, ma solo e unicamente di **convergenza assicurata**.

<u>Nota bene</u>: il tutto, tra l'altro, dipende molto dall'implementazione dell'algoritmo di backtracking. Per esempio, il fattore di riduzione $\rho$ gioca un ruolo fondamentale: _se lo variassimo potremmo favorire velocità di convergenza e precisione di alcune funzioni_.

##### Errori relativi
Procediamo adesso con l'analisi degli errori relativi sempre su entrambi i casi di algoritmi, andando a commentare i risultati rispetto anche alle osservazioni fatte in precedenza.
Infatti, l'_errore relativo è a tutti gli effetti lo strumento di misura reale per mostrare la precisione delle soluzioni calcolate_ (ricordando che si tratta di problemi test).

Quello che ci aspettiamo è, in linea teorica, una _sorta di equivalenza tra errori relativi e norme del gradiente_.

###### Passo fisso
Mostriamo i grafici degli errori relativi sugli stessi casi di $\alpha$ precedenti (ometto il codice).

Per $\alpha = 0.07$ si ha:
![[calcolo-hw-2-ottimiz-errrel1.png]]

Come previsto, almeno in questo primo caso abbiamo una netta somiglianza del grafico con quello che mostra la norma del gradiente. Non devono essere uguali, anzi: _la norma del gradiente è un valore dipendente da $f(x_{k})$, mentre l'errore relativo da $x_{k}$_.

Ciò che si nota di importante dal grafico è che, comunque, tutti gli algoritmi raggiungono dopo un certo numero di iterazioni (chi prima chi dopo) una distanza dalla soluzione molto bassa.

Un altro dettaglio è quel **lieve incremento dell'errore relativo delle ultime due iterazioni su $f_{3}$**. Questo non coincide con la discesa della norma del gradiente, e stupisce il fatto che comunque l'algoritmo termini per `tolx`. Anzi, è un assurdo vero e proprio: se supponiamo che $x^{*} = 0.922222$ sia il punto di minimo globale di $f_{3}$, allora **non è possibile che l'algoritmo di discesa del gradiente con passo fisso produca 2 iterazioni di seguito da $x_{k} \approx x^{*}$ tale che $x_{k+2}$ sia più distante da $x^{*}$ di quanto lo sia $x_{k+1}$**: _vorrebbe dire che la direzione di discesa dell'antigradiente è sbagliata_!
Il motivo è un errore nel calcolo della soluzione $x^{*}$: non si tratta di $0.922222$ ma di $0.922225$. Modificando questo valore, il grafico viene
![[calcolo-hw-2-ottimiz-errrel2.png]]

Per $\alpha = 0.08$ si ha:
![[calcolo-hw-2-ottimiz-errrel3.png]]
ossia una generale diminuzione del numero di iterazioni per raggiungere gli stessi errori relativi, sia in $f_{1}$ che in $f_{2}$ che in $f_{3}$.

Andiamo adesso a diminuire $\alpha$ a $0.02$:
![[calcolo-hw-2-ottimiz-errrel4.png]]
sempre in linea con i risultati sulla norma del gradiente.

Torniamo su valori più alti, per $\alpha = 0.1$:
![[calcolo-hw-2-ottimiz-errrel5.png]]

Anche questo sembra proprio confermare la relazione tra l'errore relativo e la norma del gradiente. Infatti per questo valore c'è una buona convergenza per $f_{1}$ e $f_{3}$, mentre l'algoritmo in $f_{2}$ si "blocca" in un loop tra $n$ valori (in seguito si scopriranno quanti e quali sono) equidistanti dalla soluzione $x^{*}$.

Per $\alpha = 0.2$, invece, avremo:
![[calcolo-hw-2-ottimiz-errrel6.png]]

Ancora una volta il risultato è simile a quello della norma del gradiente, con una differenza interessante: l'errore relativo in $f_{3}$ sembra oscillare nel decorso delle 100 iterazioni tra due distinti valori. Questo ci suggerisce due cose sulla funzione:
- l'algoritmo per lo step-size $\alpha = 0.2$ si **alterna su 2 soli valori**;
- questi **due punti $x_{k}$ e $x_{j}$ hanno stesso valore della norma del gradiente, ma non la stessa distanza dalla soluzione $x^{*}$**!

Per $\alpha = 0.4$ si ha:
![[calcolo-hw-2-ottimiz-errrel7.png]]
sempre in linea con i risultati sulla norma del gradiente.

Infine per $\alpha = 0.5$, avremo:
![[calcolo-hw-2-ottimiz-errrel8.png]]
per cui vale lo stesso discorso fatto per la norma del gradiente.

###### Backtracking
Anche in questo caso, allora, mostriamo l'unico grafico prodotto dall'esecuzione dell'algoritmo con backtracking
![[calcolo-hw-2-ottimiz-errrel9.png]]
su cui possiamo produrre le seguenti considerazioni:
- anche in questo caso, ovviamente, l'algoritmo con backtracking converge alla soluzione per $f_{1}$ istantaneamente, per cui non appare nel grafico;
- per $f_{2}$, possiamo notare con molta attenzione la **ripetizione di una sorta di "pattern" nella discesa dell'errore relativo** --> in realtà, **anche nella norma del gradiente si intravede un pattern, di cui non ci siamo accorti perché era più difficile da individuare**! La spiegazione? E' molto probabile che il percorso composto dagli iterati $x_{k}$ (vettori) per $f_{2}$ costituisca una sorta di _spirale_, tale che dopo $j$ iterazioni $x_{k}$ si trovi sulla traiettoria che collega $x_{k-j}$ a $x^{*}$;
- per $f_{3}$ _il fatto che l'ultima iterazione produca un errore relativo più ampio della precedente non è un problema_ (l'importante è che non ce ne siano 2 di fila così).

###### Confronto
Il confronto tra algoritmo con passo fisso e con backtracking rispetto all'errore relativo è assolutamente equivalente a quello che trattato rispetto alla norma del gradiente.

##### Plot e cammino
In quest'ultimo capitolo dell'esperimento, _andiamo a confermare o confutare tutte le osservazioni fatte in precedenza in merito alle 3 funzioni e al comportamento dell'algoritmo, sia con passo fisso che con backtracking_.
Abbiamo infatti accumulato finora una serie di ipotesi, e _mostrando i grafici delle 3 funzioni e del cammino percorso dalla discesa del gradiente in entrambe le sue forme_, verificheremo la loro veridicità.

###### $f_{3}$
All'inizio dell'esperimento, abbiamo dimostrato matematicamente che $f_{3}$ non è convessa. Questo, fondamentalmente, _non ci assicura che l'algoritmo di discesa del gradiente, per ogni punto di partenza $x_{0}$, converga al minimo globale_.
Mostriamo quindi il grafico della funzione nell'intervallo $[-3, 3]$.
```python
x = np.linspace(-3, 3, 100)
y = f3(x)

plt.title(r"$f_3$")
plt.plot(x, y, 'r-')
plt.grid()
plt.show()
```
![[calcolo-hw-2-ottimiz-plot1.png]]

Notiamo proprio che, come da teoria, $f_{3}$ non è assolutamente convessa, e presenta due punti di minimo, il primo dei quali è in $[-2, -1]$. L'algoritmo partiva da $x_{0} = 0$, un punto molto fortunato: _il valore dell'antigradiente puntava verso il minimo globale $0.922225$_, consentendo di convergere verso la soluzione al problema di ottimizzazione. Se però, tuttavia, proviamo a spostare il punto di partenza a $- \frac{1}{2}$, la soluzione calcolata dall'algoritmo con passo fisso (per $\alpha = 0.07$), risulta essere
```python
x3, rel_err3, _, grad_norm3 = GD(f3, df3, np.array([-1/2]), x3_true, alpha)
print(x3[0])

# Output: -1.2322389
```
che dal grafico sembrerebbe proprio essere quella corretta.

Se proviamo ad eseguire l'algoritmo con backtracking, il risultato è relativamente simile:
```python
x3, rel_err3, _, grad_norm3 = GD_backtracking(f3, df3, np.array([-1/2]), x3_true)
print(x3[0])

# Output: -1.2322392
```
ma se proviamo a stampare il numero di iterazioni dell'algoritmo di backtracking per ogni iterazioni, otteniamo:
```python
# 0 1 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2 2
```
Avendo scelto come punto di partenza $-\frac{1}{2}$, che è _poco sbilanciato verso la soluzione $-1.2322392$_, l'algoritmo di backtracking per la prima iterazione $x_{1}$ non dimezza neanche una volta il valore di $\alpha$, _mantenendolo a $1$_.

Proviamo adesso a porre il valore di $x_{0}$ su un estremo sinistro della funzione, come $-3$, e ad eseguire l'algoritmo con passo fisso $\alpha = 0.07$:
```python
# Output: 0.922225
```
L'**algoritmo ha converso sul minimo globale**! Se magicamente abbasso $\alpha$ a $0.03$, ecco che l'algoritmo torna a convergere sul minimo locale. Ci chiediamo allora se, _la versione dell'algoritmo con backtracking_ risolva autonomamente questo problema, _convergendo al minimo più vicino_:
```python
# Output: -1.232239
```
**La risposta è sì**! Addirittura, la pendenza (antigradiente) è così alta in $x_{0} = -3$, che nella prima iterazione l'algoritmo di backtracking dimezza ben $4$ volte $\alpha = 1$. Testiamolo fino in fondo, ponendo $x_{0} = -10$, e vediamo se anche in questo caso l'algoritmo è capace di convergere esclusivamente al minimo più vicino:
```python
# Output: -1.232239
```
Lo fa! In questo caso $\alpha$ viene all'inizio dimezzato $8$ volte!

Questa è una grande proprietà dell'algoritmo di discesa del gradiente con backtracking: se anche la funzione in analisi non è convessa (e quindi presumibilmente prevede più punti di minimo locale), l'**algoritmo con backtracking convergerà al minimo più vicino al punto di partenza $x_{0}$**. E' un enorme vantaggio rispetto all'algoritmo con passo fisso: con quest'ultimo, in caso di funzione non convessa, non si sa dove mettere le mani! Una _lieve variazione di $\alpha$ potrebbe far convergere l'algoritmo a un altro punto di minimo_, senza tenere in considerazione il caso della divergenza.
In altri termini, se si vuole fare una scansione dei punti di minimi di una funzione per identificare quello globale, se si utilizza il passo fisso è necessario _per ogni $x_{0}$ analizzata variare anche lo step-size per trovare il punto di minimo più vicino a $x_{0}$_; invece con backtracking questo processo è _completamente automatizzato e ci si può concentrare sulla sola variazione di $x_{0}$_.

###### $f_{1}$
Conosciamo già da un punto di vista puramente matematico alcune proprietà di $f_{1}$. Ora mostriamo le sue curve di livello usando la funzione della libreria `matplotlib` chiamata `contour`. I passaggi per mostrare tale grafico si riassumono nel seguente codice:
```python
x = np.linspace(-1, 5, 100)
y = np.linspace(-1, 5, 100)
X, Y = np.meshgrid(x, y)
Z = f1([X, Y])

plt.title(r"$f_1$")
plt.contour(X, Y, Z, 100)
plt.axis("scaled")
plt.colorbar()
plt.grid()
plt.show()
```
dove:
- `np.meshgrid(x, y)` è una funzione che dati due array `x` e `y` restituisce due matrici `X` e `Y` tali che `X[i, j] = x[i]` e `Y[i, j] = y[j]` --> estremamente utile per la rappresentazione di curve di livello;
- `plt.contour(X, Y, Z, 100)` è la funzione che disegna le curve di livello rispetto alla meshgrid `X, Y` e alla funzione `Z` (valori della funzione $f_{1}$), e `100` è il numero di curve da disegnare;
- `plt.colorbar()` serve a mostrare una barra laterale funge da legenda, associando ai colori delle curve di livello i valori assunti dalla funzione $f_{1}$.

Il risultato è il seguente:
![[calcolo-hw-2-ottimiz-plot2.png]]

Come ci aspettavamo, $f_{1}$ è una funzione radiale centrata in $(3, 1)$, e il minimo globale è $f(3, 1) = 0$.

Ora, si vuole mostrare il comportamento dell'algoritmo di discesa del gradiente mostrando i percorsi a partire da $x_{0} = (0, 0)$, sia con passo fisso che con backtracking.
Per farlo usiamo l'oggetto `LineCollection` di `matplotlib`, tale che per ogni iterazione della discesa del gradiente il nuovo iterato $x_{k}$ sia connesso da un segmento a quello precedente $x_{k-1}$:
```python
lines = []

def GD(f, df, x0, x_true, alpha, maxit=100, tolf=1e-6, tolx=1e-6):
	...
	
	while condizione:
		x = x0 - alpha * df(x0)
		lines.append([x0, x])

		...


x = np.linspace(-1, 5, 100)
y = np.linspace(-1, 5, 100)
X, Y = np.meshgrid(x, y)
Z = f1([X, Y])

line_segments = LineCollection(lines, linewidths=1, colors='r')
points = [point for segment in lines for point in segment]
xp, yp = zip(*points)

plt.title(r"$f_1$")
plt.contour(X, Y, Z, 100)
plt.plot(xp, yp, 'ro', markersize=5, zorder=2)
plt.axis("scaled")
plt.colorbar()
plt.gca().add_collection(line_segments)
```

Fondamentalmente:
- accumuliamo tutti i segmenti dei punti della successione $x_{k}$ in `lines`;
- convertiamo questi segmenti in un oggetto `LineCollection`;
- estraiamo dai segmenti i singoli punti (`points`), per poi dividerli in coordinate con `zip(*points)` (`*points` serve a "srotolare" la lista di punti in una sequenza di punti, e `zip()` li divide in due liste di coordinate);
- mostriamo i punti con `plt.plot()`;
- mostriamo i segmenti aggiungendo la `LineCollection` a `plt.gca()`, ossia l'oggetto `Axes` corrente (bisognerebbe usare un `plt.subplot()`...).

Per $\alpha = 0.07$, il risultato è il seguente:
![[calcolo-hw-2-ottimiz-plot3.png]]

Proviamo adesso per i più "iconici" valori di $\alpha$, prima di passare al backtracking. In modo particolare, man mano che $\alpha$ cresce dovremmo vedere sempre meno pallini rossi, fino a che per $\alpha = 0.5$ non otterremo 2 soli punti ($x_{0}$ e $x^{*}$); quindi per $\alpha > 0.5$ dovremmo cominciare a sperimentare un'alternanza di valori degli iterati $x_{k}$, tutti sulla stessa traiettoria (la retta che passa per $x_{0}$ e $x^{*}$), tale che fissato un certo $\beta > 0.5$:
- per $\alpha < \beta$ l'algoritmo converge;
- per $\alpha = \beta$ l'algoritmo si alterna tra due valori mantenendo la stessa distanza da $x^{*}$;
- per $\alpha > \beta$ l'algoritmo diverge.

Proviamo, partendo da $\alpha = 0.4$:
![[calcolo-hw-2-ottimiz-plot4.png]]

Quindi per $\alpha = 0.5$:
![[calcolo-hw-2-ottimiz-plot5.png]]

Ora per $\alpha = 0.7$:
![[calcolo-hw-2-ottimiz-plot6.png]]

Intuitivamente, si deduce che **il valore di $\alpha$ per il quale l'algoritmo si alterna tra due valori senza mai convergere né divergere è il doppio di quello che consente di convergere in un'iterazione**, ovvero $\alpha = 1.0$:
![[calcolo-hw-2-ottimiz-plot7.png]]

Proviamo quindi ad aumentare leggermente $\alpha$ portandolo anche solo a $1.002$:
![[calcolo-hw-2-ottimiz-plot8.png]]
appunto l'algoritmo diverge.

E' il momento adesso di provare a vedere l'esecuzione dell'algoritmo con backtracking:
![[calcolo-hw-2-ottimiz-plot9.png]]

E' appunto equivalente all'esecuzione con passo fisso per $\alpha = 0.5$.

###### $f_{2}$
La funzione $f_{2}$, tra le 3, è quella più interessante da studiare. In particolare vogliamo mostrare su grafico il suo comportamento per certi valori di $\alpha$ (nel caso del passo fisso), e la "spirale" che si dovrebbe creare con la scelta di $\alpha$ con backtracking.

Partiamo plottando le curve di livello di $f_{2}$:
![[calcolo-hw-2-ottimiz-plot10.png]]

In effetti si tratta proprio di una serie di ellissi concentriche con centro $(1, 2)$.

Cominciamo anche in questo caso con i casi più eclatanti di $\alpha$, partendo da $0.07$:
![[calcolo-hw-2-ottimiz-plot11.png]]

Sappiamo che il minimo numero di iterazioni con il punto fisso per $f_{2}$ si ha per $\alpha = 0.089$, per cui mostriamolo:
![[calcolo-hw-2-ottimiz-plot12.png]]

L'alternanza dei valori sembra ridursi sempre più fino a convergere al minimo globale. Se portiamo il valore di $\alpha$ a $0.1$, otteniamo un risultato che già avevamo ottenuto in precedenza, con il calcolo della norma del gradiente e dell'errore relativo:
![[calcolo-hw-2-ottimiz-plot13.png]]
Questo è infatti esattamente in linea con le supposizioni fatte in precedenza:
- **il valore del gradiente rimane il medesimo** per ogni iterato $x_{k}$;
- **il valore dell'errore relativo all'inizio si abbassa, ma poi converge a un valore su cui rimane** per il resto delle iterazioni.

Abbiamo provato, ad ogni modo, che il numero di punti su cui rimane bloccato l'algoritmo è sempre 2.

Se proviamo ad aumentare anche solo di pochissimo il valore di $\alpha$, per esempio a $0.1003$, l'algoritmo comincerà a divergere:
![[calcolo-hw-2-ottimiz-plot14.png]]

L'unica cosa che resta da fare è mostrare l'andamento a spirale dell'algoritmo in caso di utilizzo del backtracking:
![[calcolo-hw-2-ottimiz-plot15.png]]

E invece **non si tratta affatto di una spirale**. Siamo _abbastanza certi dell'esistenza di un pattern, di una sequenza di norme del gradiente e di errori relativi che si ripetono nel corso delle iterazioni seppur con valori più bassi_, ma questa non è come avevamo ipotizzato un andamento che produce una spirale come percorso degli iterati.

#### Conclusioni
Nel corso di questo esperimento abbiamo _mostrato pregi e difetti delle due versioni dell'algoritmo di discesa del gradiente_, sia con passo fisso che con backtracking; abbiamo dimostrato la _relazione tra norma del gradiente ed errore relativo nello studio di problemi test_, scoprendo alcune _proprietà sulle funzioni prese in analisi_; infine, abbiamo _verificato le nostre ipotesi mostrando i cammini percorsi dall'algoritmo di discesa del gradiente sulle curve di livello delle funzioni_.

## Referenze
[^1]: il tutto è spiegato meglio [qui](https://en.wikipedia.org/wiki/Conjugate_gradient_method#Convergence_properties)
[^2]: fonti prese da [qui](https://webthesis.biblio.polito.it/20920/1/tesi.pdf)