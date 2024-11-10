---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 03-11-2024 18:22:33
links:
  - "[[Lecture 21102024132104]]"
---
# Interpolazione
---
## Introduzione
> L'**interpolazione** è un sottocaso del problema dell'[[Approssimazione di dati|approssimazione di dati]] in cui _si cerca di approssimare esattamente la [[Funzione matematica|funzione]] che passa per i punti dati in input_. In particolare si vuole trovare un [[Polinomio|polinomio]] interpolante $p(x)$ tale che
> $$p(x_{k}) = y_{k} \ \ \ \forall k \in \{1, \cdots, n\}$$
> dove le [[Coppia ordinata|coppie]] $(x_{k}, y_{k})$ sono i dati in ingresso, e se $f(x)$ è la funzione interpolante, allora $f(x_{k}) = y_{k} \ \ \ \forall k \in \{1, \cdots, n\}$.

Quindi io ho solo $k$ valori della funzione $f(x)$, e voglio trovare il polinomio $p(x)$ che passa proprio per quei $k$ punti.

## Preliminari
Anche in questo caso, si cercano quindi dei coefficienti $c_{i}$ che rendano $p$ interpolante rispetto a $y$. Per ottenere questo, _il grado del polinomio $p$ dovrà esattamente essere $n$, il numero di punti da cui deve passare_. Questo è giustificato dal seguente teorema.

### Teorema di esistenza e unicità
> Per ogni insieme di coppie $(x_{i}, y_{i})$ con $i = 0, \cdots, n$, con i nodi $x_{i}$ distinti tra di loro, esiste un unico polinomio di grado $\leq n$, indicato con $p_{n}(x)$ e chiamato **polinomio interpolatore dei valori $y_{i}$ nei nodi $x_{i}$** tale che:
> $$p_{n}(x_{i}) = y_{i} \ \ \ i = 0, \cdots, n$$

Se $y_{i}$ rappresenta i valori assunti da una funzione [[Funzioni continue|continua]] $f$, allora $p_{n}(x)$ è detto **polinomio interpolatore di $f$**, indicato con $$p_{n}(f)$$.

### Idea
Per calcolare il polinomio interpolatore, dal teorema precedente possiamo pensare di passare ai [[Problema dei minimi quadrati|minimi quadrati]]. Abbiamo $n+1$ dati, e $n+1$ coefficienti $c_{0}, \cdots, c_{n}$, per cui possiamo scrivere la soluzione del problema dell'interpolazione come:
$$\min_{c} {\|Xc - y\|_{2}}^{2}$$
dove:
- $c = (c_{0}, \cdots, c_{n})$, il [[Vettore|vettore]] dei coefficienti;
- $X \in M_{n+1}(\mathbb{R})$ è la [[Matrice di Vandermonde|matrice di Vandermonde]], quadrata.

Il problema con questo tipo di soluzione, è che per $n \gg 1$, $X$ può essere _mal condizionata_. Inoltre la risoluzione del problema, sia con le equazioni normali che con la [[Fattorizzazione ai valori singolari|SVD]], richiede almeno $\frac{n^{3}}{3}$ operazioni.

## Approccio
Si utilizza quindi un approccio differente per calcolare il polinomio interpolatore $p_{n}(x)$.

### Delta di Kronecker
Bisogna reintrodurre i [[Delta di Kronecker|delta di Kronecker]] nella seguente maniera: definisco particolari polinomi di grado $n$ come
$$\phi_{k}(x_{j}) = \delta_{k, j}$$
ovvero
$$\phi_{k}(x_{k}) = 1 \ \ \ \land \ \ \ \phi_{k}(x_{j}) = 0, \ \ \ j \neq k$$

Quindi avremo $n+1$ polinomi del tipo $\phi_{k}$, e per ognuni di questi si definiscono $n+1$ punti $\phi_{k}(x_{j})$.

### Funzioni $\phi_{k}$
Vogliamo codificare queste funzioni in modo da renderle polinomiali, mantenendo vera la condizione di Kronecker (la sua proprietà): $\phi_{k}$ dovranno essere polinomi che in $x_{k}$ restituiscono 1, mentre in $x_{j}$ con $j \neq k$ restituiscono 0.

Si dimostra che ogni polinomio $\phi_{k}$ soddisfa questo criterio se costruito nel seguente modo:
$$\phi_{k} = \prod_{j=0, j \neq k}^{n} \frac{x-x_{j}}{x_{k}-x_{j}}$$

Questi polinomi sono chiamati _[[Polinomio di Lagrange|polinomi di Lagrange]]_.

### Polinomi di Lagrange
Da qui è semplice. Una volta che abbiamo i $n+1$ polinomi di Lagrange $\phi_{k}$ costruiti come sopra, allora si dimostra che il polinomio interpolante $p_{n}(x)$ è
$$p_{n}(x) = y_{0}\phi_{0}(x) + y_{1}\phi_{1}(x) + \cdots + y_{n}\phi_{n}(x) = \sum\limits_{k=0}^{n}y_{k}\phi_{k}(x)$$

E' ovvio che $p_{n}(x)$ interpoli nei punti $(x_{i}, y_{i})$ per $i \in \{0, \cdots, n\}$. Infatti preso $p_{n}(x_{i})$, ciò che rimane nell'espressione è $y_{i}\phi_{i}(x_{i}) = y_{i}$.

## Errore
Si vuole adesso quantificare l'errore di questo metodo, che esprima la differenza tra $p$ ed $f$ nei punti diversi da $x_{i}$. Infatti per definizione $p$ interpola, ma al di fuori di quei punti è davvero simile ad $f$?

Per scoprirlo ci avvaliamo del seguente teorema:
> Sia $f \in C^{n+1}(I)$[^1] dove $I$ è l'intervallo contenente gli $n+1$ punti $x_{i}$, allora $$\forall x \in I. \exists \eta \in I : E(x) = f(x) - p_{n}(x) = \frac{f^{n+1}(\eta)}{(n+1)!} \prod_{i=0}^{n} (x - x_{i})$$

Il fatto che ricordi lo [[Sviluppo in serie di Taylor|sviluppo in serie di Taylor]] non è un caso. Notiamo anche che, ovviamente, $E(x_{i}) = 0 \ \ \ i = 0, \cdots, n$.

### Convergenza/divergenza
Da questo teorema vorremmo dimostrare che se aumentiamo gli $n$ punti di $f$, allora l'errore $E(x)$ diminuisca. Formalmente si vorrebbe dimostrare che
$$\max_{x \in I} |E(x)| \longrightarrow_{n \to +\infty} 0$$
ovvero che per infiniti punti $n$, l'errore $E$ tenda sempre a 0.

Ma il teorema di prima non ci permette di dimostrarlo: infatti non è così! Anzi, esistono diversi controesempi che dimostrano come all'aumentare del numero di nodi $n$, l'errore diverga:
$$\max_{x \in I} |E(x)| \longrightarrow_{n \to +\infty} +\infty$$

Questo prende il nome di **[[Fenomeno di Runge|fenomeno di Runge]]**. Si risolve distribuendo attraverso una distribuzione dei nodi tale da far convergere l'errore sempre a 0 per $n \to +\infty$: [[Nodi di Chebyshev-Gauss-Lobatto|nodi di Chebyshev-Gauss-Lobatto]].

## Condizionamento
Se assumiamo di avere un [[Errore di arrotondamento|errore di rappresentazione]] sugli input $y_{i}$, tale che otteniamo il polinomio $p_{n}(x)$ su $\tilde{y_{i}} = y_{i} + \Delta y$, allora qual è il rapporto tra $\tilde{p_{n}}(x)$ e $p_{n}(x)$, non considerando gli [[Errore algoritmico|errori algoritmici]]? In poche parole, qual è il condizionamento del metodo?

Se $\Delta z$ è l'[[Errore inerente|errore inerente]] $\tilde{p_{n}}(x) - p_{n}(x)$, allora
$$|\Delta z| \leq C(n) \cdot |\Delta y|$$
e cos'è $C(n)$?

Assumendo
$$\Delta y = \max |y_{i} - \tilde{y_{i}}| = \max |f(x_{i}) - \tilde{f}(x_{i})|$$[^2]
allora
$$\Delta z = \max_{x \in I} |p_{n}(x) - \tilde{p_{n}}(x)| = \max_{x \in I} |\sum\limits_{i=0}^{n} f(x_{i}) \phi_{i}(x) - \sum\limits_{i=0}^{n} \tilde{f}(x_{i}) \phi_{i}(x)| = \max_{x \in I} |\sum\limits_{i=0}^{n} (f(x_{i}) - \tilde{f}(x_{i}))\phi_{i}(x)|$$
che date le proprietà del polinomio di Lagrande $\phi_{i}$ può essere scritto come
$$\Delta z = \Lambda_{n}(x) \max |f(x_{i}) - \tilde{f}(x_{i})| = \Lambda_{n}(x) \Delta y$$
dove
$$\Lambda_{n}(x) = \max_{x \in I} |\sum\limits_{i=0}^{n} \phi_{i}(x)|$$
ed è proprio il [[Numero di condizione|numero di condizione]] del problema dell'interpolazione, chiamata **[[Costante di Lebesgue|costante di Lebesgue]]**. Per cui _se $\Lambda_{n}(x) \gg 1$ allora il problema è mal posto_.

<u>Nota bene</u>: nel caso di interpolazione polinomiale su _nodi equispaziati_, la costante di Lebesgue assume il valore
$$\Lambda_{n}(x) \simeq \frac{2^{n+1}}{en(\log{n} + \gamma)}$$
dove $\gamma$ è la [[Costante di Eulero-Mascheroni|costante di Eulero-Mascheroni]].

## Referenze
[^1]: [[Classe C|classe C]]
[^2]: la [[Norma vettoriale|norma]] $\infty$ di $y_{i} - \tilde{y_{i}}$