---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 24-03-2025 19:22:31
links:
  - "[[Lecture 19032025092241]]"
---
# Algoritmo di Goldberg-Tarjan
---
## Introduzione
> L'**algoritmo di Goldberg-Tarjan** è un [[Algoritmo|algoritmo]] per risolvere il [[Problema del flusso massimo|problema del flusso massimo]], basata sulla nozione di _preflusso_.

### Preflussi
In opposizione all'[[Algoritmo di Ford-Fulkerson|algoritmo di Ford-Fulkerson]] e all'[[Algoritmo di Edmonds-Karp|algoritmo di Edmonds-Karp]], questo _costruisce ad ogni iterazione il flusso massimo più locale_, al posto di cercare un flusso massimo globale. In particolare, **abbandona l'idea di flusso ammissibile**: si concentra nel trovare _soluzioni ottime localmente_, che quindi _globalmente potrebbero non rispettare i vincoli di conservazione del flusso_. Queste soluzioni ottime locali costituiscono quindi una nozione di flusso più liberale, più permissiva, del flusso ammissibile: si chiamano **preflussi**.

Dei preflussi cambiano sostanzialmente i vincoli per i nodi intermedi:
$$\sum\limits_{(j, i) \in BS(i)} x_{ji} - \sum\limits_{(i, j) \in FS(i)} x_{ij} \geq 0 \ \ \ \ \ \ i \in N \setminus \{s, t\}$$

In altre parole i vincoli di capacità sono soddisfatti, mentre quelli di bilanciamento ai nodi intermedi no, e quindi possiamo far entrare più flusso rispetto a quanto ne esce.

Definiamo allora l'**eccesso** $e_{i}$ di un nodo proprio come la differenza
$$e_{i} = \sum\limits_{(j, i) \in BS(i)} x_{ji} - \sum\limits_{(i, j) \in FS(i)} x_{ij}$$
e diremo che un nodo $i$ è attivo se $e_{i} > 0$, e bilanciato altrimenti.

<u>Nota bene</u>: un preflusso in cui tutti i suoi nodi $i$ hanno $e_{i} = 0$, è un flusso ammissibile.

## Algoritmo
### Idea
L'idea dell'algoritmo è quella di eliminare gli eccessi presenti nel preflusso corrente in modo _iterativo_ e _locale_. Lo si fa spostando il flusso da ogni eccesso in 2 modi:
- `PushForward` --> spostiamo il flusso da $i$ in un arco $(i, j)$ se $x_{ij} < u_{ij}$;
- `PushBackward` --> spostiamo il flusso da $i$ in un arco $(j, i)$ se $x_{ij} > 0$;

Queste operazioni devono essere fatte in modo controllato, attraverso un _sistema di etichettature_: **possiamo fare push su $i$ solo se la sua "quota"/"altezza" è sufficientemente più alta rispetto a quella del nodo $j$ su cui si vuole scaricare il flusso**.

![[goldberg-tarjan-algoritmo.png]]

dove:
- `EtichettaturaValida(G)` --> $d_{i} =$ lunghezza del cammino minimo da $i$ a $t$, quindi sarà più alto più si è lontani da $t$;
- `PushForward(v, j)` --> aumento il flusso $(v, j)$ del minimo tra $e_{v}$ e $u_{vj} - x_{vj}$, formalmente $x_{vj} = x_{vj} + \min\{u_{vj} - x_{vj}, e_{v}\}$;
- `PushBackward(i, v)` --> diminuzione del flusso $x_{iv}$, ossia $x_{iv} = x_{iv} - \min\{x_{iv}, e_{v}\}$;
- `Relabel(v)` --> vogliamo aumentare la quota di $v$ aumentandola quanto basta per effettuare una `PushForward` o una `PushBackward`.

### Complessità
La [[Complessità computazionale|complessità]] dell'algoritmo è
$$O(N^{2}A)$$

## Referenze