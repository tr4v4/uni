---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 19-08-2025 17:07:08
links:
  - "[[Lecture 24102024120228]]"
---
# Parser bottom-up
---
## Introduzione
Definita una [[Grammatiche libere|grammatica libera]] $G = (NT, T, S, R)$, costruiamo il [[Automa a pila|PDA]] $M$ che riconosce $L(G)$\$ come $M = (T, \{q\}, T \cup NT \cup \{\$\}, \delta, q, Z, \varnothing)$ dove:
1. $(q, aX) \in \delta(q, a, X) \ \ \ \forall a \in T. \forall X \in T \cup NT \cup \{\$\}$ - **shift**, ossia consumo il carattere letto e lo metto sulla pila;
2. $(q, A) \in \delta(q, \epsilon, \alpha^{R})$ se $A \to \alpha \in R$ - **reduce**, ossia se ho sulla pila una produzione al contrario, allora la elimino tutta[^1] e al suo posto ci metto il nonterminale da cui parte;
3. $(q, \epsilon) \in \delta(q, \$, S\$)$ - **accept**, ossia se mi ritrovo a leggere il carattere di fine stringa (\$) e sulla pila ho il simbolo iniziale della grammatica seguito dal simbolo iniziale della pila, allora vuol dire che sono riuscito ad accettare la stringa.

Prendiamo in esempio la grammatica $G$:
$$S \to aSb | ab$$
Il parser bottom-up costruito secondo le specifiche è il seguente:
![[parser-bottom-up-1.png]]

Sull'input $aabb$\$, il funzionamento è il seguente:
![[parser-bottom-up-2.png]]

La _[[Derivazione canonica destra|derivazione canonica destra]] a rovescio_ è quindi la seguente
$$aabb \impliedby aSb \impliedby S$$
da cui è facilmente ottenibile l'[[Albero di derivazione|albero di derivazione]].

Le grammatiche $LR(k)$ allora sono quelle cui linguaggio generato è riconoscibile da un parser bottom-up deterministico usando $k$ simboli di [[Look-ahead|look-ahead]].

Nella maggior parte dei casi, i parser risultanti sono _estremamente nondeterministici_. In particolare ci sono:
- **conflitti shift-reduce** --> quando potresti fare sia shift che reduce;
	- nell'esempio al passo 3 potrei fare shift, andando a ottenere nello stack $Zaabb$ e come input solo \$;
	- la strada è infruttuosa!
- **conflitti reduce-reduce** --> quando potresti fare più reduce;
	- nell'esempio non ci sono conflitti del genere;
	- _questi avvengono quando hai produzioni uguali o che condividono lo stesso prefisso per nonterminali diversi_ --> devi scegliere quale nonterminale scrivere sulla pila!

Di conseguenza, per ottenere un DPDA, è necessario introdurre informazioni aggiuntive per risolvere i conflitti:
- _più stati_ --> [[DFA dei prefissi viabili]];
- _look-ahead_.

Con un esempio complesso si capisce che **è buona norma scegliere in modo tale che ciò che si trova sulla pila sia un prefisso (a rovescio) di una parte destra di una produzione della grammatica**.

<u>Nota bene</u>: c'è anche un altro problema, le produzioni-$\epsilon$! Una grammatica che contiene la produzione $S \to \epsilon$ sarebbe tradotta da un parser bottom-up in una transizione del tipo
![[parser-bottom-up-3.png]]
che è una _reduce sempre applicabile_! Quindi bisogna stare attenti e cercare di evitare di usare produzioni del genere quando si vuole usare la tecnica di bottom-up parsing.

## Costruzione
### Deterministicizzazione
La strategia per risolvere i conflitti shift-reduce e reduce-reduce, e quindi il nondeterminismo, dei parser bottom-up, consiste nel **scegliere l'azione giusta in modo che sulla pila ci sia un [[Prefisso viabile|prefisso viabile]]**.

Quindi, in altre parole, dovremo fornire al PDA una struttura di controllo (_tabella di parsing_) che lo aiuti a scegliere l'azione giusta.

### Tipologie
I parser bottom-up possono essere:
- [[Parser LR|parser LR]];
- [[Parser LALR|parser LALR]]

## Referenze

[^1]: è una generalizzazione dei PDA in cui consumo dalla pila non solo il top ma un'intera stringa;
