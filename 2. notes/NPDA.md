---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 28-10-2024 18:32:54
links:
  - "[[Lecture 17102024120438]]"
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
<u>Osservazione</u>: spesso si ha che per un DPDA $N$ $$L[N] \neq P[N]$$
Ma dimostreremo che
$$L = L[N] \implies \exists N' : L = P[N']$$
e viceversa che
$$L = P[N] \implies \exists N' : L = L[N']$$

ossia che **la classe dei linguaggi riconosciuti da PDA per stato finale o per pila vuota è la stessa**.

## Referenze