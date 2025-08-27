---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 29-09-2024 21:02:19
links:
  - "[[Lecture 24092024110820]]"
---
# Rappresentazione finita di un linguaggio
---
## Introduzione
Assumendo di avere chiara la definizione di [[Linguaggio formale|linguaggio formale]], ci si chiede, nel caso in cui il linguaggio in questione $L$ sia infinito (ossia praticamente sempre), **in che modo si possa rappresentare in maniera finita**. E non solo: ci si chiede anche **come verificare se una stringa $w \in L$**.

E' il problema centrale dell'informatica e dei programmatori: _rappresentare oggetti infiniti in una memoria finita_.

Per capire come fare, si prende spunto dagli [[Assiomi di Peano|assiomi di Peano]], che consentono di rappresentare l'infinita dei [[Numeri naturali|naturali]] $\mathbb{N}$ in modo finito, con solo due regole:
1. $0 \in \mathbb{N}$
2. $x \in \mathbb{N} \implies S(x) \in \mathbb{N}$, dove $S(x)$ è il _successore_ di $x$

Allo stesso modo, posso rappresentare implicitamente i numeri pari $\mathbb{P}$, attraverso una [[Funzione informatica|funzione informatica]] _finita_ che li identifica:
```R
fun pari(x: integer): boolean {
	pari := (x mod 2 = 0);
	return pari;
}
```

## Tecniche
Per i [[Linguaggio di programmazione|linguaggi]] esistono 2 tecniche:
- **generativo**/sintetico, che definisce il linguaggio come l'_insieme delle stringhe generate_ da una struttura finita detta [[Grammatiche|grammatica]];
- **riconoscitivo**/analitico, che definisce il linguaggio come l'_insieme delle stringhe riconosciute_ da una struttura finita detta [[Automa|automa]].

Nonostante le buone intenzioni, purtroppo c'è un limite matematico anche qui. Sappiamo infatti che $|A^{*}| = |\mathbb{N}|$, ossia che l'insieme di tutte le combinazioni di lettere di un alfabeto $A$ è [[Equipotenza|equipotente]] ad $\mathbb{N}$; e sappiamo anche che un qualunque linguaggio $L$ è definito come $L \subseteq A^{*}$. Allora l'**insieme di tutti i linguaggi altro non sarà che l'[[Assioma dell'insieme potenza|insieme potenza]] di $A^{*}$**:
$$\mathscr{P}(A^{*})$$

E' noto che l'insieme delle parti di un insieme infinito ha la [[Cardinalità|cardinalità]] di $\mathbb{R}$ (la cardinalità del continuo), che per il [[Teorema di Cantor|teorema di Cantor]], è _un infinito ben maggiore di quello contabile_.

In poche parole, **esistono tantissimi linguaggi che non possono essere rappresentati finitamente, né da una grammatica né da un automa**. Questo è facilmente dimostrabile con l'_argomento diagonale di Cantor_[^1].

## Referenze
[^1]: lo stesso che dimostra che $\mathbb{R}$ [[Dimostrazione R non numerabile|non è numerabile]]