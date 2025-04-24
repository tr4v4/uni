---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 09-03-2025 19:02:03
links:
  - "[[Lecture 05032025091441]]"
  - "[[Lecture 19032025092241]]"
  - "[[Lecture 20032025131726]]"
---
# Problema del flusso di costo minimo
---
## Introduzione
> Un **problema del flusso di costo minimo** (**MCF**) e' un'istanza del [[Problema di flusso|problema di flusso]] in cui la funzione obiettivo da minimizzare e' il _costo del flusso_.

Si assume che le capacita' inferiori $l_{ij}$ siano nulle.

## Modellizzazione
La funzione obiettivo e'
$$\min cx$$
e in vincoli sono
$$0 \leq x \leq u \ \ \ \ \ \ \ Ex = b$$
dove:
- $c \in \mathbb{R}^{|A|}$ e' il vettore dei costi;
- $u \in \mathbb{R}^{|A|}$ e' il vettore delle capacita' (superiori);
- $E \in \mathbb{R}^{|N| \times |A|}$ e' una sorta di [[Matrice di adiacenza|matrice di adiacenza]] tra nodi e archi (per ogni nodo si guardano gli archi, e negli archi entranti si mette $1$ mentre in quelli uscenti $-1$, e si ottiene il vincolo della conservazione del flusso);
- $b \in \mathbb{R}^{|N|}$ è il vettore degli sbilanciamenti.

## Assunzioni
### Singola sorgente e singolo pozzo
Conviene assumere che ci sia una sola sorgente (nodo di input) e un solo pozzo (nodo di output). E si dimostra che **ogni problema MFC puo' essere trasformato in un problema equivalente con una sola sorgente e un solo pozzo**: e' **sufficiente aggiungere due nodi fittizzi, una sorgente e un pozzo**, tali che
- _al nodo sorgente si attaccano tutte le sorgenti della rete di partenza, collegandoli con archi di costo nullo e capacità superiore pari all'inverso dello sbilanciamento delle sorgenti_;
- _al nodo pozzo si attaccano tutti i pozzi della rete di partenza, collegandoli con archi di costo nullo e capacità superiore pari all'inverso dello sbilanciamento dei pozzi_.

![[mcf-assunzioni-1.png]]
![[mcf-assunzioni-2.png]]
[^1]

### Capacita' dei nodi
A volte **e' utile imporre che anche i nodi abbiano delle capacita'**, ovvero che solo una quantità di flusso compresa nell'intervallo chiuso $[l_{i}, u_{i}]$ possa passare per il nodo $i \in N$. E' possibile modellizzare questa situazione sdoppiando ciascun ndo $i$ in due nodi $i', i''$ tali che
- _tutti gli archi entranti in $i$ vadano a finire in $i'$_;
- _tutti gli archi uscenti da $i$ partano da $i''$_;
- _vi sia un arco fittizio $(i', i'')$ con costo nullo, capacità inferiore $l_{i}$ e capacità superiore $u_{i}$_.

![[mcf-assunzioni-3.png]]

## Preliminari
### Pseudoflusso
Bisogna introdurre la nozione di **pseudoflusso**: è una definizione più lasca di flusso ammissibile, in cui rimane il vincolo sulle capacità, ma i vincoli di sbilanciamento non sono tenuti in conto. Matematicamente deve valere
$$0 \leq x_{ij} \leq u_{ij} \ \ \ \ \forall (i, j) \in A$$
ma definiamo sbilanciamento $e_{x}(i)$ lo sbilanciamento in ogni nodo $i$ della quantità entrante rispetto a quell'uscente nel flusso $x$:
$$e_{x}(i) = \sum\limits_{(j, i) \in BS(i)} x_{ji} - \sum\limits_{(i, j) \in FS(i)} x_{ij} - b_{i}$$

Quindi raccogliamo i nodi sbilanciati nei due insiemi:
- $O_{x} = \{i \in N | e_{x}(i) > 0\}$ --> vogliamo portare via del flusso da un nodo appartenente a questo insieme;
- $D_{x} = \{i \in N | e_{x}(i) < 0\}$ --> vogliamo portare del flusso verso un nodo appartenente a questo insieme.

Ovviamente, se $O_{x} = D_{x} = \varnothing$, allora $x$ è un flusso. Lo sbilanciamento complessivo di uno pseudoflusso $x$ è dato da
$$g(x) = \sum\limits_{i \in O_{x}}e_{x}(i) = - \sum\limits_{j \in D_{x}}e_{x}(j)$$

<u>Nota bene</u>: la seconda uguaglianza deve avvenire, fondamentalmente significa che lo sbilanciamento complessivo dei nodi che offrono flusso dev'essere lo stesso dei nodi che domandano flusso. E questo e' _per forza rispettato anche negli pseudoflussi fin tanto che viene superato il check sui parametri di bilanciamenti_ ($\sum\limits_{i \in D} b_{i} = -\sum\limits_{i \in O} b_{i} \ \ \ \iff \ \ \ \sum\limits_{i \in N} b_{i} = 0$).

### Grafo residuo
A questo punto possiamo generalizzare la nozione di [[Grafo residuo|grafo residuo]] al problema del flusso di costo minimo: è sufficiente che ogni arco comprenda anche un costo! Costruiamo sempre $G_{x}$ con archi concordi e discordi, ma comprendendo ora anche il loro costo. In particolare:
- in un arco concorde $(i, j)$ di $G_{x}$, il costo è semplicemente $c_{ij}$;
- in un arco discorde $(j, i)$ di $G_{x}$, il costo è invece $−c_{ij}$.

Sappiamo che dato un [[Cammino aumentante|cammino aumentante]] $P$, è possibile inviare $0 \leq \theta \leq \theta(P, x)$ unità di flusso lungo $P$, attraverso l'operatore $x(P, \theta)$. Quest'ultimo, nel contesto dei problemi del flusso di costo minimo, sarà indicato come $x \oplus P \theta$.

Quindi, la nozione stessa di cammino aumentante, adesso, avrà un costo:
$$c(P) = \sum\limits_{(i, j) \in P^{+}} c_{ij} - \sum\limits_{(i, j) \in P^{-}} c_{ij}$$

Si verifica che
$$c \cdot (x(P, \theta)) = c \cdot (x \oplus P \theta) = c \cdot x + \theta c(P)$$

### Pseudoflusso minimale
A differenza dei problemi di flusso massimo, non possiamo aumentare il flusso indiscriminatamente: questo costa a seconda di dove passa. Per questo si introduce la nozione di **pseudoflusso minimale**: è uno _pseudoflusso $x$ che ha costo minimo tra tutti gli pseudoflussi con lo stesso vettore di sbilanciamento $e_{x}$_.

Infatti, un vettore di sbilanciamento $e_{x}$ e' associato a piu' pseudoflussi: prendiamo in esempio una rete con solo una sorgente, una terminazione, e due archi da $s$ a $t$; il primo arco costa 5, il secondo 10; i fattori di sbilanciamento $b_{s}$ e $b_{t}$ sono rispettivamente $-2, 2$.
Ora, se considero un vettore di sbilanciamento $e_{x} = (1, -1)$, allora $x$ puo' essere $(1, 0)$ o $(0, 1)$, ma questi hanno ovviamente due costi diversi!

#### Lemma
> Uno pseudoflusso e' minimale $\iff$ non esistono cicli aumentanti di costo negativo.

Rispettivamente, la controparte sarebbe un flusso ammissibile è ottimo $\iff$ non esistono cicli aumentanti di costo negativo.

##### Dimostrazione
$\implies$: per assurdo, assumo che esista un ciclo aumentante di costo negativo per un cammino aumentante nel grafo residuo dello pseudoflusso $x$; ma se esiste, allora posso scegliere il cammino aumentante che lo contiene, e ottenere uno pseudoflusso $x'$ che per lo stesso vettore degli sbilanciamenti $e_{x}$ ha un costo piu' piccolo di $x$ --> assurdo per la minimalita' di $x$;

$\impliedby$: per assurdo, assumo che $x$ non sia minimale, ovvero che esista uno pseudoflusso $x'$ tale che questo abbia costo minimo per lo stesso $e_{x}$. Per il [[Teorema di struttura degli pseudoflussi|teorema di struttura degli pseudoflussi]], possiamo scrivere $x'$ come $$x' = x \oplus \theta_{1}P_{1} \oplus \cdots \oplus \theta_{n}P_{n}$$ dove $\theta_{i} > 0$ e $P_{i}$ e' un ciclo. Ora, dato che $cx' < cx$, allora per forza significa che un qualche ciclo $P_{i}$ deve avere costo negativo, per consentire a $x'$ di avere un costo minore. Formalmente, dato che $cx' = cx + \theta_{1}c(P_{1}) + \cdots + \theta_{n}c(P_{n})$, allora $cx' < cx$ implica che $$cx + \theta_{1}c(P_{1}) + \cdots + \theta_{n}c(P_{n}) < cx$$. Di conseguenza, deve esistere un $P_{i}$ che ha costo negativo, in contrapposizione con l'ipotesi iniziale.

**Qed**.

#### Preservazione della minimalita'
> Sia $x$ uno pseudoflusso minimale e sia $P$ un cammino aumentante rispetto ad $x$ avente costo minimo tra tutti i cammini che uniscono un nodo di $O_{x}$ ad un nodo di $D_{x}$. Allora, qualunque sia $\theta \leq \theta(x, P)$, abbiamo che $x(\theta, P) = x \oplus \theta P$ è ancora pseudoflusso minimale.

##### Dimostrazione
Siano $s$ e $t$ i vertici che $P$ collega. Supponiamo che $\theta \leq \theta(x, P)$ e che $y$ sia un qualunque pseudoflusso con vettore di sbilanciamento $e_{x(\theta, P)}$.
Per il teorema di struttura degli pseudoflussi esistono:
- $k$ cammini aumentanti $P_{1}, \cdots, P_{k}$ rispetto a $x$, tutti da $s$ a $t$, e
- $h$ cicli aumentanti $C_{1}, \cdots, C_{h}$ rispetto a $x$

tali che $y = x \oplus \theta_{1}P_{1} \oplus \cdots \oplus \theta_{k}P_{k} \cdots \mu_{1}C_{1} \oplus \cdots \oplus \mu_{h}C_{h}$, (dove tutti gli $\theta_{i}$, $\mu_{j}$ sono positivi). Deve essere, per ragioni che hanno a che fare con lo sbilanciamento, che $\sum\limits_{1 \leq i \leq k} \theta_{i} = \theta$.
Poiché $x$ è minimale, $c(C_{i}) \geq 0$. Inoltre, siccome $P$ ha costo minimo, $c(P_{i}) \geq c(P)$.

Di conseguenza
$$cy = cx + \theta_{1}c(P_{1}) + \cdots + \theta_{k}c(P_{k}) + \mu_{1}c(C_{1}) + \cdots + \mu_{h}c(C_{h}) \geq cx + \theta c(P) = cx(\theta, P)$$

**Qed**.

## Algoritmi
Gli algoritmi risolutivi sono:
- [[Algoritmo dei cammini minimi successivi]]
- [[Algoritmo di cancellazione dei cicli]]

## Referenze
- [[Teorema di struttura degli pseudoflussi]]

[^1]: ricorda un po' la dimostrazione dell'[[Equivalenza tra NFA ed espressioni regolari|equivalenza tra NFA ed espressioni regolari]]!
