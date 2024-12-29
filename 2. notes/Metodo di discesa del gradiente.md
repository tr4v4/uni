---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 10-11-2024 16:39:21
links:
  - "[[Lecture 22102024092339]]"
---
# Metodo di discesa del gradiente
---
## Introduzione
> Il **metodo di discesa del gradiente** (o della **ripida discesa**) è un metodo per la _risoluzione di [[Ottimizzazione di dati|problemi di ottimizzazione]] svincolati e smooth_
> $$\min_{x \in \mathbb{R}^{n}} f(x)$$
> basato sulle _condizioni del primo ordine_.

Appartiene ai cosiddetti [[Metodo di ricerca in linea|metodi di ricerca in linea]], ossia degli [[Algoritmo iterativo|algoritmi iterativi]] che a partire da un $x_{0}$ seguono un percorso $x_{1}, \cdots, x_{k}, x_{k+1}, \cdots$ per arrivare alla soluzione $x^{*}$.

## Idea
La discesa del gradiente, scelto un termine $x_{0} \in \mathbb{R}^{n}$, considera l'iterazione ([[Successione numerica|successione]])
$$x_{k+1} = x_{k} + \alpha_{k}p_{k}$$
dove:
- $\alpha_{k} > 0$ è detto _step-size_ o _learning-rate_;
- $p_{k} \in \mathbb{R}^{n}$ è un [[Vettore|vettore]] detto _direzione di discesa_ (descritto dopo).

Quindi, **l'algoritmo si muove verso la direzione del minimo** per ogni iterato $k \in \mathbb{N}$. O formalmente
$$x^{*} = \lim_{k \to \infty} x_{k}$$
con $x^{*}$ punto di minimo.

### Direzione di discesa
> Si dice che $p_{k}$ è una **direzione di discesa** se
> $$\exists \alpha_{k} : f(x_{k} + \alpha_{k}p_{k}) \leq f(x_{k})$$

Un teorema ci dice che:
> $p_{k}$ è di discesa per $f(x)$ in $x_{k}$ se $p_{k}^{T} \nabla f(x_{k}) \leq 0$.

Ma allora è facile scegliere il $p_{k}$ giusto! Ci basta risolvere la disequazione. Se scegliamo
$$p_{k} = -\nabla f(x_{k})$$
otteniamo
$$p_{k}^{T} \nabla f(x_{k}) = - {\|\nabla f(x_{k})\|_{2}}^{2} \leq 0$$

Allora sceglieremo sempre **$p_{k}$ come l'anti-gradiente**.

## Algoritmo
Dai presupposti precedenti è facile istanziare l'algoritmo:
$$\begin{cases} x_{0} \in \mathbb{R}^{n} \\ x_{k+1} = x_{k} - \alpha_{k} \nabla f(x_{k}) \end{cases}$$
dove l'unica cosa rimasta da scegliere è $\alpha_{k}$.

### Criteri di arresto
Trattandosi di un algoritmo iterativo è necessario definire dei criteri di arresto per fermare l'algoritmo una volta raggiunto un risultato accettabile:
1. $\|\nabla f(x_{k})\|_{2} \leq \text{tol}_{f}$, ossia quando il gradiente raggiunge una [[Norma vettoriale|norma]] molto bassa (di solito $\text{tol}_{f} = 10^{-6}$);
2. $\|x_{k+1} - x_{k}\|_{2} \leq \text{tol}_{x}$, ossia quando c'è troppa poco spostamento tra un'iterazione e un'altra --> _ci vogliamo arrendere quanto la funzione è troppo piatta_.

### Learning-rate $\alpha_{k}$
Il comportamento dell'algoritmo su diversi valori di $\alpha_{k}$ può essere riassunto nella seguente immagine:
![[learning-rate.png]]

Come facciamo a scegliere allora il valore perfetto per $\alpha_{k}$? Teoricamente ci vengono in aiuto le [[Condizione di Wolfe|condizioni di Wolfe]], e in particolare la prima, nota come [[Condizione di Armijo|condizione di Armijo]].

#### Backtracking
Un algoritmo ausiliario usato dalla discesa del gradiente è quello di backtracking, basato sulla condizione di Armijo:
1. per ogni iterazione $k \in \mathbb{N}$:
	1. si inizializza $\alpha_{k}$ con una stima di partenza (di solito $=1$);
	2. si controlla se $\alpha_{k}$ soddisfa la condizione di Armijo;
	3. se sì l'algoritmo termina; altrimenti si riduce il valore di $\alpha_{k}$ e si ripete dallo step precedente;

Si dimostra che implementando così l'algoritmo, questo _terminerà sempre_ e il valore raggiunto da $\alpha_{k}$ soddisferà le condizioni di Wolfe, _facendo convergere sempre l'algoritmo_.

<u>Attenzione</u>: la _ricerca di questo $\alpha_{k}$ ha comunque un costo, che viene aggiunto a quello della discesa del gradiente ad ogni passo $k$_.

### Codice
```Python
def backtracking(f, df, x, alpha=1, rho=0.5, c=1e-4):
    """
    Algoritmo di backtracking per Discesa Gradiente.

    Parameters:
    f       : Funzione obiettivo.
    df      : Gradiente della funzione obiettivo.
    x       : Iterato x_k.
    alpha   : Stima iniziale di alpha(default 1).
    rho     : Fattore di riduzione (default 0.5).
    c       : Costante delle condizioni di Armijo (default 1e-4).

    Returns:
    alpha   : Learning rate calcolato con backtracking.
    """
    while f(x - alpha * df(x)) > f(x) + c * alpha * np.linalg.norm(df(x))**2:
        alpha *= rho
    return alpha


def GD_backtracking(f, df, x0, x_true, maxit=100, tolf=1e-6, tolx=1e-6):
    r"""
    Implementa il metodo di discesa del gradiente con passo scelto con backtracking applicato ad una funzione f(x) della quale si conosce la derivata df(x). 

    Parameters:
    f (function): la funzione obiettivo che si vuole minimizzare
    df (function): la derivata (o gradiente) della funzione obiettivo
    x0 (ndarray): valore iniziale dell'algoritmo
    x_true (ndarray): la soluzione esatta dell'algoritmo (nota SOLO in fase di test)
    maxit (int): numero di iterazioni
    tolf (float): tolleranza di || grad(f) ||_2
    tolx (float): tolleranza di || x_{k+1} - x_k ||_2
    """
    # Inizializzazione
    k = 0
    rel_err = np.zeros((maxit+1, ))
    obj_val = np.zeros((maxit+1, ))
    grad_norm = np.zeros((maxit+1, ))

    # Ciclo iterativo (uso un ciclo while)
    condizione = True
    while condizione:
        # Scelta di alpha_k con backtracking
        alpha = backtracking(f, df, x0, alpha=1)

        # Aggiornamento x_{k+1} = x_k - alpha_k df(x_k)
        x = x0 - alpha * df(x0)

        # Calcolo dell'errore e salvataggio
        rel_err[k] = np.linalg.norm(x - x_true) / np.linalg.norm(x_true)
        obj_val[k] = f(x)
        grad_norm[k] = np.linalg.norm(df(x))

        # Check condizioni di arresto
        condizione = (k < maxit) and (np.linalg.norm(df(x)) > tolf) and (np.linalg.norm(x - x0) > tolx)

        # Se l'algoritmo termina per || x_{k+1} - x_k || < tolx, stampare il warning
        if (np.linalg.norm(x - x0) < tolx):
            print(f"Algoritmo terminato per condizione su tolx.")
            
        # Preparazione per step successivo
        k = k + 1
        x0 = x

    # Se l'algoritmo si ferma prima di maxit, tagliare i valori inutilizzati delle metriche
    if k < maxit:
        rel_err = rel_err[:k]
        obj_val = obj_val[:k]
        grad_norm = grad_norm[:k]

    return x, rel_err, obj_val, grad_norm
```

## Referenze