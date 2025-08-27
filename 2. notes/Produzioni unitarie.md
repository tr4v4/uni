---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 25-08-2025 19:13:26
links:
  - "[[Lecture 05112024110833]]"
---
# Produzioni unitarie
---
## Introduzione
> In una [[Grammatiche|grammatica]] le **produzioni unitarie** sono produzioni per un nonterminale della forma
> $$A \to B$$

Possono creare cicli
$$A \implies^{+} A$$
e per questo si vogliono eliminare.

## Eliminazione
### Coppia unitaria
Se le produzioni unitarie si definiscono come quelle produzioni del tipo $A \to B$ con $A, B \in NT$, allora definiamo _coppie unitarie_ le [[Coppia ordinata|coppie]] $(A, B)$ se $A \implies^{+} B$ usando solo produzioni unitarie.

Per calcolare le coppie unitarie induttivamente, definiamo
- $U_{0}(G) = \{(A, A) | A \in NT\}$;
- $U_{i+1}(G) = U_{i}(G) \cup \{(A, C) | (A, B) \in U_{i}(G) \land B \to C \in R\}$.

Anche qui si ha che $U_{i}(G) \subseteq U_{i+1}(G)$ e soprattutto che
$$\exists i_{C} : U_{i_{C}}(G) = U_{i_{C}+1}(G)$$
sempre perche' $NT$ e' finito.

Per definizione, allora poniamo $U(G) = U_{i_{C}}(G)$, detto **insieme di tutte le coppie unitarie**.

### Algoritmo
Data $G = (NT, T, S, R)$ libera, basta allora definire $G' = (NT, T, S, R')$ dove, _per ogni $(A, B) \in U(G)$, $R'$ contiene tutte le produzioni $A \to \alpha$, dove $B \to \alpha \in R$ non e' unitaria_.

<u>Osservazione</u>: poiche', per ogni $A \in NT$, la coppia $(A, A) \in U(G)$, allora $R'$ contiene tutte le produzioni non-unitarie di $R$ e in aggiunta un po' di altre.

Di conseguenza, **se $G=(NT, T, S, R)$ e' libera, e $U(G)$ e' l'insieme delle sue coppie unitarie, allora se $G'=(NT, T, S, R')$ e' la grammatica ottenuta dall'algoritmo sopra, questa non contiene produzioni unitarie e $L(G) = L(G')$**.

### Esempio
Prendiamo la grammatica non [[Grammatica ambigua|ambigua]] per le espressioni aritmetiche
$$E \to E+T|T \ \ \ \ \ T \to T*A|A \ \ \ \ \ A \to a|b|(E)$$
che ha le produzioni unitarie $E \to T$ e $T \to A$.

Costruiamo l'insieme delle coppie unitarie:
- $U_{0}(G) = \{(E, E), (T, T), (A, A)\}$;
- $U_{1}(G) = U_{0}(G) \cup \{(E, T), (T, A)\}$;
- $U_{2}(G) = U_{1}(G) \cup \{(E, A)\}$;
- $U_{3}(G) = U_{2}(G) = U(G) = \{(E, E), (T, T), (A, A), (E, T), (T, A), (E, A)\}$.

A questo punto $G'$ sicuramente avra' le produzioni
$$E \to E + T \ \ \ \ \ T \to T * A \ \ \ \ \ A \to a|b|(E)$$
per via di $U_{0}(G)$ (queste sono le produzioni non-unitarie di $R$).

In aggiunta ci saranno poi
$$E \to T * A$$
perche' $(E, T) \in U_{1}(G)$ e $T \to T*A$ non e' unitaria; poi
$$T \to a|b|(E)$$
perche' $(T, A) \in U_{1}(G)$; e infine
$$E \to a|b|(E)$$
perche' $(E, A) \in U_{2}(G)$.

Quindi, in definitiva, $G'$ sara'
$$E \to E+T|T*A|a|b|(E) \ \ \ \ \ T \to T*A|a|b|(E) \ \ \ \ \ A \to a|b|(E)$$

## Referenze