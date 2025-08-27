---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 28-10-2024 18:32:54
links:
  - "[[Lecture 17102024120438]]"
  - "[[Lecture 18102024090854]]"
---
# NPDA
---
## Introduzione
> Un **NPDA** (_Automa a pila nondeterministico_) è un [[Automa a pila|automa a pila]] definito da una 7-upla
> $$(\Sigma, Q, \Gamma, \delta, q_{0}, \bot, F)$$
> dove:
> - $\Sigma$ è un _alfabeto finito di simboli in input_
> - $Q$ è un _insieme finito di stati_
> - $\Gamma$ è un _insieme finito di simboli della pila_
> - $q_{0} \in Q$ è lo _stato iniziale_
> - $\bot \in \Gamma$ è il _simbolo iniziale sulla pila_
> - $F \subseteq Q$ è l'_insieme degli stati finali_
> - $\delta$ è la _funzione di transizione_ del tipo $$\delta: Q \times (\Sigma \cup \{\epsilon\}) \times \Gamma \to \mathscr{P}_{fin}(Q \times \Gamma^{*})$$

## Caratteristiche
Ovviamente la funzione $\delta$ rimane la più importante. In particolare, per gli automi a pila nondeterministici la funzione di transizione considera 3 fattori di input:
- $Q$, lo stato in cui si trova;
- $\Sigma \cup \{\epsilon\}$, la stringa che legge in input (anche niente, $\epsilon$);
- $\Gamma$, il simbolo sulla cima della pila;

In output, invece, $\delta$ restituisce l'[[Assioma dell'insieme potenza|insieme delle parti]] delle [[Coppia ordinata|coppie]]:
- $Q$, lo stato in cui "atterro";
- $\Gamma^{*}$, la stringa che scrivo sulla pila (anche $\epsilon$);

La **transizione consuma la stringa in input, consuma il simbolo in cima della pila (pop) e scrive in cima alla pila una stringa (push)**.

Il nondeterminismo sta nel fatto che:
- $|\delta(q, a, A)|$ può essere $> 1$, ossia **per una stessa tripla $q \in Q, a \in \Sigma \cup \{\epsilon\}, A \in \Gamma$, ci possono essere più coppie (stato, stringa su pila) su cui andare**;
- l'esistenza delle **transizioni-$\epsilon$**, per cui potrebbe esistere un qualche $q \in Q, a \in \Sigma \cup \{\epsilon\}, A \in \Gamma$ tale che $|\delta(q, a, A)| = 1$ ma anche $|\delta(q, \epsilon, A)| = 1$;

Come gli automi a pila, anche gli NPDA possono essere rappresentati da [[Diagramma di transizione|diagrammi di transizione]] modificati adeguatamente.

## Transizioni
### Descrizione istantanea
La descrizione istantanea, o configurazione, di un NPDA è una tripla
$$(q, w, \beta)$$
con:
- $q \in Q$ - stato corrente
- $w \in \Sigma^{*}$ - input ancora non letto
- $\beta \in \Gamma^{*}$ - stringa sulla pila

<u>Nota bene</u>: per convenzione, il _top_ è il _simbolo più a sinistra della pila_ (che viene raffigurata orizzontalmente e non verticalmente);

### Mossa
Data l'esistenza delle transizioni-$\epsilon$, un NPDA può fare due mosse per ogni tripla, formalizzate con le seguenti [[Regole di inferenza|regole di inferenza]]:
$$
\begin{prooftree}
\AxiomC{$(q', \alpha) \in \delta(q, a, x)$}
\UIC{$(q, aw, x\beta) {\vdash_{N}} (q', w, \alpha \beta)$}
\end{prooftree}
$$
$$
\begin{prooftree}
\AxiomC{$(q', \alpha) \in \delta(q, \epsilon, x)$}
\UIC{$(q, w, x\beta) {\vdash_{N}} (q', w, \alpha \beta)$}
\end{prooftree}
$$

### Computazione
Allo stesso modo definiamo [[Induzione strutturale|induttivamente]] più mosse con la formalizzazione di computazione:
$$
\begin{prooftree}
\AxiomC{}
\UIC{$(q, w, \beta) {\vdash_{N}}^{*} (q, w, \beta)$}
\end{prooftree}
$$
$$
\begin{prooftree}
\AxiomC{$(q, w, \beta) {\vdash_{N}}^{*} (q', w', \beta') \ \ \ (q', w', \beta') \vdash_{N} (q'', w'', \beta'')$}
\UIC{$(q, w, \beta) {\vdash_{N}}^{*} (q'', w'', \beta'')$}
\end{prooftree}
$$
ossia la chiusura riflessiva e transitiva di $\vdash_{N}$.

## Linguaggio accettato
Per un NPDA esistono due modalità di riconoscimento di una stringa:
1. **per stato finale**, ovvero $$L[N] = \{w \in \Sigma^{*} | (q_{0}, w, \bot) {\vdash_{N}}^{*} (q, \epsilon, \alpha), q \in F\}$$
2. **per pila vuota**, ovvero $$P[N] = \{w \in \Sigma^{*} | (q_{0}, w, \bot ) {\vdash_{N}}^{*} (q, \epsilon, \epsilon)\}$$
<u>Osservazione</u>: spesso si ha che per un PDA $N$ $$L[N] \neq P[N]$$
Ma dimostreremo che
$$L = L[N] \implies \exists N' : L = P[N']$$
e viceversa che
$$L = P[N] \implies \exists N' : L = L[N']$$

ossia che **la classe dei [[Linguaggio accettato|linguaggi riconosciuti]] da PDA per stato finale o per pila vuota è la stessa**.

### Teorema
> La _classe dei linguaggi riconosciuti da PDA per stato finale o per pila vuota è la stessa_. In particolare, preso un PDA $N$:
> - $L = L[N] \implies \exists N' : L = P[N']$
> - $L = P[N] \implies \exists N' : L = L[N']$

#### Dimostrazione
Se $N$ riconosce $L$ per pila vuota e $\bot$ è il simbolo iniziale della sua pila, allora costruisco $N'$ wrappando $N$ nel seguente modo:
![[pila-vuota-a-stato-finale.png]]

Così facendo infatti:
- il simbolo iniziale della pila di $N'$ è $Z$;
- ogni stato di $N$ ha una nuova transizione-$\epsilon$ che legge $Z$ dalla pila e porta allo stato finale di $N'$ $f$;

Quindi, **ogni stringa riconosciuta per pila vuota da $N$ non svuoterà del tutto la pila** (rimane $Z$ di $N$) e **sarà costretta ad andare nello stato finale $f$ con la transizione-$\epsilon$**.

Se invece $N$ riconosce $L$ per stato finale, allora costruisco $N'$ wrappando $N$ nel seguente modo:
![[stato-finale-a-pila-vuota.png]]

Così facendo:
- il simbolo iniziale della pila di $N'$ è $Z$;
- ogni stato finale di $N$ punta con una transizione-$\epsilon$ e togliendo dalla pila qualunque cosa in top ci sia allo stato $f$ di $N'$;

Quindi, **ogni stringa riconosciuta per stato finale da $N$ sicuramente non avrà svuotato la pila** (rimane $Z$ di $N$) e **sarà costretto ad andare con una transizione-$\epsilon$ su $f$ dove verranno rimossi tutti gli eventuali simboli rimanenti aggiunti da $N$ e infine il simbolo iniziale di $N'$ $Z$**.

<u>Nota bene</u>: viene aggiunto $Z$ come fondo della pila di $N$ _per evitare che una transizione di $N$ possa consumare tutti i simboli sulla pila_ (riconoscendo una stringa magari non appartenente al linguaggio). Solo lo stato $f$ di $N'$ deve consumare tutti i simboli sulla pila.

**Qed**.

## Referenze
- [[Linguaggio libero]]