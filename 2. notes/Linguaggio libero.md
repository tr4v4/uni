---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 15-08-2025 17:21:16
links:
  - "[[Lecture 18102024090854]]"
---
# Linguaggio libero
---
## Introduzione
> Un [[Linguaggio formale|linguaggio]] si dice **libero** se è [[Linguaggio generato|generato]] da una [[Grammatiche libere|grammatica libera]].

## Teoremi
### Legame con PDA
> Un linguaggio $L$ è libero $\iff$ è [[Linguaggio accettato|accettato]] da un [[Automa a pila|PDA]] (di solito [[NPDA]]).

#### Dimostrazione
$\implies$: se $L$ è libero, allora $\exists G = (NT, T, R, S)$ grammatica libera tale che $L = L(G)$. Costruiamo il PDA $N = (T, \{q\}, T \cup NT, \delta, q, S, \varnothing)$ dove la **funzione di transizione $\delta$ simula la costruzione di una [[Derivazione canonica sinistra|derivazione canonica sinistra]]**. In altri termini:
$$\delta(q, \epsilon, A) = \{(q, \beta) | A \to \beta \in R\} \ \ \ \forall A \in NT$$
$$\delta(q, a, a) = \{(q, \epsilon)\} \ \ \ \forall a \in T$$

Indi per cui, ogni volta che $N$ ha un nonterminale $A$ in cima alla pila, sceglie _nondeterministicamente_ una produzione per $A$, senza consumare l'input; se invece sulla pila c'è un terminale $a$ e l'input presenta proprio $a$, questi vengono consumati, se invece l'input presenta $b \neq a$ allora ci si blocca, e si fa backtracking provando con un'altra produzione.

A questo punto, si può dimostrare che
$$S \implies^{*} w \iff (q, w, S) \vdash_{N}^{*} (q, \epsilon, \epsilon)$$

dove $\implies^{*}$ è una serie di derivazioni leftmost.

$\impliedby$: molto più complessa, basata su due lemmi:
1. ogni PDA $N$ può essere simulato da un PDA $N'$ con un solo stato (aumentando opportunamente i simboli della pila[^1]);
2. ogni PDA con un solo stato ha un'equivalente grammatica libera, tale che se $(q, B1B2 \ldots Bk) \in \delta(q, a, A)$ con $a \in \Sigma \cup \{\epsilon\}$ nel PDA con un solo stato, allora la grammatica $G$ contiene la produzione $A \to a B1\ldots Bk$;

A quel punto si può dimostrare che
$$S \implies^{*}_{G} w \iff (q, w, S) \vdash_{N}^{*} (q, \epsilon, \epsilon)$$

#### Esempi
##### 1
Supponiamo di voler ottenere il PDA che accetta il linguaggio generato dalla grammatica
$$S \to aSb | \epsilon$$

Lo definiamo nel seguente modo
![[grammatica-libera-a-pda.png]]

tale che:
- $S$ è il simbolo inziale sulla pila;
- il PDA riconosce per pila vuota;

La stringa $ab$, per esempio, produce nella pila del PDA proprio la sua derivazione canonica sinistra:
$$S \implies aSb \implies a\epsilon b \implies ab$$
![[grammatica-libera-a-pda-2.png]]

<u>Nota bene</u>: questo PDA è un [[NPDA]], estremamente non deterministico!

##### 2
In quest'altro caso, abbiamo la grammatica
$$A \to aAa | bAb | \epsilon$$

Il PDA associato sarà l'NPDA
![[grammatica-libera-a-pda-3.png]]

Sulla stringa $abba$, la derivazione canonica sinistra
$$A \implies aAa \implies abAba \implies ab\epsilon ba \implies abba$$
viene implementata nella pila nel seguente modo:
![[grammatica-libera-a-pda-4.png]]

E' fondamentale notare che soprattutto in questo esempio, il grado di nondeterminismo del PDA è altissimo: ci sono _ben 3 transizioni-$\epsilon$ che consumano lo stesso simbolo in cima allo stack_ ($A$). Quindi, **come si fa a capire quale strada prendere per derivare $abba$**?
La risposta, almeno per adesso, sta nel **guardare il prossimo carattere**!
Nell'esempio:
- alla prima derivazione da $A$, scelgo di derivare (scrivere sulla pila) $aAa$ perché il prossimo carattere della stringa è $a$;
- alla terza derivazione, scelgo di derivare $A$ in $bAb$ perché il prossimo carattere della stringa è $b$;

Questa è un anticipazione del [[Look-ahead|look-ahead]].

### Chiusura
I linguaggi liberi sono chiusi per:
1. _unione_
2. _concatenazione_
3. _ripetizione_ (stella di Kleene)

<u>Nota bene</u>: i **linguaggi liberi non sono chiusi per intersezione**! E di conseguenza, essendo chiusi per unione, non sono chiusi neanche per complementazione.

#### Dimostrazione
Fissiamo 2 linguaggi $L_{1}, L_{2}$ e 2 grammatiche libere $G_{1}, G_{2}$ tali che $L_{1} = L(G_{1})$ e $L_{2} = L(G_{2})$.

##### Unione
Il linguaggio $L_{1} \cup L_{2}$ sarà generato dalla grammatica:
$$G = (NT_{1} \cup NT_{2} \cup \{S\}, T_{1} \cup T_{2}, S, R_{1} \cup R_{2} \cup \{S \to S_{1} | S_{2}\})$$

di fatto libera.

**Qed**.

##### Concatenazione
Il linguaggio $L_{1} \cdot L_{2}$ sarà generato dalla grammatica:
$$G = (NT_{1} \cup NT_{2} \cup \{S\}, T_{1} \cup T_{2}, S, R_{1} \cup R_{2} \cup \{S \to S_{1}S_{2}\})$$

**Qed**.

##### Ripetizione
Il linguaggio $(L_{1})^{*}$ sarà generato dalla grammatica:
$$G = (NT_{1} \cup \{S\}, T_{1}, S, R_{1} \cup \{S \to \epsilon | S_{1}S\})$$

**Qed**.

### Rapporto linguaggi regolari
> L'intersezione $L_{1} \cap L_{2}$ di un linguaggio libero $L_{1}$ con un [[Linguaggio regolare|linguaggio regolare]] $L_{2}$ è un linguaggio libero.

#### Dimostrazione
Se $L_{1}$ è libero allora esiste un PDA $N_{1} = (\Sigma, Q_{N_{1}}, \Gamma, \delta_{N_{1}}, q_{N_{1}}, Z, F_{N_{1}})$. Se $L_{2}$ è regolare esiste invece un DFA $N_{2} = (\Sigma, Q_{N_{2}}, \delta_{N_{2}}, q_{N_{2}}, F_{N_{2}})$.

Costruiamo il PDA $N$:
$$N = (\Sigma, Q_{N_{1}} \times Q_{N_{2}}, \Gamma, \delta, (q_{N_{1}}, q_{N_{}2}), Z, F_{N_{1}} \times F_{N_{2}})$$
dove $\delta((q, p), a, X)$ è l'insieme di tutte le coppie $((r, s), \gamma)$ tali che:
- $s = \delta_{N_{2}}(p, a)$;
- $(r, \gamma) \in \delta_{N_{1}}(q, a, X)$;

cioè $N$ segue le mosse di $N_{1}$, tenendo traccia dello stato raggiungo da $N_{2}$.

Quindi, si può dimostrare che
$$(q_{N_{1}}, w, Z) \vdash_{N_{1}}^{*} (q, \epsilon, \gamma) 
\land \hat{\delta}_{N_{2}}(q_{N_{2}}, w) = q'$$
$$\iff$$
$$((q_{N_{1}}, q_{N_{2}}), w, Z) \vdash_{N}^{*} ((q, q'), \epsilon, \gamma)$$

#### Applicazione
Questo teorema è utilissimo. Ci consente di dimostrare quando un linguaggio è libero, intersecandolo con un linguaggio regolare apposito e controllando se il risultante è libero o meno.

Inoltre, si osserva dalle regole di chiusura dei linguaggi regolari che:
- se $L = L_{1} \cap L_{2}$ non è regolare e $L_{2}$ è regolare, allora $L_{1}$ non può essere regolare (per la chiusura sull'intersezione dei regolari);
- se $L = L_{1} \cap L_{2}$ non è libero e $L_{2}$ è regolare, allora $L_{1}$ non può essere libero, altrimenti si falserebbe il teorema;

## Referenze
- [[Pumping theorem]]

[^1]: fondamentalmente questi fungono da stati...