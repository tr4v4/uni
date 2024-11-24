---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 23-11-2024 13:55:53
links:
  - "[[Lecture 05112024094126]]"
---
# CGLS
---
## Introduzione
> Il **CGLS** (_Conjugate Gradient Least Squares_) è l'applicazione del [[Metodo dei gradienti coniugati|metodo dei gradienti coniugati]] ai [[Problema dei minimi quadrati|problemi dei minimi quadrati]]. La sua fama è dovuta al fatto che è perfetto per risolvere problema in cui la [[Matrice|matrice]] $A$ è _grande_ e _sparsa_.

## Caratteristiche
La particolarità dell'algoritmo, che lo rende ottimale per $A$ grandi e sparse, è che **non utilizza le equazioni normali**. Si tratta infatti di un [[Algoritmo iterativo|algoritmo iterativo]], che _si basa sul [[Metodo di discesa del gradiente|metodo della discesa del gradiente]]_.

Il fatto che non utilizzi le equazioni normali è significativo. Queste infatti sono della forma
$$A^{T}Ax = A^{T}y$$
e per definizione si ha che
$$k(A^{T}A) = k(A)^{2}$$
dove $k$ è il [[Numero di condizione|numero di condizionamento]].

Un'altra importante caratteristica dell'algoritmo è che:
- $A$ e $A^{T}$ compaiono solo nella forma del tipo $Ax$ oppure $A^{T}z$ --> non sono mai da sole;
- il numero di operazioni del tipo $Ax$ e $A^{T}z$ è minimo.

Infatti solitamente a questo algoritmo sono associate delle _tecniche che consentono di calcolare $Ax$ e $A^{T}z$ senza dover memorizzare $A$ e $A^{T}$_[^2]!

## Algoritmo
### Inizializzazione
Dato un iterato iniziale $x_{0} \in \mathbb{R}^{n}$ a libera scelta (spesso $\underline{0}$), si calcola:
- il _residuo_ $r_{0} = A^{T}(y - Ax_{0})$;
- la _direzione_ $p_{0} = r_{0}$.

### Iterazioni
Per $k = 0, 1, \cdots, \text{maxit}$:
1. calcola vettore $q_{k} = Ap_{k}$;
2. calcola parametro $\alpha_{k} = \frac{{\|r_{k}\|_{2}}^{2}}{{\|q_{k}\|_{2}}^{2}}$;
3. aggiorna soluzione $x_{k+1} = x_{k} + \alpha_{k}p_{k}$;
4. aggiorna residuo $r_{k+1} = r_{k} - \alpha_{k}A^{T}q_{k}$;
5. calcola parametro $\beta_{k} = \frac{{\|r_{k+1}\|_{2}}^{2}}{{\|r_{k}\|_{2}}^{2}}$;
6. aggiorna direzione $p_{k+1} = r_{k} + \beta_{k}p_{k}$.

### Condizioni di arresto
Trattandosi di un algoritmo iterativo, è necessario definire delle condizioni di arresto. L'unico di cui si ha interesse riguarda il calcolo del residuo. In particolare si può arrestare l'algoritmo quando
$$\|r_{k}\|_{2} < \text{tol} \cdot \|r_{0}\|_{2}$$
dove $\text{tol}$ è una tolleranza prefissata.

## Implementazione
```python
import numpy as np

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

## Convergenza
Tra le proprietà più importanti e incredibili dell'algoritmo, si ha quello della convergenza:
> Se $A \in \mathbb{R}^{m \times n}$, allora l'algoritmo CGLS convergerà alla soluzione _esatta_ del problema ai minimi quadrati in _al massimo_ $n$ iterazioni.

Di conseguenza, è sempre possibile scegliere $\text{maxit} = n$, avendo la certezza teorica che l'algoritmo convergerà entro $n$ iterazioni alla soluzione esatta, ma solitamente $n$ è un valore troppo elevato per problemi reali.

## Regolarizzazione
Infine, è possibile adattare l'algoritmo CGLS ai problemi dei minimi quadrati [[Regolarizzazione|regolarizzati]] con [[Regolarizzazione alla Tikhonov|Tikhonov]]:
$$\min_{x} \frac{1}{2}{\|Ax - y\|_{2}}^{2} + \frac{\lambda}{2}{\|Lx\|_{2}}^{2}$$
dove:
- $L \in \mathbb{R}^{d \times n}$ è la _matrice di Tikhonov_, spesso $= I$;
- $\lambda > 0$ è il _parametro di regolarizzazione_.

La versione dell'algoritmo che utilizza la regolarizzazione di Tikhonov è la seguente:
```python
import numpy as np

def cgls_tikhonov(A, y, L, lam, tol=1e-6, maxit=100):
    """
    Algoritmo CGLS per risolvere il problema ai minimi quadrati regolarizzati con Tikhonov:
    min_x (1/2) * ||Ax - y||_2^2 + (lam/2) * ||Lx||_2^2
    """
    # Inizializzazione
    x = np.zeros(A.shape[1])
    r = r0 = y - A @ x
    p = A.T @ r - lam * (L.T @ (L @ x)) 
    z = p.copy() # z prende il posto di "p" come direzione

    for k in range(maxit):
        # Calcolo valori richiesti
        q = A @ p
        t = L @ p
        alpha = np.linalg.norm(z)**2 / np.linalg.norm(q)**2
        
        # Calcolo del coefficiente alpha
        alpha = (z.T @ z) / (q.T @ q + lam * (t.T @ t))
        
        # Aggiornamento di x
        x = x + alpha * p
        
        # Aggiornamento del residuo
        r = r - alpha * q
        
        # Verifica del criterio di arresto
        if np.linalg.norm(r) < tol * np.linalg.norm(r0):
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

## Referenze
[^2]: proprietà fondamentali nell'applicazione all'[[Imaging|imaging]]