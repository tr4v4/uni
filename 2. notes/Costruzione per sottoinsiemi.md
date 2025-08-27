---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 14-10-2024 20:39:21
links:
  - "[[Lecture 08102024111650]]"
---
# Costruzione per sottoinsiemi
---
## Introduzione
> La tecnica di **costruzione per sottoinsiemi** (o **subset construction**) consiste in un [[Algoritmo|algoritmo]] in grado di costruire un [[DFA]] a partire da un [[NFA]], tale che siano equivalenti (riconoscano lo stesso linguaggio).

## Idea
L'idea sta nel _seguire contemporaneamente tutti i possibili cammini alternativi dell'NFA_, e quindi di _definire gli stati del DFA equivalente come insiemi di stati dell'NFA_.

## Algoritmo
### Preliminari
Per definire l'algoritmo è prima necessario dare alcune definizioni fondamentali:
- _$\epsilon$-closure_
- _mossa_

#### $\epsilon$-closure
> Sia $q$ uno stato di un NFA. La $\epsilon$-closure di $q$ è l'insieme degli stati raggiungibili da $q$ solo con _mosse_ $\epsilon$.

Formalmente definiamo un [[Assioma|assioma]] e una [[Regole di inferenza|regola d'inferenza]]:
$$\begin{prooftree}
\AxiomC{}
\UIC{$\{q\} \subseteq \epsilon \text{-closure}(q)$}
\end{prooftree}$$
Ossia ogni stato è sempre raggiungibile da se stesso con una transizione $\epsilon$ (ovvio).

$$\begin{prooftree}
\AxiomC{$p \in \epsilon \text{-closure}(q)$}
\UIC{$\delta(p, \epsilon) \subseteq \epsilon \text{-closure}(q)$}
\end{prooftree}$$
Tipico ragionamento [[Induzione strutturale|induttivo]] delle regole d'inferenza[^1].

Se $P$ è un insieme di stati di un NFA, allora
$$\epsilon \text{-closure}(P) = \bigcup_{p \in P} \epsilon \text{-closure}(p)$$

#### Mossa
> Si definisce la mossa di un DFA nel contesto dell'algoritmo di costruzione per sottoinsiemi, una funzione definita come
> $$\text{mossa}: \mathscr{P}(Q) \times \Sigma \to \mathscr{P}(Q)$$
> tale che
> $$\text{mossa}(P, a) = \bigcup_{p \in P} \delta(p, a)$$
> dove $P$ è un insieme di stati di un NFA.

#### Conclusione
Assemblando le due notazioni, possiamo iniziare a definire le funzioni di transizioni del DFA equivalente. Infatti si ha che se:
- $\Delta$ è il _nome della funzione di transizione del DFA equivalente_
- $A$ è un _insieme di stati del NFA_
- $b \in \Sigma$

allora
$$\Delta(A, b) = \epsilon \text{-closure}(\text{mossa}(A, b))$$

E' importante capire i ruoli della $\epsilon \text{-closure}$ e della mossa, perché ognuno di loro è ciò che consente di deterministicizzare l'NFA! Infatti:
- **mossa**, a partire da un insieme di stati e da un carattere dell'alfabeto, raccoglie gli output della funzione di transizione per ognuno di questi stati con quel carattere, consentendo il raggruppamento di stati che diventerà un nuovo stato del DFA --> **risolve il fatto che ci siano più stati per una stessa coppia ($q$, $a$)**;
- **$\epsilon \text{-closure}$**, a partire dall'insieme di stati elaborati dalla mossa, amplia tale insieme con tutti gli stati raggiungibili da essi con transizioni-$\epsilon$ --> **risolve il problema dell'esistenza delle transizioni-$\epsilon$**.

### Subalgoritmi
Definiti le $\epsilon \text{-closure}$ formalmente, ora si vuole definire un algoritmo vero e proprio per il loro calcolo. In particolare, fissato $P$ insieme di stati di un NFA, calcoliamo $\epsilon \text{-closure}(P)$.
```R
T = P;
eps_clos(P) = P;
while T != NULL {
	"scegli un r in T e rimuovilo da T"
	for each s in delta(r, eps) {
		if s not in eps_clos(P) {
			add s to eps_close(P);
			add s to T;
		}
	}
}
```

#### Linguaggio accettato alternativo
Usando le $\epsilon\text{-closure}$ è possibile definire il [[Linguaggio accettato|linguaggio accettato]] da un NFA in modo più elegante.
Definisco la funzione
$$\hat{\delta}: Q \times \Sigma^{*} \to \mathscr{P}(Q)$$
tale che:
$$\hat{\delta}(q, \epsilon) = \epsilon\text{-closure}(q)$$
e
$$\hat{\delta}(q, xa) = \epsilon\text{-closure}(P)$$
dove $x \in \Sigma^{*}$ e
$$P = \{p \in Q | \exists r \in \hat{\delta}(q, x) \land p \in \delta(r, a)\}$$

Equivalentemente possiamo definire $\hat{\delta}$ come
$$\hat{\delta}(q, xa) = \epsilon \text{-closure} (\text{mossa}(\hat{\delta}(q, x), a)) = \epsilon \text{-closure} \left( \bigcup_{p \in \hat{\delta}(q, x)} \delta(p, a) \right)$$

Ad ogni modo, così facendo la definizione formale di stringa riconosciuta diventa
$$w \in L[N] \iff \exists p \in F : p \in \hat{\delta}(q_{0}, w)$$

Il significato della funzione $\hat{\delta}$ può essere facilmente espresso come segue: presa una stringa $w$ e uno stato iniziale $q_{0}$, allora $\hat{\delta}(q_{0}, w)$ è l'$\epsilon\text{-closure}$ dell'insieme degli stati percorsi per riconoscere $w$, e quindi l'insieme di stati raggiungibili con transizioni-$\epsilon$ a partire dall'insieme degli stati attraversati per riconoscere $w$.

### Costruzione per sottoinsiemi
Dato un NFA $N = (\Sigma, Q, \delta, q_{0}, F)$, l'algoritmo di costruzione per sottoinsiemi è:
```R
S = eps_clos(q_0);    # S è lo stato iniziale del DFA
T = {S}               # T è l'insieme degli stati del DFA
                      # S non è marcato all'inizio
while exists P in T : P not marked {
	mark P;
	for each a in Sigma {
		R = eps_clos(mossa(P, a));    # R è un eventuale nuovo stato del DFA
		if R not in T {
			add R to T;           # Non marco R perché dovrà essere definito!
		}
		Delta(P, a) = R
	}
}
```

Quindi, terminato l'algoritmo, definiamo il DFA come
$$M_{N} = (\Sigma, T, \Delta, \epsilon\text{-closure}(q_{0}), \mathscr{F})$$
dove $\mathscr{F}$ è l'insieme degli stati $\in T$ (che quindi sono insiemi!) considerati finali, e costruiti nel seguente modo:
$$R \in \mathscr{F} \iff \exists q \in R : q \in F$$

ossia **uno stato finale del DFA è un insieme di stati del NFA tale che almeno uno è uno stato finale**!

### Analisi
Nel [[Complessità computazionale|caso pessimo]] si ha che
$$T = \mathscr{P}(Q)$$
ossia il numero di stati del DFA risultante è uguale a $2^{n}$ dove $n = |Q|$ ([[Cardinalità|cardinalità]]).

Per esempio l'NFA
![[caso-pessimo-nfa-to-dfa-1.png]]
diventa il DFA
![[caso-pessimo-nfa-to-dfa-2.png]]

## Teorema
> Sia $N = (\Sigma, Q, \delta, q_{0}, F)$ un NFA e sia $M_{N}$ l'automa ottenuto con la costruzione dei sottoinsiemi, allora $M_{N}$ è un DFA e si ha che
> $$L[N] = L[M_{N}]$$

Come corollario si ha che _la classe dei linguaggi riconosciuti dagli NFA coincide con la classe di quelli riconosciuti dai DFA_.

### Dimostrazione
Supponiamo $N = (\Sigma, Q, \delta, q_{0}, F)$ un NFA e $M_{N} = (\Sigma, T, \Delta, \epsilon\text{-closure}(q_{0}), \mathscr{F})$ l'automa ottenuto con l'algoritmo di costruzione per sottoinsiemi.

Dobbiamo dimostrare che:
1. $M_{N}$ è un DFA, ossia deterministico;
2. $L[N] = L[M_{N}]$;

#### 1.
Ovvio, in quanto $\Delta(A, a)$ è definita per ogni coppia $(A, a)$, $\forall A \in T$ e $\forall a \in \Sigma$, _in modo univoco_ (per la costruzione), e il risultato di $\Delta$ è un elemento di $T$.

#### 2.
Prima di tutto osserviamo che per un DFA, $\forall R \in T \ \ \ \epsilon\text{-closure}(R) = R$, perché non ci sono mosse $\epsilon$. Quindi definiamo $i_{M} = \epsilon\text{-closure}(q_{0})$, ossia lo stato iniziale di $M_{N}$.

Vogliamo in definitiva mostrare che
$$\forall w \in \Sigma^{*} \ \ \ \hat{\delta}(q_{0}, w) = \hat{\Delta}(i_{M}, w)$$
per [[Induzione strutturale|induzione]] sulla lunghezza di $w$.

##### Caso base
Supponiamo $|w| = 0$, e quindi $w = \epsilon$, allora:
$$\hat{\delta}(q_{0}, \epsilon) = \epsilon\text{-closure}(q_{0}) = i_{M}$$

D'altro canto, si ha che
$$\hat{\Delta}(i_{M}, \epsilon) = \epsilon\text{-closure}(i_{M}) = i_{M}$$
per l'osservazione l'iniziale.

Da ciò, vale
$$\hat{\delta}(q_{0}, \epsilon) = \hat{\Delta}(i_{M}, \epsilon)$$

##### Caso induttivo
Supponiamo che $w = xa$, con $x \in \Sigma^{*}, a \in \Sigma$, e per ipotesi induttiva che
$$\hat{\delta}(q_{0}, x) = \hat{\Delta}(i_{M}, x)$$

Dobbiamo dimostrare che
$$\hat{\delta}(q_{0}, xa) = \hat{\Delta}(i_{M}, xa)$$

Allora, per definizione di $\hat{\delta}$ si ha che:
$$\hat{\delta}(q_{0}, xa) = \epsilon\text{-closure}(\text{mossa}(\hat{\delta}(q_{0}, x), a))$$
e per ipotesi induttiva
$$\epsilon\text{-closure}(\text{mossa}(\hat{\delta}(q_{0}, x), a)) = \epsilon\text{-closure}(\text{mossa}(\hat{\Delta}(i_{M}, x), a))$$
da cui, considerando che su $M_{N}$, in quanto DFA, non fa effetto $\epsilon\text{-closure}$
$$\epsilon\text{-closure}(\text{mossa}(\hat{\Delta}(i_{M}, x), a)) = \text{mossa}(\hat{\Delta}(i_{M}, x), a)$$
che per definizione è
$$\text{mossa}(\hat{\Delta}(i_{M}, x), a) = \hat{\Delta}(i_{M}, xa)$$

**Qed**.

## Referenze
[^1]: nota come suona meglio la lettura della regola in top-down