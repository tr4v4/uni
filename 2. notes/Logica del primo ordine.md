---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 20-11-2023 20:18:59
links:
  - "[[Lecture 15112023130429]]"
---
# Logica del primo ordine
---
## Introduzione
La **logica del primo ordine** è la diretta conseguenza dei limiti espressivi di quella [[Logica proposizionale|proposizionale]]. Quest'ultima, infatti, come già visto _associa ad ogni connotazione solo ed esclusivamente un valore di verità_. Ma se volessimo per esempio analizzare da un punto di vista logico la frase
$$\text{se } x^{2} \text{ è maggiore di 2, allora } x^{2} \text{ è maggiore di 4}$$
la logica proposizionale non avrebbe abbastanza strumenti [[Sintassi|sintattici]] per costruirla: sarebbe tradotta in una [[Implicazione|implicazione]] $A \implies B$, che però non coglie il senso della frase.

In poche parole, quindi, per descrivere la matematica è necessaria **una logica più fine**, ricca, che vada oltre al valore di verità delle proposizioni.

## Sintassi
La sintassi della logica del prim'ordine si compone di:
- **formule**/**proposizioni**: connotazioni che denotano valore di verità (esattamente come in logica proposizionale)
- **termini**: connotazioni che denotano _elementi del dominio del discorso_, ovvero i singoli oggetti del discorso (che non assumono un valore di verità)

### Proposizioni
$$P ::= P^{n}(t_{1}, t_{2}, t_{3}, ... t_{n}) | \bot | \top | P \land P | P \lor P | P \implies P | \forall x . P | \exists x . P$$
dove:
- $P^{n}(t_{1}, t_{2}, t_{3}, ... t_{n})$ sono _predicati_ $n$-ari composti da termini $t$
- $\forall$ e $\exists$ sono i [[Quantificatori|quantificatori]], rispettivamente _universale_ ed _esistenziale_

### Termini
$$t ::= x | c | f^{n}(t_{1}, t_{2}, t_{3}, ..., t_{n})$$
dove:
- $x$ sono le _variabili_, di un'infinità [[Numerabilità|numerabile]]
- $c$ sono le _costanti_
- $f^{n}(t_{1}, t_{2}, t_{3}, ..., t_{n})$ sono _funzioni_ $n$-arie composte da termini $t$ (esempio "somma", o "padre di")

### Differenze
La differenza fondamentale tra funzioni $f^{n}$ e predicati $P^{n}$ è che:
- la funzione _prende elementi del discorso $t$ e restituisce un elemento del discorso $t$_
- un predicato _prende elementi del discorso $t$ e restituisce un valore di verità_

### Osservazioni
Il nome logica _del primo ordine_ fa presupporre che esista la logica del secondo ordine, terz'ordine ecc... Il motivo per cui si chiama così è perché delle proposizioni $\forall x . P$ e $\exists x . P$, _le variabili $x$ possono essere solo elementi del dominio del discorso $A$, e non funzioni o predicati_.
Per esempio:
- $\forall x . x > 4$ --> logica del primo ordine
- $\forall f . f(x) > 4$ --> NON logica del primo ordine
- $\forall P . P(x) > 4$ --> NON logica del primo ordine

<u>Attenzione</u>: **tutta la matematica si può ottenere dalla logica del primo ordine**, infatti attenzione a _confondere le funzioni matematiche da quelle logiche_ (abuso di notazione).

Ciò risuona male, dal momento che in matematica non è scorretto considerare un gruppo di funzioni t.c. $\forall f. f(x) > 4$. Ma le funzioni intese in matematica sono quelle descritte a partire da [[ZF]], ovvero una [[Relazione|relazione]] per cui [[Funzione matematica|ogni elemento del dominio è associato a uno e un solo elemento del codominio]]. Di fatto, una funzione matematica, in quanto relazione, è un [[Definizione di essere sottoinsieme|sottoinsieme]] del [[Prodotto cartesiano|prodotto cartesiano]], e quindi a sua volta un insieme: _un termine del dominio del discorso_! Una funzione logica, invece, è un'espressione che presi termini $t$ ritorna termini $t$.

<u>Nota bene</u>: sembra mancare, nella sintassi della logica del prim'ordine, la serie di variabili $A, B, C, ...$ tipiche della logica proposizionale, che assumevano per ogni mondo $v$ un significato. Ebbene, esse, qui, sono inglobate nei predicati $P^{0}$ (_0-ari_), ovvero in quei _predicati che non prendono alcun termine in ingresso, ma che assumono indipendentemente un valore di verità_.

## Semantica
In logica del prim'ordine, _a seconda del mondo $v$, non solo i predicati ma anche i termini assumono un significato_ (una semantica), _differente_. Quando scegliamo un mondo $v$ fissiamo anche l'insieme del dominio del discorso $A$, e assegna:
- _a ogni simbolo di costante $c$ un elemento di $A$_
	- per esempio $[[\pi]]^{v} = 2$
	- quindi stiamo dicendo che nel mondo $v$ la semantica della costante $\pi$ è 2
- _a ogni simbolo di funzione $n$-aria $f^{n}$ una funzione $n$-aria su $A$_
	- per esempio $[[+]]^{v} = *$
	- quindi stiamo dicendo che nel mondo $v$ la semantica della funzione $+$ è la moltiplicazione ($*$)
- _a ogni simbolo di predicato $n$-ario $P^{n}$ un predicato $n$-ario su $A$_
	- per esempio $[[>]]^{v} = |$ (dividere)
	- quindi stiamo dicendo che nel mondo $v$ la semantica del predicato $>$ è "divide" ($|$)

Da questo ne deriva la seguente osservazione: **la matematica è completamente ipotetica**. Il senso delle costanti, delle funzioni e dei predicati è solo il senso che viene assegnato loro dal mondo $v$ nel dominio del discorso $A$.

### Definizione
La definizione di semantica classica della logica del prim'ordine non è tanto differente da [[Semantica classica#Definizione|quella della proposizionale]]: sono solo aggiunti i quantificatori. Una definizione **tarksiana** sarebbe:
- $[[\forall x . F]]^{v}$ sse la semantica di $F$ nel mondo $v$ è sempre 1 al variare della semantica di $x$ su tutti gli elementi di $A$
	- ovvero, se $x$ scorre tra tutti gli elementi del dominio del discorso di $A$, il risultato di $F$ in un certo mondo $v$ è sempre 1
- $[[\exists x . F]]^{v}$ sse la semantica di $F$ nel mondo $v$ è almeno una volta 1 al variare della semantica di $x$ su tutti gli elementi di $A$
	- ovvero, se $x$ scorre tra tutti gli elementi del dominio del discorso di $A$, il risultato di $F$ in un certo mondo $v$ è almeno una volta 1

## Referenze