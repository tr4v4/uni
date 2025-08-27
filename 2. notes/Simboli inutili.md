---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 25-08-2025 19:15:32
links:
  - "[[Lecture 05112024110833]]"
---
# Simboli inutili
---
## Introduzione
### Generatore
> Un simbolo $x \in T \cup NT$ e' detto **generatore** $\iff \exists w \in T^{*} : x \implies^{*} w$.

Induttivamente calcoliamo i generatori come:
- $G_{0}(G) = T$
- $G_{i+1}(G) = G_{i}(G) \cup \{B \in NT | B \to C_{1} \cdots C_{k} \in R \land C_{1}, \cdots, C_{k} \in G_{i}(G)\}$

<u>Nota bene</u>: il caso $k = 0$ implica nel passo induttivo che la produzione $B \to \epsilon \in R$ pone $B$ tra i generatori (che e' corretto!).

Anche in questo caso esistera' un $i_{C}$ tale che
$$G_{i_{C}}(G) = G_{i_{C}+1}(G)$$
perche' $T \cup NT$ e' finito. A questo punto l'insieme $G(G) = G_{i_{C}}(G)$ e' l'**insieme di tutti i simboli generatori di $G$**.

### Raggiungibile
> Un simbolo $x \in T \cup NT$ e' detto **raggiungibile** $\iff S \implies^{*} \alpha x \beta$ per qualche $\alpha, \beta \in (T \cup NT)^{*}$.

Induttivamente calcoliamo i raggiungibili come:
- $R_{0}(G) = \{S\}$
- $R_{i+1}(G) = R_{i}(G) \cup \{X_{1}, \cdots, X_{k} | B \to X_{1} \cdots X_{k} \in R \land B \in R_{i}(G)\}$

Anche in questo caso esistera' un $i_{C}$ tale che
$$R_{i_{C}}(G) = R_{i_{C}+1}(G)$$
perche' $T \cup NT$ e' finito. A questo punto l'insieme $R(G) = R_{i_{C}}(G)$ e' l'**insieme di tutti i simboli raggiungibili di $G$**.

### Simbolo inutile
> Un simbolo e' detto **inutile** _se non e' generatore o se non e' raggiungibile_.

Possono creare cicli
$$A \implies^{+} A$$
e per questo si vogliono eliminare.

#### Esempio
Consideriamo la grammatica
$$S \to AB|a \ \ \ \ \ B \to b$$
Allora i simboli generatori sono solo $\{S, B, a, b\}$, poiche'
- $S \implies^{*} a$
- $B \implies^{*} b$
- $a \implies^{*} a$
- $b \implies^{*} b$

Manca $A$ all'appello! **$A$ non e' un generatore**, allora possiamo togliere tutte le produzioni che la coinvolgono:
$$S \to a \ \ \ \ \ B \to b$$

A questo punto notiamo che **$B$ non e' piu' un simbolo raggiungibile**, allora possiamo togliere anche lui e le sue produzioni:
$$S \to a$$

La grammatica ricavata e' assolutamente equivalente alla prima ma senza simboli inutili.

## Eliminazione
### Algoritmo
L'algoritmo per l'eliminazione dei simboli inutili si struttura nei 2 seguenti passi:
1. prima **elimino tutti i non-generatori** e tutte le produzioni che usano almeno uno di questi;
2. poi **elimino tutti i non-raggiungibili** e tutte le produzioni che li usano.

Formalmente sia $G = (NT, T, S, R)$ una grammatica libera tale che $L(G) \neq \varnothing$. Allora:
1. sia $G_{1}$ la grammatica ottenuta da $G$ eliminando tutti i simboli che non appartengono a $G(G)$, e tutte le produzioni che fanno uso di almeno uno di tali simboli;
2. sia $G_{2}$ la grammatica che si ottiene da $G_{1}$ eliminando tutti i simboli che non appartengono a $R(G_{1})$, e tutte le produzioni che fanno uso di almeno uno di tali simboli;

allora $G_{2}$ non ha simboli inutili e $L(G_{2}) = L(G)$.

#### Dimostrazione
Dobbiamo dimostrare la doppia inclusivita':
$$L(G_{2}) \subseteq L(G) \ \ \ \land \ \ \ L(G) \subseteq L(G_{2})$$

$L(G_{2}) \subseteq L(G)$: ovvio, perche' $G_{2}$ contiene meno produzioni di $G$.

$L(G) \subseteq L(G_{2})$: dimostriamo quindi che se $S \implies^{*}_{G} w$ allora $S \implies^{*}_{G_{2}} w$. Notiamo che ogni simbolo usato nella derivazione $S \implies^{*}_{G} w$ sara' per forza sia raggiungibile sia generatore, allora quella derivazione lo sara' anche per $G_{2}$.

**Qed**.

#### Ordine
E' fondamentale notare che **l'ordine dei 2 passi dell'eliminazione e' importante**!
1. prima elimino i non-generatori;
2. poi elimino i non-raggiungibili.

Se invertissi l'ordine, potrebbe capitare di non eliminare tutti i simboli inutili.

Prendendo la grammatica usata nell'esempio
$$S \to AB|a \ \ \ \ \ B \to b$$

Se prima elimino i non raggiungibili ottengo la stessa grammatica; quindi, eliminando i non generatori mi ritrovo con
$$S \to a \ \ \ \ \ B \to b$$
con $B$ simbolo non raggiungibile, e quindi inutile!

## Referenze