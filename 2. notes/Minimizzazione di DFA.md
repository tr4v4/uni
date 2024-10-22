---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 20-10-2024 16:31:44
links:
  - "[[Lecture 10102024120505]]"
  - "[[Lecture 15102024110302]]"
---
# Minimizzazione di DFA
---
## Introduzione
Abbiamo visto che con l'[[Algoritmo|algoritmo]] di [[Costruzione per sottoinsiemi|costruzione per sottoinsiemi]] è possibile ottenere un [[DFA]] a partire da qualunque [[NFA]]. Tuttavia, _se l'NFA ha $n = |Q|$ stati, il DFA equivalente potrebbe avere $2^{n}$ stati_.

Quello che si cerca allora di fare, una volta costruito il DFA, è di **minimizzare il suo numero di stati, trovando un DFA equivalente che ha il minor numero di stati**: l'_automa minimo_.

Consideriamo per esempio il DFA
![[esempio-minimizzazione-dfa-1.png]]
tale che il suo [[Linguaggio accettato|linguaggio accettato]] è definito dall'[[Espressione regolare|espressione regolare]]
$$L[N] = (a|b)a^{*}b(a|b)^{*}$$

Se per notazione definiamo $L[N, q_{i}]$ come il linguaggio accettato dall'automa $N$ a partire dallo stato $q_{i}$, allora
$$L[N, q_{0}] = L[N] = (a|b)a^{*}b(a|b)^{*}$$
e in particolare
$$L[N, q_{1}] = a^{*}b(a|b)^{*} = L[N, q_{2}]$$

Per cui gli stati $q_{1}$ e $q_{2}$ sono assolutamente equivalenti: si dicono **indistinguibili**. Possiamo _fonderli_ in un unico stato e ottenere un DFA equivalente:
![[esempio-minimizzazione-dfa-2.png]]

Il DFA ottenuto _non solo è più piccolo, ma è minimo_: **non ci sono due stati tra loro equivalenti**.

## Notazioni
### $\hat{\delta}$
> Per un DFA $N = (\Sigma, Q, \delta, q_{0}, F)$, definiamo $\hat{\delta}: Q \times \Sigma^{*} \to Q$ come l'unico stato che posso raggiungere seguendo il cammino di una stringa $w$ e partendo dallo stato $q_{0}$, o [[Induzione strutturale|induttivamente]] sulla lunghezza di $w$:
> $$\hat{\delta}(q, \epsilon) = q$$
> e
> $$\hat{\delta}(q, xa) = \delta(\hat{\delta}(q, x), a)$$

Da questo deriva una differente definizione di stringa accettata dall'automa:
$$w \in L[N] \iff \hat{\delta}(q, w) \in F$$

### Equivalenza tra stati
> Due stati $q_{1}, q_{2}$ di un DFA $N$ sono **equivalenti** (o **indistinguibili**) se
> $$\forall x \in \Sigma^{*}. \ \ \ \hat{\delta}(q_{1}, x) \in F \iff \hat{\delta}(q_{2}, x) \in F$$
> per cui se
> $$L[N, q_{1}] = L[N, q_{2}]$$

Finora abbiamo intuito che per vedere se un DFA è minimo o meno, basta prendere ogni coppia dei suoi stati e vedere se questi sono equivalenti: _bisognerebbe controllare che il linguaggio accettato sia lo stesso di entrambi gli stati per ogni stringa possibile dell'alfabeto ($\Sigma^{*}$)_.

Essendo ciò impossibile, possiamo usare la **contronominale**:
> Due stati $q_{1}, q_{2}$ non sono equivalenti se
> $$\exists x \in \Sigma^{*}. \ \ \ \hat{\delta}(q_{1}, x) \in F \land \hat{\delta}(q_{2}, x) \notin F$$
> o, viceversa se
> $$\exists x \in \Sigma^{*}. \ \ \ \hat{\delta}(q_{1}, x) \notin F \land \hat{\delta}(q_{2}, x) \in F$$

## Idea
### Strategia
A partire dal risultato sulle equivalenze tra stati, possiamo definire uno pseudo-algoritmo per minimizzare un DFA che non cerchi le equivalenze tra stati, ma bensì le non-equivalenze: **cerco di distinguere due stati considerando le $x \in \Sigma^{*}$ a partire dalla più corta ($\epsilon$)**. Escludo iterativamente le coppie di stati non equivalenti a cominciare dalla stringa $\epsilon$.

Prendiamo in esempio l'automa
![[esempio-minimizzazione-dfa-3.png]]

e applichiamo l'algoritmo:
1. $w = \epsilon$, per definizione di DFA (non essendoci transizioni-$\epsilon$) gli unici stati che riconoscono la stringa vuota sono quelli finali, per cui si possono eliminare tutte le coppie di stati che contengono gli stati finali --> escludiamo $(A, D)$, $(B, D)$ e $(C, D)$;
2. $w = a$
	1. $\delta(B, a) = B$ e $\delta(C, a) = D$, ma $(B, D)$ è già stata esclusa al passo precedente, per cui neanche $(B, C)$ è una coppia di stati equivalente --> la escludiamo;
	2. $\delta(A, a) = B$ e $\delta(C, a) = D$, per il discorso di prima neanche $(A, C)$ sono equivalenti --> escludiamo la coppia;
	3. non posso escludere nessun'altra coppia;
3. $w = b$, non posso escludere nessun'altra coppia (provare per credere);
4. $w \in \{a, b\}^{*}$, posso provarci all'infinito, ma non riuscirò ad escludere nessun'altra coppia!

Le coppie rimaste saranno quelle equivalenti, per cui non sono riuscito a trovare una $x \in \Sigma^{*}$ tale che li rendesse non-equivalenti. Sono $(A, B), (A, A), (B, B), (C, C), (D, D)$.

Ovviamente, le coppie del tipo $(q, q)$ sono triviali: ogni stato è equivalente a se stesso. Per cui l'unica reale coppia di stati equivalenti è
$$(A, B)$$

Fondendoli ecco che si ottiene il DFA minimo
![[esempio-minimizzazione-dfa-4.png]]

### Teoria
Ma su quali basi teoriche si fonda questa strategia? Per poterci fidare, è necessario formalizzare alcuni concetti.

#### $\sim_{i}$
> Dato un DFA $M = (\Sigma, Q, \delta, q_{0}, F)$, definiamo una famiglia di [[Relazione|relazioni]] $\sim_{i} \subseteq Q \times Q$ induttivamente nel seguente modo:
> $$\sim_{0} = F \times F \cup (Q \setminus F) \times (Q \setminus F)$$
> $$q_{1} \sim_{i+1} q_{2} \iff \forall a \in \Sigma. \ \ \ \delta(q_{1}, a) \sim_{i} \delta(q_{2}, a)$$

Il significato dei due casi è:
- $\sim_{0}$ altro non è che _l'insieme delle coppie tra stati finali unito all'insieme delle coppie tra stati non finali_, e rappresenta infatti _tutte le possibili coppie che possono rappresentare un'equivalenza di stati quando analizzo la stringa $w = \epsilon$_ --> si vanno ad _escludere le coppie tra stati finali e non finali_;
- $q_{1}$ è equivalente a $q_{2}$ se $\forall x \in \Sigma^{*}$ con $|x| \leq i+1$ avviene che $\hat{\delta}(q_{1}, x) \in F \iff \hat{\delta}(q_{2}, x) \in F$ --> esattamente la _definizione di equivalenza tra stati_, per cui stiamo scremando $\sim_{i+1}$ in modo tale che _contenga solo gli stati fino a quel momento considerati equivalenti_ (quel momento è $i+1$, infatti consideriamo solo le $x$ tali che $|x| \leq i+1$).

<u>Nota bene</u>: questa notazione altro non è che la **formalizzazione matematica della strategia ideata**!

#### Osservazioni
Questa formalizzazione ci consente di dimostrare delle proprietà matematiche proprio sull'algoritmo proposto.

##### 1.
La relazione identità $\text{Id} = \{(q, q) | q \in Q\}$ è tale che
$$\text{Id} \subseteq \sim_{i} \ \ \ \forall i$$
o in altre parole "_ogni stato è sempre equivalente a se stesso_".

##### 2.
Si scopre che $\sim_{i}$ è una [[Relazione di equivalenza|relazione di equivalenza]] $\forall i$. Ovvio.

##### 3.
Ovviamente si ha
$$\sim_{i+1} \subseteq \sim_{i}$$

##### 4.
Questa è fondamentale:
$$\exists k : \sim_{k} = \sim_{k+1} \implies \sim_{j} = \sim_{k} \ \ \ \forall j > k$$

Il che significa che se alla $k+1$-esima iterazione ($|w| = k+1$) il numero di coppie di stati attualmente considerate equivalenti non diminuisce, ossia non escludo più coppie non-equivalenti, allora non potrò più escludere coppie: **ho trovato la soluzione**.

###### Dimostrazione
Semplifichiamo la dimostrazione, assumendo che $\sim_{2} = \sim_{1}$ e dimostrando l'[[Dimostrazione per assurdo|assurdo]] $\sim_{3} \neq \sim_{2}$.
Per l'osservazione 3 vale per forza $\sim_{3} \subset \sim_{2}$, ovvero che
$$\exists q_{1}, q_{2} : q_{1} \sim_{2} q_{2} \land q_{1} \not \sim_{3} q_{2}$$

L'ipotesi $q_{1} \not \sim_{3} q_{2}$ significa che al passo 3 dell'algoritmo ($|w| = 3$) gli stati del DFA $q_{1}$ e $q_{2}$ sono considerati non-equivalenti, ovvero
![[Drawing 2024-10-20 21.03.16.excalidraw|700]]

Dalla raffigurazione possiamo notare che dagli stati $A_{1}, A_{2}$, per la stessa ipotesi $q_{1} \not \sim_{3} q_{2}$, si ha che $A_{1} \not \sim_{2} A_{2}$.
Per ipotesi $\sim_{2} = \sim_{1}$, per cui $A_{1} \not \sim_{1} A_{2}$:
![[Drawing 2024-10-20 21.28.40.excalidraw|700]]

Ma questo è in contraddizione con $q_{1} \sim_{2} q_{2}$: _assurdo_!

**Qed**.

##### 5.
Quest'ultima osservazione ci dice che il $k$ supposto nella proposizione precedente esiste e ha un limite:
$$\exists k < |\sim_{0}| : (\sim_{k} = \sim_{k+1} \implies \sim_{j} = \sim_{k} \ \ \ \forall j > k)$$

Infatti nella peggiore delle ipotesi, da $\sim_{0}$ _ad ogni iterazione rimuovo 1_ (o meglio 2, per la simmetria) _coppia_.

In realtà si potrebbe dimostrare che $k \leq |Q| - 1$, questo perché $|Q|-1$ è la _lunghezza del massimo [[Cammino|cammino]] aciclico_.

## Algoritmo
L'algoritmo che implementa in modo sistematico la strategia adottata e i criteri di arresto elaborati, si chiama [[Algoritmo di tabella a scala|algoritmo di tabella a scala]].

## Automa minimo
> Dato un DFA $M = (\Sigma, Q, \delta, q_{0}, F)$, l'automa minimo equivalente $M_{\min} = (\Sigma, Q_{\min}, \delta_{\min}, [q_{0}], F_{\min})$ è dato da:
> - $Q_{\min} = \{[q] | q \in Q\}$ dove $[q] = \{q' \in Q | q \sim q'\}$, ossia è l'insieme delle [[Classe di equivalenza|classi di equivalenza]] della relazione di equivalenza tra stati $\sim$;
> - $\delta_{\min}([q], a) = [\delta(q, a)]$;
> - $F_{\min} = \{[q] | q \in F\}$.

<u>Osservazione</u>: _non esistono 2 stati distinti in $M_{\min}$ che siano tra loro equivalenti_, ossia $[q] \neq [q'] \implies q \nsim q'$, usando la contronominale si produrrebbe l'assurdo assumendo che gli stati sono equivalenti.

<u>Nota bene</u>: è possibile definire le classi di equivalenza sulla relazione $\sim$ perché essa stessa è una relazione di equivalenza, come si evince dall'[[Minimizzazione di DFA#2.|osservazione 2]].

### Notazioni
Se per un DFA abbiamo definito $\hat{\delta}$ in un determinato modo, per il DFA minimo associato non cambia molto concettualmente, ma la notazione è più pesante.

Definiamo $\hat{\delta}_{\min}$ come:
$$\hat{\delta}_{\min} : Q_{\min} \times \Sigma^{*} \to Q_{\min}$$
$$\hat{\delta}_{\min}([q], \epsilon) = [q]$$
$$\hat{\delta}_{\min}([q], xa) = \delta_{\min}(\hat{\delta}([q], x), a)$$
da cui
$$w \in L[M_{\min}] \iff \hat{\delta}_{\min}([q_{0}], w) \in F_{\min}$$

### Teorema minimo
> Dato un DFA $M = (\Sigma, Q, \delta, q_{0}, F)$, _l'automa minimo $M_{\min} = (\Sigma, Q_{\min}, \delta_{\min}, [q_{0}], F_{\min})$ riconosce lo stesso linguaggio di $M$ ed ha il minimo numero di stati tra tutti gli automi deterministici_.

#### Dimostrazione
##### Ben definizione
Intanto è necessario mostrare che $M_{\min}$ è _ben definito_, ossia che la definizione di $\delta_{\min}$ non dipende dallo stato usato come rappresentante della classe di equivalenza. Questo è ovvio, infatti
$$[q] = [q'] \implies \delta_{\min}([q], a) = \delta_{\min}([q'], a)$$

##### Linguaggio riconosciuto
Dobbiamo dimostrare che il linguaggio riconosciuto da $M$ è lo stesso riconosciuto da $M_{\min}$, ossia
$$L[M] = L[M_{\min}]$$

Per farlo ci è sufficiente dimostrare che
$$\forall w \in \Sigma^{*} \ \ \ \hat{\delta}(q_{0}, w) = r \iff \hat{\delta}_{\min}([q_{0}], w) = [r]$$
o equivalentemente
$$\forall w \in \Sigma^{*} \ \ \ \hat{\delta}_{\min}([q_{0}], w) = [\hat{\delta}(q_{0}, w)]$$

Procedo per induzione sulla lunghezza di $w$:
- $w = \epsilon$: ho $\hat{\delta}_{\min}([q_{0}], \epsilon) = [q_{0}] = [\hat{\delta}(q_{0}, \epsilon)]$;
- $w = xa$: ho $\hat{\delta}_{\min}([q_{0}], xa) = \delta_{\min}(\hat{\delta}_{\min}([q_{0}], x), a) = \delta_{\min}([\hat{\delta}(q_{0}, x)], a) = [\delta(\hat{\delta}(q_{0}, x), a)] = [\hat{\delta}(q_{0}, xa)]$
**Qed**.

##### Minimo
Dobbiamo dimostrare che $M_{\min}$ è effettivamente minimo, e _lo facciamo supponendo per assurdo che esista un automa deterministico con un numero minore di stati di quello minimo e che sia equivalente ad esso_.

Supponiamo allora che esista un DFA $N$ tale che $L[N] = L[M_{\min}]$, ma con un numero inferiore di stati, e facciamo 4 osservazioni.

###### 1.
Gli _stati iniziali di $N$ e $M_{\min}$ devono per forza essere equivalenti_, perché per ipotesi $L[N] = L[M_{\min}]$.

###### 2.
Se $p \in Q_{\min}$ e $q \in Q$ sono equivalenti, allora _sono equivalenti anche i loro successori $\forall a \in \Sigma$_.

###### 3.
Si nota che $N$ non ha stati irraggiungibili dal suo iniziale, altrimenti potrei costruire $N$ con ancora meno stati.
Ugualmente, $M_{\min}$ non ha stati irraggiungibili per costruzione.

Allora per l'osservazione precedente, _ogni stato di $M_{\min}$è equivalente ad almeno uno stato di $N$_. Questo perché $|Q| < |Q_{\min}|$, e tutti questi stati sono raggiungibili (sia in $N$ che in $M_{\min}$). Sapendo che gli stati iniziali di $N$ e $M_{\min}$ sono equivalenti, allora lo devono essere anche i successori, ed essendo tutti gli stati raggiungibili il ragionamento si protrae a catena per ogni stato di $M_{\min}$ e $N$.

###### 4.
Si conclude facendo notare che poiché $M_{\min}$ ha meno stati di $N$, due stati $p, p'$ di $M_{\min}$ devono essere equivalenti ad uno stesso stato $q$ di $N$. Ma la relaizone di equivalenza $\sim$ è transitiva! Perciò
$$p \sim q \land q \sim p' \implies p \sim p'$$
e _questo è un assurdo considerato che non esistono due stati distinti in $M_{\min}$ che siano tra loro equivalenti_.

**Qed**.

## Referenze