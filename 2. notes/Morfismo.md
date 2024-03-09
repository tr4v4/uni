---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 02-12-2023 14:44:24
links:
  - "[[Lecture 30112023091742]]"
  - "[[Lecture 13122023131453]]"
---
# Morfismo
---
## Introduzione
> Un **morfismo** tra due [[Strutture algebriche|strutture algebriche]] dello stesso tipo è una _[[Funzione matematica|funzione]] che mappa gli elementi della prima in quelli della seconda rispettandone le proprietà e il modo di manipolarle_.
> O formalmente, si dice morfismo tra due strutture algebriche $\mathcal{A}$ e $\mathcal{B}$ una funzione $f: \mathcal{A} \to \mathcal{B}$ t.c.
> 1. per ogni costante $e_\mathcal{A}$ si deve avere $f(e_\mathcal{A}) = e_\mathcal{B}$
> 2. per ogni operazione $\circ_\mathcal{A}$ si deve avere $\forall x_{1}, x_{2}, ..., x_{n}. \ \ f(\circ_\mathcal{A}(x_{1}, x_{2}, ..., x_{n})) = \circ_\mathcal{B}(f(x_{1}), f(x_{2}), ..., f(x_{n}))$

<u>Nota bene</u>: _la prima condizione è una versione speciale della seconda_, in cui la costante è un'operazione $\circ$ 0-aria!

## Tipologie
Il morfismo è **valido e unico per ogni struttura algebrica**, ovvero che le proprietà di tale funzione sono univoche per ogni struttura algebrica presa in considerazione. Si parla infatti di morfismi di [[Magma|magmi]], morfismi di [[Monoide|monoidi]], ecc...

### Left unital magma
Siano $(\mathbb{A}, \circ, a)$ e $(\mathbb{B}, \bullet, b)$ due [[Left unital magma|left unital magma]], un morfismo dal primo al secondo è una funzione $f \in \mathbb{B}^{\mathbb{A}}$[^1] t.c.:
- $f(a) = b$
- $\forall x, y. f(x \circ y) = f(x) \bullet f(y)$

#### Esempio
Considerati i due left unital magma $(\mathbb{N}, +, 0)$ e $(\mathbb{N}, *, 1)$, un esempio di morfismo dal primo al secondo potrebbe essere $f(n) = 2^{n}$, in quanto vengono rispettate le proprietà del morfismo tra left unital magma:
- $2^{0} = 1$
- $\forall x, y. 2^{x+y} = 2^{x} * 2^{y}$

## Importanza
> L'importanza dei morfismi si ritrova nel momento in cui, applicando i principi dell'[[Astrazione|astrazione]], _andiamo a studiare delle proprietà di una struttura algebrica mediante un'altra struttura_.
> Pertanto si ha che $f: \mathcal{A} \to \mathcal{B}$ è un modo per osservare sugli elementi di $\mathbb{A}$ delle proprietà $\mathbb{B}$.

#### Esempio
Prendiamo un insieme $\mathbb{X}$ e una funzione $| \cdot |: \mathcal{P}(\mathbb{X}) \to \mathbb{N}$ chiamata [[Cardinalità|cardinalità]], che associa ad ogni sottoinsieme di $\mathbb{X}$ (con l'[[Assioma dell'insieme potenza|insieme potenza]]) il numero di elementi in esso contenuto.
Quello che abbiamo fatto è astrarre di un insieme generico una sua proprietà.

Questo meccanismo di astrazione è lo stesso introdotto dall'[[Insieme quoziente|insieme quoziente]], ovvero il processo di astrazione di un generico insieme $\mathbb{A}$ rispetto ad una [[Relazione di equivalenza|relazione di equivalenza]] $\equiv$.

La reale astrazione si ottiene però con il [[Teorema fondamentale dei morfismi|teorema fondamentale dei morfismi]].

## Argomenti
- [[Immagine di morfismo]]
- [[Definizione di relazione di equivalenza indotta di un morfismo]]
- [[Definizione di proiezione]]
- [[Teorema fondamentale dei morfismi]]

## Referenze
- [[Isomorfismo]]

[^1]: [[Spazio di funzione|spazio di funzione]]