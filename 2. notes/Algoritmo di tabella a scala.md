---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 20-10-2024 21:48:53
links:
  - "[[Lecture 10102024120505]]"
---
# Algoritmo di tabella a scala
---
## Introduzione
> L'**algoritmo di tabella a scala** è un [[Algoritmo|algoritmo]] per il calcolo del [[DFA]] [[Minimizzazione di DFA|minimo]].

## Idea
Sulla base delle osservazioni sulla minimizzazione dei DFA possiamo definire un algoritmo efficace basato su una tabella:
1. definiamo una tabella composta da solo coppie di stati "vere", ossia senza considerare quelle riflessive ($(q, q) \ \ \ \forall q$);
2. al round 0 marco con `x0` tutte le celle della tabella di coppie (finale, non finale) e (non finale, finale);
3. al round 1 marco con `x1` tutte le coppie $(q_{1}, q_{2})$ non ancora marcate che per qualche $a \in \Sigma$ ha $(\delta(q_{1}, a), \delta(q_{2}, a))$ già marcata;
4. idem per round $i$;
5. quando a un $k$-esimo round non riesco a mettere nessuna nuova marca termino l'algoritmo;

Il risultato sarà una tabella contenente celle marcate e celle non marcate: **quelle non marcate costituiscono gli stati equivalenti**.

![[algoritmo-tabella-a-scala-1.png]]

## Algoritmo
```R
# Costruisco la tabella a scala
# Marco x0 ogni coppia (q1, q2) tale che q1∈F e q2∈Q\F (e viceversa)
b := true;
i := 1;
while b {
	b := false;
	foreach (q1, q2) : !marked(q1, q2) {
		if ∃a∈∑ : marked(delta(q1, a), delta(q2, a)) {
			# Marca (q1, q2) con xi
			b := true;
		}
	}
	i := i+1
}
```

Al termine, sia $J$ l'insieme delle coppie non marcate, allora definiamo la [[Relazione di equivalenza|relazione di equivalenza]] $\sim$ come la chiusura riflessiva e simmetrica di $J$, ossia:
$$\sim = J \cup \{(q_{2}, q_{1}) | (q_{1}, q_{2}) \in J\} \cup \{(q, q) | q \in Q\}$$

<u>Nota bene</u>: _questo passaggio è necessario solo formalmente_, per passare da una tabella a scala a un insieme matematicamente "accettabile". In realtà _quello che interessa sono solo e unicamente le coppie non marcate, che si fondono per dare origine al DFA minimo_.

<u>Nota bene</u>: al round $i$, le parti di tabelle non marcate costituiscono $\sim_{i}$ (una volta chiusa riflessivamente e simmetricamente).

## Teoremi
### Terminazione
> Dato un DFA $M = (\Sigma, Q, \delta, q_{0}, F)$, _l'algoritmo di riempimento della tabella a scala termina_, e _due stati $p, q$ sono distinguibili (non equivalenti) $\iff$ la casella $(p, q)$ (o $(q, p)$) è marcata_ (di conseguenza sono equivalenti $\iff$ non è marcata).

#### Dimostrazione
Che l'algoritmo termini sempre ci è garantito dalla relazione $\sim_{i}$, infatti abbiamo già dimostrato che $\exists k : \sim_{k} = \sim_{k+1}$.

Dimostriamo ambo i versi dell'implicazione sulla distinguibilità degli stati.
$\implies$: suppongo che $p, q$ non siano equivalenti, ossia che $\exists w \in \Sigma^{*} : \hat{\delta}(p, w) \in F \land \hat{\delta}(q, w) \notin F$ (o viceversa). Se prendo $|w| = k$, allora per forza $(p, q) \notin \sim_{k}$, ossia la coppia viene marcata entro il round $k$;

$\impliedby$: suppongo $(p, q)$ marcata nella tabella, allora se si considera la catena di coppie/simboli che da $(p, q)$ portano a una coppia non presente in $\sim_{0}$ si dimostra da sé che $p, q$ sono non equivalenti.

**Qed**.

## Referenze