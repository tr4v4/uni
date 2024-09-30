---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 25-09-2024 23:22:15
links:
  - "[[Lecture 19092024125624]]"
---
# Linguaggio formale
---
## Introduzione
> Un **linguaggio formale** $L$ su alfabeto $A$ è un sottoinsieme $L \subseteq A^{*}$, dove
> $$A^{*} = \bigcup_{n \geq 0} A^{n}$$
> e $A^{n}$ si costruisce [[Induzione strutturale|induttivamente]] come
> - $A^{0} = \{\epsilon\}$ ([[Assioma del singoletto|singoletto]] del carattere nullo)
> - $A^{n+1} = A \cdot A^{n} = \{aw | a \in A \land w \in A^{n}\}$
> 
> e $\cdot$ è l'operatore di concatenazione tra stringhe.

### Contabilità di $A^{*}$
Se $A$ è finito, $A^{*}$ è un insieme infinito [[Numerabilità|numerabile]]. Infinito perché un unione di infiniti insiemi ($n \geq 0$), e numerabile perché posso ordinare ogni $A^{n}$ in $A^{*}$ tale che $a < b < c < \cdots$ e quindi elencare tutte le parole di $A^{*}$ in funzione dei naturali $\mathbb{N}$ ($\epsilon (A^{0}), a, b, c, \cdots (A^{1}), aa, ab, ac, \cdots, ba, bb, bc, \cdots, ca, cb, cc, \cdots (A^{2}), \cdots$).

Ma anche se $A$ fosse infinito $A^{*}$ rimarrebbe numerabile! Questo segue dal fatto che $A$ è in corrispondenza biunivoca con $\mathbb{N}$ (ovvio), e che:
- $\mathbb{N} \times \mathbb{N}$ è numerabile (lo sappiamo già dalla [[Dimostrazione Q numerabile|dimostrazione di Q numerabile]], con la tecnica del _dove-tailing_)
- $\mathbb{N}^{k}$ è numerabile (con dimostrazione che sfrutta l'associazione tra una dimensione e il dove-tailing di $\mathbb{N}^{k-1}$, diminuendo la dimensione)
- $\mathbb{N}^{*} = \Cup_{k \geq 0} \mathbb{N}^{k}$ è numerabile, ovvio se si sa che $\mathbb{N}^{k}$ è numerabile

da cui $A^{*}$ numerabile.

## Notazioni
### Lunghezza di una stringa
Induttivamente vale che:
- $|\epsilon| = 0$
- $|aw| = 1 + |w|$

Per esempio: $|abc| = 1 + |bc| = 1 + 1 + |c| = 1 + 1 + 1 + 0 = 3$

### Concatenazione
La parola $xy$ è la stringa ottenuta concatenando $x$ a $y$. Formalmente si indica con
$$w = xy \iff \begin{cases} |w| = |x| + |y| \\ w(j) = x(j) & 1 \leq j \leq |x| \\ w(|x| + j) = y(j) & 1 \leq j \leq |y| \end{cases}$$

Esistono inoltre delle leggi associate a questa operazione:
- _associatività_: $x(yz) = (xy)z$
- _elemento neutro_: $x \epsilon = x = \epsilon x$

### Sottostringa
Si dice che $v$ è sottostringa di $w$ $\iff$
$$\exists x, y \in A^{*} : w = xvy$$
<u>Nota bene</u>: $x$ e $y$ possono essere ovviamente anche $\epsilon$, per cui _ogni stringa è sottostringa di se stessa_, e _$\epsilon$ è sottostringa di ogni stringa_.

#### Suffisso e prefisso
Si dice che $v$ è suffisso di $w$ $\iff$
$$\exists x \in A^{*} : w = xv$$

Si diche che $v$ è prefisso di $w$ $\iff$
$$\exists x \in A^{*} : w = vx$$

### Potenza $n$-esima di una stringa
Presa una stringa $w \in A^{*}$, si ha:
- $w^{0} = \epsilon$
- $w^{n+1} = ww^{n} \ \ \ \forall n \geq 0$

Per esempio: $(ab)^{1} = ab$, $(ab)^{2} = abab$, ecc...

### Linguaggio
Si definisce un linguaggio $L$ su alfabeto $A$ un qualunque sottoinsieme $L \subseteq A^{*}$.

Per esempio, fissato l'alfabeto $A = \{a\}$, allora saranno tutti _linguaggi finiti_ $\varnothing, \epsilon, \{a, aaa\}$.
Poi, sempre da $A$, posso definire linguaggi infiniti:
- $L_{1} = \{a, aa, aaa, \cdots\} = \{a^{n} | n \geq 1\} = A^{*} \setminus \{\epsilon\}$
- $L_{2} = \{\epsilon, aa, aaaa, \cdots\} = \{a^{2n} | n \geq 0\}$

## Operazioni
### Complemento
Si definisce $\bar{L}$ il complemento del linguaggio $L$ su alfabeto $A$ come:
$$\bar{L} = \{w \in A^{*} | w \notin L\} = A^{*} \setminus L$$

### Unione
$$L_{1} \cup L_{2} = \{w | w \in L_{1} \lor w \in L_{2}\}$$

### Intersezione
$$L_{1} \cap L_{2} = \{w | w \in L_{1} \land w \in L_{2}\}$$

### Concatenazione
$$L_{1} \cdot L_{2} = \{w_{1}w_{2} | w_{1} \in L_{1} \land w_{2} \in L_{2}\}$$

<u>Nota bene</u>: la _concatenazione non è commutativa_!

#### Differenza $L_{1} \times L_{2}$
Non bisogna assolutamente confondere la concatenazione con il [[Prodotto cartesiano|prodotto cartesiano]]. Quest'ultimo, infatti, è l'insieme delle coppie tra le stringhe di $L_{1}$ e le stringhe di $L_{2}$. Inoltre, non sono neanche equipotenti, per via dell'associatività delle stringhe.

Per esempio, prendiamo i due linguaggi $L_{1} = \{a, ab\}$ e $L_{2} = \{bc, c\}$. Avremo:
$$L_{1} \cdot L_{2} = \{abc, ac, abbc\}$$
$$L_{1} \times L_{2} = \{ (a, bc), (a, c), (ab, bc), (ab, c) \}$$

<u>Nota bene</u>: $a \cdot bc = ab \cdot c = abc$; invece $(a, bc) \neq (ab, c)$.

### Potenza
Si definisce induttivamente come:
- $L^{0} = \{\epsilon\}$
- $L^{n+1} = L \cdot L^{n} \ \ \ \forall n \geq 0$

### Chiusura
Definiamo ora la **chiusura** del linguaggio, anche detta **stella di Kleene** o **ripetizione**:
$$L^{*} = \bigcup_{n\geq 0} L^{n}$$
e la versione gemella, detta chiusura positiva
$$L^{+} = \bigcup_{n > 1} L^{n}$$
(che semplicemente esclude $\epsilon$)

## Referenze