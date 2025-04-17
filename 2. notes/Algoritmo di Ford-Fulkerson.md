---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 24-03-2025 13:01:21
links:
  - "[[Lecture 12032025091447]]"
---
# Algoritmo di Ford-Fulkerson
---
## Introduzione
> L'**algoritmo di Ford-Fulkerson** (o **FF**) è un [[Algoritmo|algoritmo]] _naive_ per risolvere il [[Problema del flusso massimo|problema del flusso massimo]], che si basa sulle nozioni di [[Grafo residuo|grafo residuo]] e [[Cammino aumentante|cammini aumentanti]].

## Algoritmo
Nella sua essenza l'algoritmo è il seguente:
1. $x = \underline{0}$;
2. costruisci $G_{x}$ e determina se $G_{x}$ ha un cammino aumentante $P$; in caso $P$ non esista, termina e restituisci $x$;
3. $x = x(P, \theta(P, x))$;
4. torna al punto 2;

### Correttezza
Dimostriamo la correttezza dell'algoritmo mostrando il risultato di alcuni lemmi.

#### Ammissibilità
> Se $x$ è un flusso ammissibile, anche $x(P, \theta(P, x))$ lo è.

#### Flusso massimo
> Se $x$ è un flusso ammissibile massimo, allora $G_{x}$ non ha cammini aumentanti.

Questo è ovvio: se $G_{x}$ avesse cammini aumentanti vorrebbe dire che è possibile aumentare il valore del flusso, per cui $x$ non sarebbe massimo.

**Qed**.

#### Capacità del taglio
> Se $G_{x}$ non ha cammini aumentanti, allora esiste un taglio di capacità pari a $v$.

E' sufficiente considerare il [[Taglio s-t|taglio s-t]] $(N_{s}, N_{t})$ dove $N_{s}$ contiene tutti e soli i nodi raggiungibili da $s$ in $G_{x}$, e $N_{t} = N \setminus N_{s}$. Questo taglio, infatti, non può avere una capacità maggiore del flusso $v$, perché se così fosse allora da uno dei nodi in $N_{s}$ si potrebbe aggiungere un arco concorde, e i nodi raggiungibili da $s$ in $G_{x}$ includerebbero tale nodo. E dualmente non può avere una capacità minore del flusso $v$, perché il flusso è ammissibile per il primo lemma.

Più formalmente, si ha che
$$v = x(N_{s}, N_{t}) = \sum\limits_{(i, j) \in A^{+}(N_{s}, N_{t})} x_{ij} - \sum\limits_{(i, j) \in A^{-}(N_{s}, N_{t})} x_{ij} = \sum\limits_{(i, j) \in A^{+}(N_{s}, N_{t})} u_{ij} - 0 = u(N_{s}, N_{t})$$

La 3° uguaglianza segue proprio dalle proprietà del taglio trovato con l'algoritmo: la prima sommatoria vale perché se non valesse allora con Ford-Fulkerson si potrebbe espandere $N_{s}$, ma $G_{x}$ non ha cammini aumentanti; la seconda vale perché se non valesse allora vorrebbe dire che ci sono archi discordi in $G_{x}$ che vanno da $N_{s}$ a $N_{t}$, e che quindi $N_{s}$ sarebbe espandibile.

**Qed**.

#### Correttezza parziale
> Se l'algoritmo di Ford-Fulkerson termina, allora il flusso $x$ è massimo.

Se l'algoritmo termina allora vuol dire che in $G_{x}$ non ci sono cammini aumentanti, per cui per il lemma precedente, questo taglio ha capacità pari a quella del flusso $x$. Sappiamo che se la capacità del taglio è uguale a quella di un flusso ammissibile, allora questo flusso è massimo[^1].

**Qed**.

### Terminazione
Per parlare di terminazione possiamo analizzare la [[Complessità computazionale|complessità computazionale]], e scopriamo che non si può dire molto sull'algoritmo...
Tuttavia, possiamo analizzare un caso specifico di grafo su cui eseguire l'algoritmo.

> Se le capacità di $G$ sono intere, allora esiste almeno un flusso intero massimo.

#### Dimostrazione
Se prendiamo un grafo pessimo di $n$ nodi, allora il flusso massimo è upperboundato da $nU$, dove $U = \max \{u_{ij} | (i, j) \in A\}$. Questo perché, se prendiamo il caso banale di un taglio s-t che separa $s$ da tutti gli altri $n-1$ nodi, allora il flusso non potrà essere superiore a $(n-1)U \approx nU$. Detto ciò, nel caso pessimo, il grafo in questione ha un arco _bottleneck_ di capacità 1, sempre scelto per ogni cammino aumentante. Come risultato si ha che ad ogni iterazione il valore del flusso calcolato viene incrementato di 1. Si deve considerare, infine, il costo di ogni visita per trovare i cammini aumentanti, upperboundata dal numero di archi $m$ (la ricerca dei cammini aumentanti è esaustiva).

Per cui, per ogni visita $O(m)$ avremo un incremento di almeno 1 quantità sul valore del flusso $O(nU)$, per cui la complessità dell'algoritmo nel caso delle capacità intere è:
$$O(mnU)$$
che non è polinomiale! Ma _pseudopolinomiale_: $U$ è un parametro del problema.

![[grafo-bottleneck.png]]

## Osservazioni
Il problema di questo algoritmo, causa diretta della sua pessima complessità, sta nella **libertà di scelta del cammino aumentante**: _se consideriamo il caso pessimo, l'algoritmo trova come cammino aumentante ad ogni iterazione sempre quello peggiore, in cui è presente un bottleneck che frena l'incremento del flusso_.

## Referenze

[^1]: [[Taglio s-t#Conseguenze]], e quindi il [[Teorema max-flow min-cut|teorema max-flow min-cut]]
