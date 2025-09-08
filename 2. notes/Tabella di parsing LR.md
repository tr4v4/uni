---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 28-08-2025 19:07:54
links:
---
# Tabella di parsing LR
---
## Introduzione
> Una **tabella di parsing $LR$** e' una matrice bidimensionale usata dai [[Parser LR|parser]] $LR$ per risolvere i conflitti shift-reduce e reduce-reduce. Viene calcolata attraverso il [[DFA dei prefissi viabili]].
> Formalmente e' fatta come:
> - _le righe contengono gli stati dell'automa canonico $LR(0)$/$LR(1)$ (DFA dei prefissi viabili)_;
> - _le colonne sono divise in **azione** ($T \cup \{\$\}$) e in **goto** ($NT$)_.

A questo punto **$M[s, x]$ conterra' le azioni che puo' compiere un parser $LR$ con $s$ in cima alla pila degli stati e $x$ simbolo in input** (o nonterminale nel caso dei _goto_). Nei casi particolari invece:
- se $M[s, x]$ e' "bianca", allora errore;
- se $M[s, x]$ contiene piu' azioni, allora c'e' un conflitto --> il parser non e' deterministico!

## Riempimento
### Caso $LR(0)$
L'algoritmo per calcolare la tabella di parsing nel caso $LR(0)$ a partire dall'automa canonico $LR(0)$ e' il seguente:
- per ogni stato $s$ dell'automa canonico $LR(0)$:
	- se $x \in T$ e $s \to^{x} t$ nell'automa $LR(0)$, inserisci _shift $t$_ in $M[s, x]$;
	- se $A \to \alpha . \in s$ e $A \neq S'$, inserisci _reduce $A \to \alpha$_ in $M[s, x]$ per tutti gli $x \in T \cup \{\$\}$;
	- se $S' \to S. \in s$, inserisci _accept_ in $M[s, \$]$;
	- se $A \in NT$ e $s \to^{A} t$ nell'automa $LR(0)$, inserisci _goto $t$_ in $M[s, A]$;

#### Esempio
Prendiamo sempre la nostra grammatica di riferimento:
1. $S' \to S$
2. $S \to (S)$
3. $S \to A$
4. $A \to a$

e inseriamo ancora il DFA dei prefissi viabili:
![[dfa-prefissi-viabili-2.png]]

Allora la tabella di parsing $LR(0)$ calcolata a partire da questo DFA sara':
![[tabella-parsing-lr0-2.png]]

Ancora non sappiamo formalmente l'algoritmo del parser, ma sulla base della tabella possiamo intuire come funzioni. Prendiamo per esempio l'input $((a))$\$:
![[parser-lr0-esecuzione-1.png]]

Da qui si capisce perfettamente il senso delle colonne di _goto_: quando viene fatta una _reduce_, la produzione sulla pila viene ridotta al nonterminale sulla base delle indicazioni della tabella di parsing; fatto cio', dobbiamo aggiornare lo stato del DFA. **Al posto di fargli riscannerizzare l'intera pila dei simboli (quella del PDA) da capo, possiamo andare allo stato che si trovava prima di entrare nella produzione appena ridotta ($s_{n-r}$ dove $r = |\alpha|$), e da li' fargli leggere il nonterminale appena aggiunto sulla pila dei simboli: lo stato in cui va il DFA, letto dalla colonna _goto_, sara' pushato sul top della pila degli stati, e sara' quindi il nuovo stato del DFA**.

Questo e' il motivo per cui nelle implementazioni reali di parser $LR(0)$ non ci si salva la pila dei simboli, ma solo quella degli stati del DFA: sono sufficienti le colonne del _goto_ per capire da dove far ripartire il DFA!

### Caso $LR(1)$
Ci sono grammatiche libere che potrebbero [[Grammatiche SLR(1)|non essere neanche]] $SLR(1)$! Questo e' ovvio: **e' sufficiente che il carattere di look-ahead appartenga ai [[First e follow|follow]] del nonterminale della produzione di cui si puo' fare shift o reduce**.

Si capisce pero' che _e' comunque possibile risolvere i conflitti shift-reduce di grammatiche non $SLR(1)$ semplicemente riducendo i casi in cui e' possibile fare una reduce sulla base di alcune valutazioni sulla grammatica_.

Intuitivamente, l'**idea e' di associare a ogni item di uno stato dell'automa canonico $LR(0)$ un carattere di look-ahead per determinarne la scelta**.

Quindi e' sufficiente definire:
- _item $LR(1)$_;
- _automa canonico $LR(1)$_;

#### Costruzione
Definito l'automa canonico $LR(1)$, si costruisce la tabella di parsing $LR(1)$ come segue:
- per ogni stato $s$ dell'automa canonico $LR(1)$:
	- se $x \in T$ e $s \to^{x} t$ nell'automa $LR(1)$, inserisci _shift $t$_ in $M[s, x]$;
	- se $[A \to \alpha ., x] \in s$ e $A \neq S'$, inserisci _reduce $A \to \alpha$_ in $M[s, x]$ per tutti gli $x$ del [[Look-ahead|look-ahead]];
	- se $S' \to S. \in s$, inserisci _accept_ in $M[s, \$]$;
	- se $A \in NT$ e $s \to^{A} t$ nell'automa $LR(1)$, inserisci _goto $t$_ in $M[s, A]$;

Ovviamente ogni casella rimasta vuota e' un errore.

La regola della reduce e' ovviamente quella fondamentale: sto dicendo che posso fare la reduce solo se in lettura ho un carattere $x$ che appartiene **in quella reale derivazione** al first di cio' che si trova dopo $A$, ossia al suo follow "reale".

Questo differisce sostanzialmente con i follow calcolati dalle tabelle $SLR(1)$: infatti _in quel caso ($SLR(1)$) stiamo calcolando in generale i follow di $A$, e non quelli che si possono solamente trovare a partire da quello stato_!

### Ricapitolo
![[riempimento-tabelle-parsing-ricapitolo.png]]

E _per $LALR(1)$ si prende la tabella $LR(1)$ e si fondono gli stati con lo stesso nucleo $LR(0)$_.

## Referenze
- [[Grammatiche LR(0)]]
- [[Tabella di parsing SLR(1)]]
- [[Tabella di parsing LALR(1)]]