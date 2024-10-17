---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 30-09-2024 22:03:31
links:
  - "[[Lecture 24092024110820]]"
---
# Linguaggio generato
---
## Introduzione
> Il **linguaggio generato** da una [[Grammatiche|grammatica]] $G = (NT, T, R, S)$ è l'insieme
> $$L(G) = \{w \in T^{*} | S \implies^{*} w\}$$
> dove $T^{*}$ è l'_insieme di tutte le possibili combinazioni di terminali_. Ossia è l'_insieme di tutte le possibili combinazioni di terminali [[Derivazione|derivabili]] dai simboli iniziali_.

### Domande fondamentali
Le domande più complesse che hanno a che fare con i linguaggi generati sono le seguenti:
1. conoscendo la grammatica $G$, **come faccio a determinare $L(G)$**?
2. presa una stringa $w$, **come faccio a verificare $w \in L(G)$**?

Ci sono tecniche opportune per entrambe le questioni, alcune anche efficienti. Ma l'algoritmo più semplice possibile, quello _naif_, che consente di rispondere ad entrambe le domande, è: **parto da $S$ e provo ad applicare in tutti i modi possibili le produzioni per trovare una derivazione che generi $w$**.

Questo tipo di algoritmo è _non deterministico_, per cui se si prende la strada sbagliata si deve tornare indietro (_backtracking_): _è estremamente inefficiente_.

#### Esempi
##### Da grammatica a linguaggio
###### 1
Supponiamo di avere la grammatica
$$G = S \to aSb | ab$$
Allora è facile prevedere l'andamento delle derivazioni:
![[esempio-derivazioni-grammatica-linguaggio.png]]

Si avrà infatti che, una volta capito il pattern, il linguaggio generato è
$$L(G) = \{a^{n}b^{n} | n \geq 1\}$$

###### 2
Da quest'altra grammatica
$$G = S \to aAb, \ \ \ A \to aAb|\epsilon$$
si ricava ugualmente il linguaggio
$$L(G) = \{a^{n}b^{n} | n \geq 1\}$$
(provare per credere!)

Questo ci insegna che esistono grammatiche formalmente diverse ma che generano lo stesso linguaggio: _in tal caso le grammatiche si dicono [[Grammatiche equivalenti|equivalenti]]_.

###### 3
Con questa grammatica
$$G = S \to AB, \ \ \ A \to aA|a, \ \ \ B \to bB|b$$
si genera un linguaggio più complesso da capire. In realtà, pensandoci, si nota che
$$L(S) = L(A) \cdot L(B)$$
e che
$$\begin{align}
& L(A) = \{a^{n}|n \geq 1\} \\
& L(B) = \{b^{n}|n \geq 1\}
\end{align}$$
Per cui $L(A) \cdot L(B)$, ossia la loro _concatenazione_, non sarà che
$$L(G) = L(S) = \{a^{n}b^{m} | n, m \geq 1\}$$

<u>Nota bene</u>: da questo momento in poi, l'algoritmo _naif_ non sarà neanche preso in considerazione. Sarà troppo complesso generare tutte le possibili combinazioni di parole, e trovare un pattern non avrebbe fine: _bisogna usare la logica_.

###### 4
Dalla grammatica
$$G = S \to AB, \ \ \ A \to aAb|\epsilon, \ \ \ B \to bB|\epsilon$$
si genera il linguaggio
$$L(G) = \{a^{n}b^{n+m} | n, m \geq 0\} = \{a^{n}b^{m} | m \geq n \geq 0\}$$

##### Da linguaggio a grammatica
###### 1
Il linguaggio
$$L = \{a^{n}b^{m} | n \geq m \geq 0\}$$
è generato dalla grammatica
$$G = S \to AB, \ \ \ A \to \epsilon|aA, \ \ \ B \to aBb|\epsilon$$

###### 2
Il linguaggio
$$L = \{a^{2n+1} | n \geq 0\} = \{a, aaa, aaaaa, \cdots\}$$
è generato dalla grammatica
$$G = S \to a | aaS$$

###### 3
Il linguaggio
$$L = \{a^{2n} b^{2m+1} | n, m \geq 0\}$$
è generato dalla grammatica
$$G = S \to aaS | bB, \ \ \ B \to \epsilon | bbB$$

###### 4
Il linguaggio (questa volta finito)
$$L = \{ab, ac, ad\}$$
è generato dalla grammatica
$$G = S \to ab|ac|ad$$
oppure
$$G = S \to aA, \ \ \ A \to b|c|d$$

###### 5
Il linguaggio
$$L = \{a^{2n} b^{m} c^{2m} | n \geq 0, m \geq 1\}$$
è generato dalla grammatica
$$G = S \to aaS | bBcc, \ \ \ B \to \epsilon | bBcc$$

###### 6
Il linguaggio
$$L = \{a^{n} b^{k} c^{n} | n \geq 0, k \geq 1\}$$
è generato dalla grammatica
$$G = S \to aSc | B, \ \ \ B \to b | bB$$

###### 7
Il linguaggio
$$L = \{a^{n}b^{n}c^{m}d^{m} | n, m \geq 0\}$$
è generato dalla grammatica
$$G = S \to AB, \ \ \ A \to aAb|\epsilon, \ \ \ B \to cBd|\epsilon$$

## Referenze