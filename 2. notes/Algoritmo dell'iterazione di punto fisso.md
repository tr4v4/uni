---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 29-09-2024 12:38:57
links:
  - "[[Lecture 23092024132935]]"
  - "[[Lecture 24092024092227]]"
---
# Algoritmo dell'iterazione di punto fisso
---
## Introduzione
> L'**algoritmo dell'iterazione di punto fisso** è un [[Algoritmo|algoritmo]] [[Algoritmo iterativo|iterativo]] per il [[Algoritmi per il calcolo delle radici di una funzione|calcolo delle radici di un'equazione]] (non lineare).

## Teoria
L'idea alla base dell'algoritmo consiste nel cambiare la domanda del problema: al posto di trovare le radici di $f$, _ci si concentra nel trovare i [[Punto fisso|punti fissi]] di $g$_, una funzione ausiliaria relazionata ad $f$ tale che i suoi punti fissi sono proprio le radici di $f$.

In particolare si definisce $g$ come
$$g(x) = x - \omega(x)f(x)$$
dove $\omega$ è una funzione tale che $0 < \omega(x) < +\infty \ \ \forall x$.

Trattandosi di un algoritmo iterativo, abbiamo bisogno di costruire una successione $x_{0}, x_{1}, x_{2}, \cdots, x_{k}, x_{k+1}, \cdots$, con $x_{k} = g(x_{k-1})$, tale che $x_{k} \longrightarrow_{k \to +\infty} p$ dove $p$ è il punto fisso di $g$ e quindi la radice di $f$.
Il punto è: come troviamo una $g$ del genere? Per capirlo è necessario dimostrare alcune proposizioni e mettere vincoli a tale funzione. In particolare:
1. $f(x) = 0 \iff g(x) = x$
2. $x_{k} \longrightarrow_{k \to +\infty} p$, $g$ continua $\implies g(p) = p$
3. $g$ mappa contrattiva

### $f(x) = 0 \iff g(x) = x$
Dimostriamo la doppia implicazione:
- $\implies$: $f(\bar{x}) = 0 \implies \bar{x} - \omega(\bar{x})f(\bar{x}) = \bar{x} \implies g(\bar{x}) = \bar{x}$;
- $\impliedby$: $\bar{x} - \omega(\bar{x})f(\bar{x}) = \bar{x} \implies -\omega(\bar{x})f(\bar{x}) = 0 \implies f(\bar{x}) = 0$ (perché per ipotesi $0 < \omega(x) < +\infty$).

**Qed**.

### $x_{k} \longrightarrow_{k \to +\infty} p$, $g$ continua $\implies g(p) = p$
Per ipotesi $x_{k} \longrightarrow_{k \to +\infty} p$ equivale a
$$\lim_{k \to +\infty} x_{k} = p$$
e avendo $g$ [[Funzioni continue|continua]], allora vale
$$\lim_{k \to +\infty} g(x_{k}) = g(p)$$
Per costruzione della successione $\{x_{0}, x_{1}, \cdots\}$, si ha che $g(x_{k}) = x_{k+1}$, per cui
$$\lim_{k \to +\infty} x_{k+1} = g(p)$$
ma
$$\lim_{k \to +\infty} x_{k+1} = \lim_{k \to +\infty} x_{k} = p$$

Riunendo i risultati si ha
$$\lim_{k \to +\infty} g(x_{k}) = g(p) \ \ \land \lim_{k \to +\infty} g(x_{k}) = p$$
da cui
$$g(p) = p$$

**Qed**.

### $g$ mappa contrattiva
Finora abbiamo dimostrato che ogni punto fisso di $g$ è una radice di $f$, e che se la successione $x_{0}, x_{1}, \cdots$ con $x_{k} = g(x_{k-1})$ converge a $p$, allora $p$ è un punto fisso di $g$ (per cui una radice di $f$): **non ci rimane da dimostrare che la successione converga**!

<u>Nota bene</u>: bisognerebbe anche dimostrare che $g$ è continua, ma essendo $f$ continua per ipotesi (dal [[Teorema degli zeri|teorema degli zeri]]), e $g$ costruita con $f$, automaticamente anche $g$ è continua.

In realtà la convergenza della successione dipende solo e unicamente da $g$, e bisognerebbe per ogni $g$ diversa dimostrare la convergenza. Quello che si fa allora è richiedere che $g$ sia una [[Mappa|mappa]] [[Contrazione|contrattiva]].

C'è un [[Teorema della mappa contrattiva|teorema]], infatti, che ci assicura che **ogni mappa contrattiva $g$, in un dominio chiuso, ha esattamente un punto fisso nel dominio**. Inoltre, questo si può calcolare come limite
$$p = \lim_{k \to +\infty} x_{k}$$
della sequenza $x_{k} = g(x_{k-1})$ per ogni $x_{0}$ (punto di partenza) del dominio.

In poche parole, **se dimostriamo che $g$ è una contrazione, allora automaticamente la successione $\{x_{0}, x_{1}, \cdots\}$** (per qualunque $x_{0}$ iniziale, purché nel dominio della mappa) **converge al punto fisso di $g$, e quindi alla radice di $f$**.

## Verifica della mappa contrattiva
Abbiamo appreso che per applicare l'algoritmo ci basta verificare che $g$, nell'intervallo di riferimento $[a, b]$, sia una mappa contrattiva. Per verificarlo in modo facile, ci basta usare la definizione di contrazione:
1. _$g$ è una mappa?_ ($g([a, b]) = [a, b]$?)
2. _$g$ è una contrazione?_ ($\forall x, y \in [a, b]. \ \ \ |g(x) - g(y)| \leq C|x - y|$ con $C < 1$?)

### 1.
Verificare il primo punto è facile: basta vedere i valori delle immagini nell'intervallo $[a, b]$ del dominio e assicurarsi se nessuno "sfori" proprio $[a, b]$.

### 2.
Questo si verifica invece riaggiustando i membri della disequazione:
$$\frac{|g(x) - g(y)|}{|x - y|} \leq C < 1$$
Notiamo che essendo $g$ continua e verificando la sua [[Funzioni derivabili|derivabilità]] in $]a, b[$, possiamo applicare [[Teorema di Lagrange|Lagrange]] e ottenere che
$$\exists c \in ]x, y[ : \frac{|g(x) - g(y)|}{|x - y|} = |g'(c)|$$
E visto che consideriamo ogni $x$ e $y$ dell'intervallo $[a, b]$, possiamo riassumere la richiesta come
$$\forall c \in [a, b]. \ \ \ |g'(c)| \leq C < 1$$
Se quindi, per ogni punto del dominio, il [[Valore assoluto|valore assoluto]] della [[Derivata|derivata]] di $g$ è minore di 1, allora $g$ è una contrazione.

## Fattore $C$
### Calcolo
Abbiamo tutte le fondamenta basi per costruire $g$. In particolare dev'essere una mappa contrattiva costruita come $g(x) = x - \omega(x)f(x)$, con $0 < \omega(x) < +\infty$, tale che $g(x) = x \iff f(x) = 0$ (ossia relazionata in un qualche modo ad $f$).

Supponendo di aver trovato $g$, il valore $C$, anche detto **fattore di contrazione**, non è che una _maggiorazione di $g'(x)$_. Questo si ricava dalla proprietà della contrazione
$$\forall x \in [a, b]. \ \ \ |g'(x)| < C$$

### Indice
Questo valore, in realtà, si mostra essere _un indice di velocità di convergenza dell'algoritmo al punto fisso di $g$_, e quindi conseguentemente alla radice di $f$.

Questo risultato è una conseguenza della seguente proposizione:
$$|E_{k+1}| \leq C|E_{k}|$$
dove $E_{k} = |x_{k} - p|$, ossia l'_errore assoluto_ ($p$ è il punto fisso di $g$).

Infatti, iterando questo argomento si ottiene
$$|E_{k+1}| \leq C|E_{k}| \leq C^{2}|E_{k-1}| \leq \cdots \leq C^{k}|E_{0}|$$
o più brevemente, che
$$|E_{k}| \leq C^{k}|E_{0}| = C^{k}|x_{0} - p|$$
ossia che l'errore assoluto al passo $k$ è $C^{k}$ moltiplicato per l'errore iniziale, ovvero la distanza tra il punto iniziale $x_{0}$ e la soluzione $p$.

Questo dimostra che più $C$ è basso (essendo $< 1$), più l'errore assoluto al passo $k$ risulta piccolo. Per cui _$C \approx 0$ è sinonimo di una veloce approssimazione dell'algoritmo alla radice_.

#### Dimostrazione
Riscriviamo
$$|E_{k+1}| \leq C|E_{k}|$$
come
$$|x_{k+1} - p| \leq C |x_{k} - p|$$
Ora sfruttando la costruzione della successione, scriviamo $x_{k+1} = g(x_{k})$; sfruttando invece il fatto che per ipotesi $p$ è il punto fisso di $g$, scriviamo $p = g(p)$. In definitiva avremo
$$\frac{|g(x_{k}) - g(p)|}{|x_{k} - p|} \leq C$$

Sapendo che $g$ è una contrazione, questo risulta ovvio.

**Qed**.

## Referenze