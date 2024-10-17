---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 05-10-2024 16:43:55
links:
  - "[[Lecture 26092024120454]]"
---
# Grammatica ambigua
---
## Introduzione
> Una [[Grammatiche libere|grammatica libera]] $G$ è detta **ambigua** se $\exists w \in L(G)$ (appartenente al [[Linguaggio generato|linguaggio generato]]) che _ammette più [[Albero di derivazione|alberi di derivazione]]_ (e di conseguenza più [[Albero sintattico|alberi sintattici]]).
> Una grammatica ambigua consente così **diverse interpretazioni sull'ordine di esecuzione delle operazioni**.

### Esempio
Consideriamo la grammatica
$$S \to a|b|c|S+S|S*S$$
e la stringa [[Derivazione|derivata]]
$$a*b+c$$

Possiamo avere due derivazioni leftmost:
1. $S \implies S+S \implies S*S+S \implies a*S+S \implies a*b+S \implies a*b+c$
2. $S \implies S*S \implies a*S \implies a*S+S \implies a*b+S \implies a*b+c$

che generano rispettivamente i due alberi
1. ![[albero-ambiguo-1.png]]
2. ![[albero-ambiguo-2.png]]

## Disambiguazione
Solitamente una grammatica ambigua è disambiguabile. _Se sappiamo che genera un linguaggio $L$, e questo linguaggio non è ambiguo, allora esisterà un'altra [[Grammatiche equivalenti|grammatica equivalente]] non ambigua che lo genera_: il vincolo è proprio che il [[Linguaggio ambiguo|linguaggio stesso non sia ambiguo]].

### Esempi
#### 1
La grammatica
$$\begin{align}
& S \to A | \epsilon \\
& A \to \epsilon
\end{align}$$
è ambigua, infatti per raggiungere la stringa $w = \epsilon$, posso fare:
1. $S \implies \epsilon$
2. $S \implies A \implies \epsilon$

e quindi produrre due alberi di derivazione.

Per disambiguarla, sapendo che $L(G) = \{\epsilon\}$, mi basta definire la nuova grammatica equivalente come
$$S \to \epsilon$$

#### 2
La grammatica dell'esempio
$$S \to a|b|c|S+S|S*S$$
è addirittura ambigua in 2 sensi:
1. _non esiste una precedenza di un operatore sull'altro ($+$ e $*$)_;
2. _non è specificata l'associatività di $+$ e $*$, infatti $a+b+c$ ha due alberi di derivazioni_.

##### Prima soluzione
Per risolverle entrambe, l'idea è di usare la seguente grammatica
$$\begin{align}
& E \to E + T | T \\
& T \to A * T | A \\
& A \to a|b|c
\end{align}$$

Così facendo si risolve:
- il problema della precedenza degli operatori, infatti così facendo vengono sempre prima svolte le operazioni con il $*$, e solo successivamente, al livello superiore quelle con il $+$; 
- il problema dell'associatività, definita a sinistra per $+$ e a destra per $*$.

Tuttavia, risolvendo le ambiguità, abbiamo diminuito la potenza espressiva della grammatica: stringhe come $a*(b+c)$, dove le parentesi servono solo a indicare la precedenza del $+$ sul $*$, non appartengono alla grammatica!

In breve, un albero di derivazione del genere
![[albero-non-generabile.png]]
non sarebbe generabile.

##### Soluzione definitiva
Per risolvere, allora, si introducono nella grammatiche le parentesi ($\in T$, terminali ausiliari) come **zucchero sintattico** per _consentire di fare il prodotto tra somme_:
$$\begin{align}
& E \to E + T | T \\
& T \to A * T | A \\
& A \to a|b|c|(E)
\end{align}$$

<u>Nota bene</u>: _le parentesi sono appunto zucchero sintattico, ossia servono solo per disambiguare la notazione lineare_. Sono solo zucchero sintattico perché _inutili nella derivazione e nell'albero di derivazione_, servono solo a noi per non confondere $a*b+c$ con $a*(b+c)$.

Una volta costruito l'albero, le parentesi non servono più a niente!

### Processo
Per disambiguare, allora, i passi sono i seguenti:
1. _si parte dalla [[Sintassi astratta|sintassi astratta]], ossia dalla grammatica semplice e intuitiva che tuttavia presenta ambiguità_;
2. _si trasforma in [[Sintassi concreta|sintassi concreta]], ossia nella versione equivalente della grammatica di partenza ma senza ambiguità e che fa uso di zucchero sintattico_;
3. _si ricava l'[[Albero concreto|albero concreto]] (togliendo lo zucchero sintattico), ossia l'albero di derivazione della sintassi concreta_;
4. _da questo si ottiene l'[[Albero sintattico|albero sintattico astratto]], quindi l'albero ottenuto dalla sintassi concreta (per disambiguare la grammatica) ma ripulito dalla sua complessità_.

## Referenze
- [[Linguaggio ambiguo]]