---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 07-09-2025 20:12:27
links:
---
# Tabella di parsing LALR(1)
---
## Introduzione
Notiamo che _il nucleo di uno stato $LR(1)$_ (ossia l'insieme dei nuclei dei singoli item $LR(1)$), _corrisponde esattamente a uno stato dell'automa $LR(0)$_. Inoltre, le transizioni dell'automa $LR(1)$ dipendono solamente dal suo nucleo, e non dal carattere di [[Look-ahead|look-ahead]].

A questo punto definiamo la tabella di parsing $LALR(1)$ in questo modo:
> La **tabella di parsing $LALR(1)$** si ottiene da [[Tabella di parsing LR|quella]] $LR(1)$ _fondendo insieme gli stati con lo stesso nucleo_.

In questo modo infatti essa conterra':
- tante righe quanti gli stati dell'automa $LR(0)$ ([[DFA dei prefissi viabili]]);
- meno _reduce_ della [[Tabella di parsing SLR(1)|tabella]] $SLR(1)$.

### Esempio
Prendiamo in esame la grammatica
0. $S' \to S$
1. $S \to CC$
2. $C \to cC$
3. $C \to d$

che produceva la tabella di parsing $LR(1)$:
![[tabella-parsing-lr1-1.png]]

Notavamo dal'automa canonico $LR(1)$
![[automa-canonico-lr1-1.png]]

che gli stati $(I_{3}, I_{6})$, $(I_{4}, I_{7})$, $(I_{8}, I_{9})$ _possono essere fusi_! Nell'automa canonico $LR(0)$ infatti ogni coppia costituirebbe un unico stato:
![[automa-canonico-lr0-per-lr1.jpg]]

A questo punto la tabella di parsing $LALR(1)$ sarebbe:
![[tabella-parsing-lalr1-1.png]]

Si ha quindi, per esempio:
$$I_{36} = I_{3} \cup I_{6} = \{[C \to c.C, c/d/\$], [C \to .cC, c/d/\$], [C \to .d, c/d/\$]\}$$

### Comportamento
In generale vale che se $G$ e' $LR(1)$ e anche $LALR(1)$, allora **gli automi corrispondenti si mimano perfettamente su input corretti**.

Invece, **su input errati, $LALR(1)$ puo' fare qualche riduzione in piu' prima di accorgersi dell'errore**.

Inoltre, **l'automa $LALR(1)$ non fara' mai degli _shift_ in piu' dell'automa $LR(1)$ per un certo input**. Di conseguenza i due parser consumano la stessa porzione di input prima di rilevare l'errore, e quindi $LALR(1)$ e' un perfetto sostituto di $LR(1)$.

## Passaggio
### Nuovi conflitti
Quello che ci si domanda, pero', e' se **la fusione degli stati del parser $LR(1)$ non porti a nuovi conflitti nel parser $LALR(1)$**... e la risposta e' **si'**, ma **solo conflitti reduce-reduce**!

#### Dimostrazione
Supponiamo per assurdo che nello stato $s$ del parser $LALR(1)$ ottenuto fondendo due stati $s_{1}, s_{2}$ del parser $LR(1)$, presenti un _conflitto shift-reduce_. Allora, esiste in $s$ un item $[A \to \alpha., a]$ e uno $[B \to \beta . a \gamma, b]$. Supponiamo che $[A \to \alpha., a] \in s_{1}$. Allora anche $[B \to \beta.a \gamma, c] \in s_{1}$ per qualche $c$. Ma questo significherebbe che anche in $s_{1}$ c'e' un conflitto shift-reduce, contro l'ipotesi che la tabella $LR(1)$ non presenti conflitti.

**Qed**.

Di conseguenza, **se $LR(1)$ e' senza conflitti, allora $LALR(1)$ puo' solo presentare conflitti reduce-reduce**. In tal caso, $G$ e' $LR(1)$ ma non $LALR(1)$.

## Costruzione
Teoricamente si puo' costruire la tabella di parsing $LALR(1)$ a partire da quella $LR(1)$ attraverso le fusioni descritte in precedenza... _ma questo richiederebbe di dover prima costruire la tabella di parsing $LR(1)$_: troppo dispendioso!

Di fatto **e' possibile costruire $LALR(1)$ direttamente dall'automa $LR(0)$**! Questa tecnica e' quella usata da [[YACC]].

## Referenze