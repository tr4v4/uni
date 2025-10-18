---
tags:
  - category/note
  - status/finished
  - topic/algoritmi-e-strutture-dati
date: 05-04-2024 17:21:57
links:
  - "[[Lecture 03042024130843]]"
  - "[[Lecture 04042024091934]]"
---
# Struttura union-find
---
## Introduzione
> Una **struttura union-find** è una _[[Struttura dati|struttura dati]] usata per gestire e rappresentare [[Insieme|insiemi]] disgiunti_, ovvero la cui [[Definizione di intersezione|intersezione]] è l'[[Definizione di insieme vuoto|insieme vuoto]] $\varnothing$. Sono composti da una collezione $S$ di $k$ elementi, del tipo
> $$S = \{s_{1}, \cdots, s_{k}\}$$
> dove $s_{1}, \cdots, s_{k}$ sono appunto insiemi disgiunti. Complessivamente il numero di elementi $n$ in $S$ è sempre maggiore uguale al numero di insiemi $k$, ovvero
> $$n \geq k$$
> e questo significa che almeno ogni insieme deve avere un elemento. Infatti la _configurazione iniziale è proprio di $k$ [[Assioma del singoletto|singoletti]]_. Ogni insieme è rappresentato da un _rappresentante univoco_, scelto tra gli elementi dell'insieme. Tutti gli elementi degli insiemi di $S$ devono essere diversi: questo _romperebbe la proprietà di disgiunzione_.

## Operazioni
Le operazioni esposte da una struttura union-find sono: `makeSet`, `union` e `find`.

### `makeSet(Elem x)`
Crea un insieme il cui unico elemento e rappresentante è `x`, ovvero il singoletto di `x`
$$\{x\}$$

<u>Attenzione</u>: _`x` non deve appartenere a un altro insieme esistente_.

### `union(Set x, Set y)`
Unisce i due insiemi i cui rappresentanti sono `x` e `y`, creando un nuovo insieme cui rappresentante di solito è `x` ed eliminando i due insiemi vecchi.

<u>Nota bene</u>: l'_unione non rompe la proprietà di disgiunzione_!

### `find(Elem x)`
Restituisce il rappresentante dell'unico insieme contenente `x`.

## Applicazioni
Queste strutture sono particolarmente usate quando si vuole _sapere di un certo sistema composto da percorsi tra nodi se due nodi sono collegati_. Infatti una volta che le operazioni di `makeSet` e `union` hanno composto lo stato di tale sistema, per sapere se due nodi sono connessi **basta richiamare `find` su entrambi e vedere se esce lo stesso nodo rappresentante**.

<u>Nota bene</u>: questa struttura consente di conoscere _se esiste un percorso che lega due nodi, ma non quale_[^1].

## Implementazioni
Ci sono due implementazioni elementari:
- [[Quick find]]
- [[Quick union]]

e poi le loro versioni migliorate basate su _euristiche di bilanciamento_.

## Referenze
- c'è un [[Isomorfismo|isomorfismo]] tra le strutture union-find e le [[Relazione di equivalenza|relazioni di equivalenza]]. Preso infatti un elemento `x`, si ha che: `x` è nello stesso insieme in cui si trova `x` (_riflessività_); se `x` è nello stesso insieme di `y` allora anche `y` è nello stesso insieme di `x` (_simmetria_); se `x` è nello stesso insieme di `y`, e `y` è nello stesso insieme di `z`, allora anche `x` sarà nello stesso insieme di `z` (_transitività_);

[^1]: è lo stesso rapporto che c'è tra la [[Logica classica|logica classica]] e la [[Logica intuizionista|logica intuizionista]]