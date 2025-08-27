---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 07-10-2024 22:10:59
links:
  - "[[Lecture 03102024120247]]"
  - "[[Lecture 15102024110302]]"
  - "[[Lecture 17102024120438]]"
---
# Linguaggio regolare
---
## Introduzione
> Un [[Linguaggio formale|linguaggio]] $L \subseteq A^{*}$ (su alfabeto $A$) è detto **regolare** $\iff$ $\exists$ una [[Espressione regolare|espressione regolare]] $r$ tale che $L$ sia un [[Linguaggio denotato da un'espressione regolare|linguaggio denotato]] da $r$, ossia
> $$L = \mathscr{L}[r]$$

### Esempi
Fissato l'alfabeto $A = \{0, 1\}$, definiamo delle espressioni regolari e i linguaggi regolari ad essi associati:
- $0^{*}10^{*}$ è $L = \{w \in A^{*} | w \text{ contiene un solo 1}\}$
- $(0|1)^{*}1(0|1)^{*}$ è $L = \{w \in A^{*} | w \text{ contiene almeno un 1}\}$
- $(0|1)^{*}001(0|1)^{*}$ è $L = \{w \in A^{*} | w \text{ contiene 001 come sottostringa}\}$
- $1^{*}(011^{*})^{*}$ è $L = \{w \in A^{*} | \text{ogni occorrenza di 0 è seguita immediatamente da almeno un 1}\}$
- $((0|1)\cdot(0|1))^{*}$ è $L = \{w \in A^{*} | w \text{ è di lunghezza pari}\}$
- $(0|1)^{*}1$ è $L = \{w \in A^{*} | w \text{ termina con un 1}\}$

## Proprietà
### Finitezza
> _Ogni linguaggio finito è regolare_.

Si prenda come esempio l'espressione regolare $r=a/bc$, e dimostro che $\mathscr{L}[r]=L$ con $L$ linguaggio finito:
$$\mathscr{L}[a/bc] = \mathscr{L}[a] \cup \mathscr{L}[bc] = \{a\} \cup \mathscr{L}[b]\cdot\mathscr{L}[c] = \{a\} \cup \{b\} \cdot \{c\} = \{a\} \cup \{bc\} = \{a, bc\}$$

<u>Nota bene</u>: esistono comunque linguaggi regolari infiniti, come $\mathscr{L}[a^{*}b] = \{a^{n}b | n \geq 0\}$ o $\mathscr{L}[a/a^{*}b] = \{a\} \cup \{a^{n}b | n \geq 0\}$.

### Non-regolarità
Esiste una proprietà [[Algoritmo|algoritmica]] fondamentale dei linguaggi regolari. Così importante che è ciò che contraddistingue i linguaggi regolari da quelli non regolari.
Di fatto sappiamo che le [[Grammatiche regolari|grammatiche regolari]] sono un [[Definizione di essere sottoinsieme|sottoinsieme]] delle [[Grammatiche libere|grammatiche libere]], e di conseguenza anche i linguaggi regolari sono un sottoinsieme dei [[Linguaggio libero|linguaggi liberi]].
![[linguaggi-liberi-e-regolari.png]]

Come facciamo a identificare un linguaggio non-regolare? Sfruttiamo questa proprietà, che prende il nome di [[Pumping lemma|pumping lemma]].

### Chiusura
La classe dei linguaggi regolari è chiusa per:
1. _unione_
2. _concatenazione_
3. _ripetizione_ (stella di kleene)
4. _complementazione_
5. _intersezione_

#### Dimostrazione
I primi 3 punti sono ovvi: se $L_{1}, L_{2}$ sono due linguaggi regolari, allora esistono due espressioni regolari $s_{1}, s_{2}$ tali che
$$L_{1} = \mathscr{L}[s_{1}] \ \ \ \ \ L_{2} = \mathscr{L}[s_{2}]$$

Dalle proprietà del linguaggio denotato ho che
$$\mathscr{L}[s_{1}] \cup \mathscr{L}[s_{2}] = \mathscr{L}[s_{1}/s_{2}]$$
$$\mathscr{L}[s_{1}] \cdot \mathscr{L}[s_{2}] = \mathscr{L}[s_{1} \cdot s_{2}]$$
$$(\mathscr{L}[s_{1}])^{*} = \mathscr{L}[(s_{1})^{*}]$$

La complementazione si dimostra introducendo un DFA $M$ che riconosca $L_{1}$ e costruendo il DFA $\bar{M}$ che riconosca il suo complementare. E' facile: se $M = (\Sigma, Q, \delta, q_{0}, F)$, allora $\bar{M} = (\Sigma, Q, \delta, q_{0}, Q \setminus F)$, ossia _basta avere come stati finali di $\bar{M}$ gli stati non finali di $M$_. Infatti vale che $w \in L[M] \iff w \notin L[\bar{M}]$, e quindi che
$$L[\bar{M}] = \Sigma^{*} \setminus L[M]$$

L'intersezione è una diretta conseguenza delle [[Leggi di De Morgan|leggi di De Morgan]]. Se abbiamo l'unione e la complementazione, allora ricaviamo l'intersezione:
$$L_{1} \cap L_{2} = \overline{\overline{L_{1}} \cup \overline{L_{2}}}$$

<u>Nota bene</u>: si può dimostrare anche usando i DFA.

#### Utilità
La chiusura per intersezione può essere utile per dimostrare che un linguaggio non è regolare: preso $L$ il linguaggio da analizzare, definisco un $L_{reg}$ linguaggio regolare e ho
$$L \cap L_{reg} = L_{non-reg} \implies L \text{ non è regolare}$$

Per esempio considero il linguaggio
$$L = \{w \in \{a, b\}^{*} | w \text{ contiene tante a quante b}\}$$
Se lo interseco con il linguaggio denotato da $a^{*}b^{*}$, ottengo
$$L \cap \mathscr{L}[a^{*}b^{*}] = \{a^{n}b^{n} | n \geq 0\}$$
che già sappiamo non essere regolare[^1].

### Proprietà algoritmiche
Nei linguaggi regolari si possono verificare automaticamente le seguenti proprietà:
1.  $w \in L[M]$? basta leggere $w$ e vedere se si è finiti in uno stato finale (in tempo lineare);
2. $L[M] = \varnothing$? equivale a chiedersi l'esistenza di un cammino aciclico dallo stato iniziale ad uno finale;
3. $L[M] = A^{*} \iff L[\bar{M}] = \varnothing$
4. $L[M_{1}] \subseteq L[M_{2}] \iff L[\bar{M_{2}}] \cap L[M_{1}] = \varnothing$
5. $L[M_{1}] = L[M_{2}] \iff L[M_{1}] \subseteq L[M_{2}] \land L[M_{2}] \subseteq L[M_{1}]$, o costruisco i DFA minimi di $M_{1}$ e $M_{2}$ e verifico se sono [[Isomorfismo|isomorfi]];
6. $L[M]$ è infinito? equivale a chiedersi $\exists z \in L[M] : n \leq |z| \leq 2n$ dove $n = |Q|$

<u>Nota bene</u>: $M, M_{1}, M_{2}$ sono tutti DFA. Questo giustifica il 2° punto!

## Referenze
[^1]: dal pumping lemma