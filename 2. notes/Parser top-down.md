---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 19-08-2025 16:02:11
links:
  - "[[Lecture 24102024120228]]"
  - "[[Lecture 07112024120244]]"
---
# Parser top-down
---
## Introduzione
In realtà abbiamo già anticipato velatamente un parser top-down quando abbiamo enunciato il [[Linguaggio libero#Legame con PDA|teorema]] che lega i [[Linguaggio libero|linguaggi liberi]] ai [[Automa a pila|PDA]].

Infatti, definita la [[Grammatiche libere|grammatica libera]] $G = (NT, T, S, R)$, possiamo costruire il PDA $M = (T, \{q\}, T \cup NT, \delta, q, S, \varnothing)$ tale che $\delta$ è definita:
- $(q, \beta) \in \delta(q, \epsilon, A)$ se $A \to \beta \in R$ (_espandi_);
- $(q, \epsilon) \in \delta(q, a, a)$ $\forall a \in T$ (_consuma_);

tale che [[Linguaggio accettato|riconosce]] per pila vuota $L(G)$, ossia $L(G) = P[M]$.

Per esempio, presa la grammatica $S \to aSb|\epsilon$ allora il PDA corrispondente è:
![[parser-top-down-1.png]]

E se dovessimo accettare la stringa $aabb$, allora le _descrizioni istantanee_ dell'automa per ogni derivazione sarebbero:
$(q, aabb, S) \vdash (q, aabb, aSb) \vdash (q, abb, Sb) \vdash (q, abb, aSbb) \vdash (q, bb, Sbb) \vdash (q, bb, bb) \vdash (q, b, b) \vdash (q, \epsilon, \epsilon)$

Il problema, ovviamente, sta nel _forte nondeterminismo_! Ma questo si può risolvere introducendo il meccanismo del **[[Look-ahead|look-ahead]]**. Infatti, per questa grammatica, è sufficiente leggere solo il prossimo simbolo per togliere il nondeterminismo dal PDA:
- se leggo $a$ $\implies$ espando $S \to aSb$;
- se leggo $b$ $\implies$ espando $S \to \epsilon$.

Questa grammatica, di fatti, si dice di classe $LL(1)$, perché consente di costruire un parser DPDA _left-to-right_, _left-derivation_ che richiede 1 solo simbolo di look-ahead.

Ad ogni modo, dalla derivazione del parser è facile quindi ricavare l'[[Albero di derivazione|albero di derivazione]]:
![[parser-top-down-2.png]]

<u>Nota bene</u>: altre grammatiche sono $LL(2)$, ossia richiedono 2 simboli di look-ahead. Per esempio
$$S \to aSb | ab$$

Attenzione: le _grammatiche left-recursive_ (con ricorsione sinistra) _non consentono di essere accettate correttamente da parser top-down_! Rischiano infatti di non consumare l'input e quindi di continuare ad espandere il simbolo iniziale e a scrivere sulla pila --> non si può sapere quando fermarsi, come avviene nel seguente caso:
$$G \to Sb|a$$
$$(q, ab, S) \vdash (q, ab, Sb) \vdash (q, ab, Sbb) \vdash \cdots$$

Bisogna trasformare quella grammatica, quindi, in una equivalente senza ricorsione sinistra:
$$S \to aA$$
$$A \to bA | \epsilon$$

Questa è adatta al top-down parsing, infatti:
- se leggo $a$ e sulla pila c'è $S$ $\implies$ espando $S \to aA$;
- se leggo $b$ e sulla pila c'è $A$ $\implies$ espando $A \to bA$;
- se leggo \$ (fine stringa) e sulla pila c'è $A$ $\implies$ espando $A \to \epsilon$.

Quindi la grammatica è di tipo $LL(1)$.

## Costruzione
Dopo aver dato un'infarinatura dell'idea di parser top-down, cominciamo a costruirlo formalmente partendo da un esempio semplice: un _parser top-down nondeterministico_, anche detto _a discesa ricorsiva_.

### Parser a discesa ricorsiva
Data una grammatica libera $G$ per ogni nonterminale $A$ con produzioni
$$A \to X_{1}^{1} \cdots X_{n_{1}}^{1} | \cdots | X_{1}^{k} \cdots X_{n_{k}}^{k}$$
definisco la funzione `A`:
- `function A()`
	- scegli nondeterministicamente $h$ tra $1$ e $k$, ovvero una produzione $A \to X_{1}^{h}\cdots X_{n_{h}}^{h}$;
	- `for i=1 to` $n_{k}$
		- `if` $X_{i}^{h} \in NT$
			- $X_{i}^{h}$`()`;
		- `else if` $X_{i}^{h}$ simbolo corrente dell'input
			- avanza di un simbolo sull'input;
		- `else`
			- `Fail()` --> torna alla scelta nondeterministica di $h$
	- `return`;

Si comincia invocando la funzione per il simbolo iniziale $S$.

#### Esempio
Prendiamo in esempio la grammatica
$$S \to ac|aSb$$
che [[Linguaggio generato|genera]] il linguaggio $L = \{a^{n+1}cb^{n} | n \geq 0\}$, e consideriamo l'input $aacb$.
Si invoca la funzione del simbolo iniziale $S$:
- viene scelto $h=1$, ossia la produzione $S \to ac$;
	- $a$ -> viene fatto match con $a$ sull'input;
	- $c$ -> viene invocato `Fail()`, perche' non corrisponde all'input ($a$) -> **backtracking**!
- viene scelto $h=2$, ossia la produzione $S \to aSb$;
	- $a$ -> viene fatto match con $a$ sull'input;
	- $S$ -> invocata la funzione $S$:
		- viene scelto $h = 1$, ossia la produzione $S \to ac$;
			- $a$ -> viene fatto match con $a$ sull'input;
			- $c$ -> viene fatto match con $a$ sull'input;
			- `return`
	- $b$ -> viene fatto match con $b$ sull'input;
	- `return` --> **la stringa viene riconosciuta**!

#### Osservazioni
Questo parser non e' altro che l'implementazione pratica del parser [[DPDA]] monostato! Infatti **lo [[Stack|stack]] di chiamate ricorsive simula in realta' proprio il comportamento della pila del DPDA**, ossia le [[Derivazione canonica sinistra|derivazioni canoniche sinistre]]!

Tuttavia, ovviamente, questo parser e' **estremamente inefficiente**: c'e' **nondeterminismo**, e addirittura nel caso peggiore avremmo necessita' di cercare tutte le strade possibili --> la [[Complessità computazionale|complessita']] diventa esponenziale sulla lunghezza della stringa $w$, dove la base $b$ e' data dal massimo numero di produzioni per uno stesso nonterminale
$$O(b^{|w|})$$

### De-nondeterminizazzione
Dovremmo quindi cercare di guidare la scelta delle produzioni: come gia' anticipato **questo puo' essere fatto guardando il prossimo o i prossimi caratteri**, ossia con il meccanismo del [[Look-ahead|look-ahead]], e in particolare con le funzioni ausilierie di [[First e follow|first e follow]].

Una volta fatta analizzati first e follow (caso 1 solo carattere look-ahead), si giunge alla composizione della [[Tabella di parsing LL(1)|tabella di parsing]] $LL(1)$.

### Parser $LL(1)$ non ricorsivo
Fatta la tabella di parsing $LL(1)$, possiamo definire un parser che accetta in modo _deterministico_ [[Grammatiche LL(1)|grammatiche]] $LL(1)$. Questo, a differenza del precedente, usera' esplicitamente una [[Pila|pila]], e non sfruttera' la [[Ricorsione|ricorsione]].

Parser:
- $Pila := S\$$;
- $X := S$;
- $input := w\$$;
- $i_{C} :=$ primo carattere dell'input;
- `while (`$X \neq \$$`)`:
	- `if (` $X$ e' un terminale `)`:
		- `if (`$X = i_{C}$`)`:
			- `pop` $X$ dalla pila;
			- avanza $i_{C}$ sull'input;
		- `else`:
			- `error()`;    --> _caso no match_
		- $X :=$ top della pila;
	- `else`:
		- `if (`$M[X, i_{C}] = X \to Y_{1} \cdots Y_{n}$`)`:
			- `pop` $X$ dalla pila;
			- `push` $Y_{1} \cdots Y_{n}$ sulla pila (con $Y_{1}$ in cima);
			- `output` la produzione $X \to Y_{1} \cdots Y_{n}$;
		- `else`:
			- `error()`;   --> _caso bianco_
		- $X :=$ top della pila;
- `if (`$i_{C} \neq \$$`)`:
	- `error()`;    --> _caso di svuotamento della pila ma input non finito_

#### Esempi
##### 1
Prendiamo la grammatica $G$
$$S \to aAB | bS \ \ \ \ \ A \to a \ \ \ \ \ B \to b$$
e notiamo che $L(G) = \mathscr{L}[b^{*}aab]$, ossia che il linguaggio generato da $G$ e' lo stesso [[Linguaggio denotato da un'espressione regolare|denotato]] dall'[[Espressione regolare|espressione regolare]] $b^{*}aab$.

Ora, $G$ e' $LL(1)$, infatti
$$\text{First}(aAB) \cap \text{First}(bS) = \varnothing$$
e non ci sono produzioni-$\epsilon$ (quindi neanche $\epsilon$ appartenenti a qualche first).

Creiamoci la tabella dei first e follow:

|     | $\text{First}$ | $\text{Follow}$ |
| --- | -------------- | --------------- |
| $S$ | $a, b$         | $\$$            |
| $A$ | $a$            | $b$             |
| $B$ | $b$            | $\$$            |

Quindi, costruiamoci la tabella di parsing $LL(1)$:

|     | $a$         | $b$        | $\$$ |
| --- | ----------- | ---------- | ---- |
| $S$ | $S \to aAB$ | $S \to bS$ |      |
| $A$ | $A \to a$   |            |      |
| $B$ |             | $B \to b$  |      |

Quindi eseguiamo il parser $LL(1)$ non ricorsivo come specificato, sull'input $baab\$$:
![[parser-top-down-ex-1.png]]
che produce l'albero di derivazione:
![[parser-top-down-ex-1-albero-derivazione.png]]

Notiamo che sull'input $aabb\$$, che non appartiene al linguaggio, andiamo nel caso in cui la pila e' vuota ma l'input non e' finito:
![[parser-top-down-ex-2.png]]

Invece, sull'input $abb\$$, sempre non appartenente al linguaggio, finiamo su una casella bianca della tabella:
![[parser-top-down-ex-3.png]]

##### 2
Prendiamo la grammatica $G$
$$S \to aAB | B \ \ \ \ \ A \to a \ \ \ \ \ B \to bB|b$$
e notiamo che $L(G) = \mathscr{L}[(aa|\epsilon)b^{+}]$, ma soprattutto che _$G$ non e' $LL(1)$_: _per via di $B \to bB | b$_!

Tuttavia, [[Fattorizzazione a sinistra|fattorizzando a sinistra]] $B$ otteniamo la [[Grammatiche equivalenti|grammatica equivalente]] $G'$
$$S \to aAB|B \ \ \ \ \ A \to a \ \ \ \ \ B \to bB' \ \ \ \ \ B' \to \epsilon | B$$

Questa $G'$ invece e' $LL(1)$, infatti usando il [[Grammatiche LL(1)#First e follow|teorema dei first e follow]] notiamo che:
- $\text{First}(aAB) \cap \text{First}(B) = \varnothing$;
- $\text{First}(\epsilon) \cap \text{First}(B) = \varnothing$;
- $\text{First}(B) \cap \text{Follow}(B') = \varnothing$.

Costruiamo la tabella dei first e follow:

|      | $\text{First}$ | $\text{Follow}$ |
| ---- | -------------- | --------------- |
| $S$  | $a, b$         | $\$$            |
| $A$  | $a$            | $b$             |
| $B$  | $b$            | $\$$            |
| $B'$ | $b, \epsilon$  | $\$$            |

Ora ci calcoliamo la tabella di parsing $LL(1)$:

|      | $a$         | $b$         | $\$$              |
| ---- | ----------- | ----------- | ----------------- |
| $S$  | $S \to aAB$ | $S \to B$   |                   |
| $A$  | $A \to a$   |             |                   |
| $B$  |             | $B \to bB'$ |                   |
| $B'$ |             | $B' \to B$  | $B' \to \epsilon$ |

Se eseguiamo il parser $LL(1)$ non ricorsivo sull'input $aabb\$$ otteniamo
![[parser-top-down-ex-4.png]]

## Referenze