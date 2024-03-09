---
tags:
  - category/note
  - status/finished
  - topic/algebra-e-geometria
date: 24-02-2024 21:10:47
links:
  - "[[Lecture 21022024091849]]"
  - "[[Lecture 22022024111644]]"
  - "[[Lecture 07032024111604]]"
---
# Algoritmo di Gauss
---
## Introduzione
> Per **algoritmo di Gauss** si intende un _[[Algoritmo|algoritmo]] che attraverso una serie di [[Operazioni elementari|operazioni elementari]] è in grado di trasformare una [[Matrice|matrice]] associata a un [[Sistema lineare|sistema lineare]] in una [[Matrice a scala|matrice a scala]], cui sistema è [[Sistemi equivalenti|equivalente]]_.
> E' anche conosciuto con il nome di _metodo di riduzione_, o _riduzione di Gauss_.

## Algoritmo
L'algoritmo di riduzione procede come segue:
1. se il primo elemento di ogni riga di $A$ è nullo, si considera la matrice ottenuta cancellando la prima colonna della matrice in esame e si ricomincia dal punto 1. Altrimenti se $a_{11} = 0$ si scambio la prima riga di $A$ con una riga il cui primo elemento è non nullo. Indichiamo tale termine, detto _pivot_, con $a$;
2. si controllano una dopo l'altra tutte le righe tranne la prima. Se il primo elemento di una riga è nullo si lascia quella riga inalterata; altrimenti se il primo elementi è $b \neq 0$ si sostituisce tale $i$-esima riga ($i > 1$) con la somma della riga $i$-esima e la prima riga moltiplicata per $\alpha = - \frac{b}{a}$;
3. a questo punto tutti gli elementi della prima colonna, tranne il primo, sono nulli. Si considera dunque la matrice che si ottiene cancellando la prima riga e la prima colonna della matrice ottenuta e si ricomincia dal punto 1.

<u>Nota bene</u>: se la matrice è _parametrica_ allora una volta ridotta a scala _potrebbe essere necessario procedere per casi sui coefficienti parametrici_. Questi infatti potrebbero non essere pivot, e quindi eventualmente modificare il [[Rango righe|rango righe]] di $A$: questo determina il risultato finale del sistema.

## Utilizzo diretto
L'algoritmo di Gauss si può utilizzare non solo per risolvere sistemi lineari. Di fatto, grazie a due teoremi fondamentali, **è possibile applicare l'algoritmo per risolvere problemi di [[Algebra lineare|algebra lineare]] senza passare per i sistemi**.

### Teoremi
> I due teoremi sono:
> 1. _le operazioni elementari sulle righe di una matrice non cambiano il [[Sottospazio generato|sottospazio generato]] dalle righe della matrice_;
> 2. _le righe non nulle di una matrice a scala sono [[Indipendenza lineare|linearmente indipendenti]]_;

Sono entrambi semplicissimi e di facile intuizione/dimostrazione, ma di grande significato:
- il primo teorema **ci consente di studiare dei vettori come se fossero righe di una matrice**, e quindi di **applicare le riduzioni di Gauss senza modificare il sottospazio generato dalle suddette**;
- il secondo teorema ci consente, a seguito delle dovute trasformazioni, di **considerare le righe di una matrice come vettori linearmente indipendenti**;

### Applicazioni
L'idea di base è di applicare queste proprietà per risolvere problemi generali di algebra lineare. Si possono riassumere le conseguenze dei due teoremi nel seguente enunciato:

> Se $V = \langle v_{1}, \cdots, v_{m} \rangle$ costruiamo la matrice di vettori in riga, e sviluppando l'algoritmo di Gauss otteniamo $w_{1}, \cdots, w_{k}$ righe. Per il primo teorema ho
> $$V = \langle v_{1}, \cdots, v_{m} \rangle = \langle w_{1}, \cdots, w_{k} \rangle$$
> mentre per il secondo ho che $w_{1}, \cdots, w_{k}$ sono linearmente indipendenti e perciò che $\beta = \{w_{1}, \cdots, w_{k}\}$ è [[Base|base]] di $V$ e la sua [[Dimensione|dimensione]] è $k$.

#### Per l'indipendenza lineare
Lo stesso principio si può applicare per determinare l'indipendenza o meno di vettori $v_{1}, \cdots, v_{m}$. Infatti riducendoli a scala (dopo averli disposti per righe) e ottenendo $w_{1}, \cdots, w_{k}$ vettori, si distinguono 2 casi:
- $k < m \implies v_{1}, \cdots, v_{m}$ sono dipendenti, perché fondamentalmente le operazioni elementari di Gauss hanno dimostrato come un (o più) vettore fosse combinazione lineare degli altri, e per il [[Teorema del completamento|teorema del completamento]] in uno spazio di $k$ dimensioni si possono avere al massimo $k$ vettori indipendenti;
- $k = m \implies v_{1}, \cdots, v_{m}$ sono indipendenti, perché sapendo che la dimensione è proprio $m$, e che generano $V$, per il [[Teorema GEL|teorema GEL]] allora sono anche indipendenti;

#### Per il completamento a base
O ancora possiamo sfruttare i teoremi per completare una base di $V$ a una base di $\mathbb{R}^{n}$. Di fatto, se abbiamo un insieme generatore $\{v_{1}, \cdots, v_{m}\}$, se vogliamo completarlo a una base di $\mathbb{R}^{n}$, per il teorema del completamento significa che ci basta aggiungere $n-m$ vettori linearmente indipendenti a $\{v_{1}, \cdots, v_{m}\}$ (ovviamento se $n-m = 0$ allora è già base di $\mathbb{R}^{n}$). Allora l'idea è quella di _mettere tali vettori come righe di una matrice, ridurla a scala, e a quel punto aggiungere delle righe non nulle negli spazi in cui manca il pivot_! Questo, per il secondo teorema, ci garantisce che tali righe aggiunte siano linearmente indipendenti: per cui li riportiamo a stato di vettore ed ecco che abbiamo ottenuto una base di $\mathbb{R}^{n}$.

C'è ad ogni modo un caso importante da tenere in considerazione: se ci viene chiesto di trovare un _sovrainsieme_ di $V$ che completi una base di $\mathbb{R}^{n}$, allora non possiamo come risposta dare le righe indipendenti della matrice "scalata" unite a quelle aggiunte; ma fortunatamente, per il primo teorema, sappiamo che le righe che hanno subito operazioni elementari costituiscono lo stesso spazio vettoriale delle originali, perciò _possiamo mantenere le originali e aggiungere le righe non nulle negli spazi in cui manca il pivot_.

L'idea in poche parole è: _se quando ci viene chiesto di completare un generatore a uno spazio, se non riusciamo a trovare i pivot, riduciamo i vettori a scala così da vedere i pivot mancanti, e questi possono essere aggiunti ai vettori non "scalati"_.

##### Esempio
Completiamo $A = \{(2, 2, 5, 1), (1, 1, 4, -1)\}$ a una base di $\mathbb{R}^{4}$. Se sappiamo che la dimensione di $\mathbb{R}^{4}$ è, appunto, 4, e che i vettori di $A$ sono linearmente indipendenti (non sono uno multiplo dell'altro) allora per il teorema del completamento dobbiamo aggiungere $4-2=2$ vettori per rendere $A$ una base di $\mathbb{R}^{4}$. Applichiamo l'algoritmo di Gauss in modo diretto, per cui mettiamo i vettori di $A$ in riga:
$$\begin{pmatrix} 2 & 2 & 5 & 1 \\ 1 & 1 & 4 & -1 \end{pmatrix}$$
Dopo una serie di operazioni elementari ci ritroviamo con la seguente matrice a scala:
$$\begin{pmatrix} 1 & 1 & 4 & -1 \\ 0 & 0 & -3 & 3 \end{pmatrix}$$

Quindi, identificati i pivot mancanti (proprio 2) li andiamo ad aggiungere:
$$\begin{pmatrix} 1 & 1 & 4 & -1 \\ 0 & 1 & 0 & 0 \\ 0 & 0 & -3 & 3 \\ 0 & 0 & 0 & 1 \end{pmatrix}$$

Ora potremmo semplicemente riscrivere queste righe come vettori e avremmo una base di $\mathbb{R}^{4}$, MA ci è richiesto di trovare un sovrainsieme di $A$ che completi a base di $\mathbb{R}^{4}$, e il vettore $(2, 2, 5, 1)$ è "andato perso". In virtù del primo teorema, però, _possiamo considerare la prima e la terza riga equivalenti ai vettori originali_, per cui prendiamo i due vettori di $A$ e ci aggiungiamo i due aggiunti alla matrice a scala:
$$\mathbb{R}^{4} = \langle (2, 2, 5, 1), (1, 1, 4, -1), (0, 1, 0, 0), (0, 0, 0, 1) \rangle$$

e l'esercizio si conclude.

## Referenze