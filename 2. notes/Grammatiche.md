---
tags:
  - category/note
  - status/ongoing
  - topic/linguaggi-di-programmazione
date: 29-09-2024 21:30:03
links:
  - "[[Lecture 24092024110820]]"
---
# Grammatiche
---
## Introduzione
Il ruolo delle grammatiche è quello di rispondere alle due domande fondamentali sulla [[Rappresentazione finita di un linguaggio|rappresentazione]] dei [[Linguaggio formale|linguaggi]]:
- _come rappresentare finitamente un linguaggio?_
- _come verificare l'appartenenza di una stringa a un linguaggio?_

Cominciamo con degli esempi

### Palindrome
Prendiamo l'alfabeto $A = \{a, b\}$, e su di esso definiamo il linguaggio $L \subseteq A^{*}$ come l'insieme di tutte le palindrome su $A$:
$$L = \{\epsilon, a, b, aa, bb, aba, bab, aaa, bbb, abba, baab, aaaa, bbbb, \cdots\}$$

Notiamo che per rappresentare le palindrome, e quindi $L$, in modo finito su questo alfabeto, ci basta semplicemente definire i casi in cui una stringa è palindroma:
- $\epsilon$
- $a$
- $b$
- $a$-palindroma-$a$
- $b$-palindroma-$b$

Qualunque palindroma a partire da $A$ è generabile secondo questo schema: **questa è la grammatica**.

Ora, esistono diverse notazioni per rappresentarla:
- _[[Backus-Naur Form]]_: $<P> ::= \epsilon | a | b | a <P> a | b <P> b$
- _grammatica_ (notazione standard): $P \to \epsilon | a | b | aPa | bPb$
- _[[Assioma|assiomi]] e [[Regole di inferenza|regole di inferenza]]_
	- _assiomi_: $\epsilon \in L(P)$, $a \in L(P)$, $b \in L(P)$
	- _regole di inferenza_: $w \in L(P) \implies awa \in L(P)$, $w \in L(P) \implies bwb \in L(P)$

Una volta definita la grammatica delle palindrome, come dimostriamo che $abba \in L(P)$? Si fa in un processo detto di **derivazione** delle stringhe: si deriva $abba$ a partire dalla generica $P$.
$$P \implies aPa \implies abPba \implies abba$$

Da un punto di vista assiomatico, si applica ad ogni passaggio una regola di inferenza che consente di costruire la stringa ricercata. In questo caso sono rispettivamente:
1. $P \to aPa$
2. $P \to bPb$
3. $P \to \epsilon$

<u>Nota bene</u>: si tratta a tutti gli effetti di **[[Albero di deduzione naturale|alberi di deduzione naturale]] costruiti dall'alto verso il basso**, ossia dagli assiomi alla tesi da dimostrare.

### Espressioni aritmetiche
Allo stesso modo possiamo rappresentare in modo finito il linguaggio che contiene tutte le espressioni aritmetiche formate da variabili $a$ e $b$, dagli operatori $*$ e $+$ e dalle parentesi $()$, usando la grammatica.

In notazione (esclusa quella assiomatica):
- _BNF_: $<E> ::= a|b|<E>*<E>|<E>+<E>|(<E>)$
- _grammatica_: $E \to a|b|E*E|E+E|(E)$

Anche in questo caso, vogliamo dimostrare $a+(a*b) \in L(E)$. Deriviamolo:
$$E \implies E+E \implies a+E \implies a+(E) \implies a+(E*E) \implies a+(a*E) \implies a+(a*b)$$

## Definizione


## Referenze