---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 14-10-2024 11:24:03
links:
  - "[[Lecture 03102024120247]]"
---
# Linguaggio accettato
---
## Introduzione
Informalmente si potrebbe dire che un NFA $N$ accetta una stringa $w = a_{1} \cdots a_{n} \iff$ nel [[Diagramma di transizione|diagramma di transizione]] esiste un cammino da $q_{0}$ (stato iniziale) a uno stato $\in F$ (stato finale) nel quale la stringa che si ottiene concatenando le etichette degli archi percorsi è esattamente $w$.

Per la definizione formale è necessario introdurre le nozioni di:
- _descrizione istantanea_
- _mossa_
- _cammino_

### Descrizione istantanea
La descrizione istantanea è la coppia
$$(q, w)$$
con:
- $q$ stato corrente;
- $w$ input da leggere.

### Mossa
Per mossa si intende formalmente una [[Regole di inferenza|regola d'inferenza]] che rappresenta formalmente il passaggio da un nodo (stato) all'altro del diagramma (automa) attraverso un arco (carattere letto in input):
$$\begin{prooftree}
\AxiomC{$q' \in \delta(q, \sigma)$}
\RL{$ \ \ \ \begin{cases} \sigma \in \Sigma \cup \{\epsilon\} \\ w \in \Sigma^{*} \end{cases}$}
\UIC{$(q, \sigma w) \vdash_{N} (q', w)$}
\end{prooftree}$$

### Cammino
Il cammino non è altro che la chiusura riflessiva e transitiva della mossa $\vdash_{N}$, ossia un'[[Assioma|assioma]] e una regola [[Induzione strutturale|induttiva]]:
$$\begin{prooftree}
\AxiomC{}
\UIC{$(q, w) {\vdash_{N}}^{*} (q, w)$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{$(q, w) \vdash_{N}^{*} (q', w') \ \ \ (q', w') \vdash_{N} (q'', w'')$}
\UIC{$(q, w) {\vdash_{N}}^{*} (q'', w'')$}
\end{prooftree}$$

## Definizione
> Il **linguaggio accettato** da un NFA $N$, indicato con $L[N]$, è
> $$L[N] = \{w \in \Sigma^{*} | \exists q \in F : (q_{0}, w) {\vdash_{N}}^{*} (q, \epsilon)\}$$
> Di conseguenza, il riconoscimento di una stringa $w$ in $L[N]$ è definito da
> $$w \in L[N] \iff \exists q \in F : (q_{0}, w) {\vdash_{N}}^{*} (q, \epsilon)$$

## Proprietà
### Equivalenza
> Due NFA $N_{1}, N_{2}$ si dicono _equivalenti_ sse accettano lo stesso linguaggio, ossia se
> $$L[N_{1}] = L[N_{2}]$$

<u>Nota bene</u>: per un linguaggio $L$, se esiste un NFA $N$ tale che $L = L[N]$, allora ne esistono infiniti equivalenti. Ovvio, _basta aggiungere "spazzatura"_ come si fa con le [[Grammatiche equivalenti|grammatiche equivalenti]].

## Referenze