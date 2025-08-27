---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 19-10-2024 18:16:59
links:
  - "[[Lecture 08102024111650]]"
---
# Equivalenza tra NFA ed espressioni regolari
---
## Introduzione
> Data un'[[Espressione regolare|espressione regolare]] $s$ possiamo costruire un [[NFA]] $N[s]$ tale che
> $$\mathscr{L}[s] = L[N[s]]$$
> ossia che _il [[Linguaggio denotato da un'espressione regolare|linguaggio denotato]] da $s$ è lo stesso [[Linguaggio accettato|riconosciuto]] dal NFA di $s$_.

In poche parole il teorema ci dice che **gli NFA riconoscono tutti i possibili [[Linguaggio regolare|linguaggi regolari]]**.

## Dimostrazione
Dimostriamo il teorema per [[Induzione strutturale|induzione]] sulla [[Sintassi|sintassi]] ([[Sintassi astratta|astratta]]) dell'espressione regolare $s$. In particolare costruiremo l'NFA $N[s]$ in modo semplificato, ossia mantenendo sempre queste due proprietà:
1. _lo stato iniziale non ha archi entranti_;
2. _lo stato finale è unico e non ha archi uscenti_;

### $s = \varnothing$
Il linguaggio denotato $\mathscr{L}[\varnothing]$ è semplicemente $\varnothing$, allora l'NFA $N[s]$ equivalente è
![[regex-to-nfa-1.png]]
ossia due stati non connessi.

### $s = \epsilon$
Il linguaggio denotato $\mathscr{L}[\epsilon] = \{\epsilon\}$, e l'NFA $N[s]$ equivalente è
![[regex-to-nfa-2.png]]

### $s = a$
Il linguaggio denotato $\mathscr{L}[a] = \{a\}$, e l'NFA $N[s]$ equivalente è
![[regex-to-nfa-3.png]]

### $s = s \cdot s$
Il linguaggio denotato $\mathscr{L}[s_{1} \cdot s_{2}] = \mathscr{L}[s_{1}] \cdot \mathscr{L}[s_{2}]$, per cui ci basta costruire un NFA scomposto in due parti poste in sequenza: la prima che riconosce $\mathscr{L}[s_{1}]$ e la seconda che riconosce $\mathscr{L}[s_{2}]$.
![[regex-to-nfa-4.png]]
Osserviamo infatti che
$$\mathscr{L}[s_{1} \cdot s_{2}] = \mathscr{L}[s_{1}] \cdot \mathscr{L}[s_{2}] = L[N[s_{1}]] \cdot L[N[s_{2}]] = L[N[s_{1} \cdot s_{2}]]$$

### $s = s/s$
Il linguaggio denotato $\mathscr{L}[s_{1}/s_{2}] = \mathscr{L}[s_{1}] \cup \mathscr{L}[s_{2}]$, allora l'idea è di costruire un NFA in cui sia possibile riconoscere sia stringhe di $\mathscr{L}[s_{1}]$ che stringhe di $\mathscr{L}[s_{2}]$, scomponendo questi due sottoautomi e ponendoli in parallelo.
![[regex-to-nfa-5.png]]
Osserviamo infatti che
$$\mathscr{L}[s_{1}/s_{2}] = \mathscr{L}[s_{1}] \cup \mathscr{L}[s_{2}] = L[N[s_{1}]] \cup L[N[s_{2}]] = L[N[s_{1}/s_{2}]]$$

### $s = s^{*}$
Il linguaggio denotato $\mathscr{L}[s^{*}] = (\mathscr{L}[s])^{*}$, allora ci basta costruire un NFA che riconosca, per ipotesi induttiva $\mathscr{L}[s]$, e per il quale sia possibile, _con una transizione-$\epsilon$_, ciclare all'infinito su quella porzione di sottoautoma.
![[regex-to-nfa-6.png]]
Osserviamo infatti che
$$\mathscr{L}[s^{*}] = (\mathscr{L}[s])^{*} = (L[N[s]])^{*} = L[N[s^{*}]]$$

<u>Nota bene</u>: la transizione-$\epsilon$ dallo stato $i$ a $f$ garantisce che l'automa riconosca anche la stringa $\epsilon$, perché per definizione $L^{*} = \bigcup_{n\geq 0} L^{n}$[^1], per cui dev'essere incluso il caso $n=0$.

## Referenze
[^1]: dalla [[Linguaggio formale#Chiusura|chiusura di linguaggio formale]]