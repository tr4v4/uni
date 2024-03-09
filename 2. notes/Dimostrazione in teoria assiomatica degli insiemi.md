---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 23-09-2023 20:29:53
links:
  - "[[Lecture 21092023090321]]"
  - "[[Lecture 27092023131717]]"
  - "[[Lecture 28092023090721]]"
---
# Dimostrazione in teoria assiomatica degli insiemi
---
## Premesse
- usiamo le dimostrazioni per comprendere la matematica che ci servirà per capire le dimostrazioni (sempre materia circolare)
- regolate da _linguaggio artificiale_
- le prove informali contengono "abusi", non correttissime, quindi ometteremo dei passaggi
- per studiare la logica useremo _meta-dimostrazioni_ (come la _meta-logica_)

## Composizione
Una dimostrazione si compone di:
- **[[Enunciato|enunciato]]** - _quello che vogliamo dimostrare_
- **prova** - _sequenza di passi che ci convincono che la conclusione valga quando valgono le ipotesi_

E' possibile, e anzi molto frequente, che durante il processo di dimostrazione sia necessario dimostrare un altro _enunciato intermedio_[^1].

## Regole fondamentali
Per dimostrare esistono _2 fondamentali regole_ che si devono adottare per poter usare correttamente gli "operatori" logici:
- **regola d'introduzione** - si deve usare nel momento in cui devo dimostrare una tesi
- **regola d'eliminazione** - si deve usare nel momento in cui, dimostrata una tesi la utilizzo come ipotesi per trarre delle conclusioni

Se volessimo fare un paragone con il mondo videoludico:
- le _ipotesi_ sono le _armi_
- le _regole d'introduzione_ sono l'_attacco diretto al boss_
- le _regole d'eliminazione_ sono l'_utilizzo delle armi_

In poche parole:
- le regole d'introduzione si usano per approcciare le tesi
- le regole d'eliminazione si usano per utilizzare le ipotesi

## Costrutti
### $\forall$
**Introduzione**:
- per dimostrare $\forall x, P(x)$
- "_sia $x$ un insieme..._" o "_sia $x$ fissato_"
	- fissato perché non so com'è fatto, uno dei possibili infiniti $x$ che scelgo e fisso (non lo cambio)
- Matita: "_assume x : set ..._"

**Eliminazione**:
- sai già che vale il $\forall$ (già dimostrato), quindi con l'ipotesi che sai scegli tu di andare avanti con la dimostrazione usando un soggetto specifico (se so che tutti i numeri sono "pari", allora 5 è pari)
- Matita: "_by NOME_IPOTESI we proved CONCLUSIONE_"

### $\implies$
**Introduzione**:
- per dimostrare $P \implies Q$
- assumo che $P(H)$ dove H è l'ipotesi e dimostro l'ipotesi come prova di $Q$
- Matita: "_suppose P (H)_"

**Eliminazione**:
- già dimostrato, voglio usare l'ipotesi dimostrata
- combinare ipotesi $P \implies Q$ con ipotesi che vale $P$: "se vale '$P$ allora $Q$' e se vale $P$, allora $Q$"
- Matita: "_by NOME_IPOTESI_PQ, NOME_IPOTESI_P we proved Q_"

### $\iff$
**Introduzione**:
- per dimostrare $P \iff Q$ si dimostra sia $P \implies Q$ che $Q \implies P$

**Eliminazione**:
- ipotesi già dimostrata
- posso usarla quindi sia in una direzione che in un'altra ($P \implies Q$ e $Q \implies P$)

### $\neg$
E' un'abbreviazione: non P è un'abbreviazione per $P \implies \text{assurdo}$.
**Introduzione**:
- per dimostrare possiamo trasformare la negazione in implicazione

**Eliminazione**:
- per concludere possiamo trasformare la negazione in implicazione

### $\land$
**Introduzione**:
- per usare AND le dimostro entrambe
- devo dimostrarle entrambe
- Matita: "_by cong, NomeP, NomeQ we proved P $\land$ Q (H)_"

**Eliminazione**:
- per usare AND posso scegliere arbitrariamente quale
- Matita:

### $\lor$
**Introduzione**:
- devo dimostrare $P \lor Q$, per farlo basta dimostrare $P$ oppure $Q$ (posso scegliere)
- <u>attenzione</u>: bisogna fare la "scelta giusta"
	- è molto facile incorrere nella strada sbagliata
	- noi non sappiamo quale dei due valga
	- quindi usare l'introduzione dell'OR solo dopo che si è dimostrato che $P$ e $Q$ sono entrambi dimostrabili
- Matita: "_by or_introl, NOMEp we proved P $\lor$ Q_" oppure "_by or_intror, NOMEq we proved P $\lor$ Q_"

**Eliminazione**:
- so già che vale $P \lor Q$
- bisogna procedere per casi (perché noi non sappiamo quali delle due è dimostrabile)
	- caso in cui vale P, ...
	- caso in cui vale Q, ...
- Matita:
  "_we proceed by cases on NOME_P_or_Q to prove CONCLUSIONE
  case or_introl
	  suppose P (H)
	  ...
  case or_intror
	  suppose Q (H)
	  ..._"
- es. monotonia dell'unione

### $\exists$
**Introduzione**:
- esiste un $X$ che ha certe proprietà
	- non ci interessa quale[^2]
	- per dimostrare la sua esistenza dobbiamo trovare uno specifico X
- quindi scelgo un qualche E e dimostro P(E), ovvero che E ha la proprietà P
- Matita: "_by ex_intro, NOME_Pe we proved $\exists X. P(X)$_"

**Eliminazione**:
- dobbiamo ragionare con un X generico, perché non sappiamo chi sia
	- infatti "sia X un qualunque elemento con la proprietà P"
- <u>attenzione</u>: X dev'essere una variabile non in uso in nessuna ipotesi o nella conclusione
- Matita: "_by PROOF_EXISTS_x_Px let X: set such that P(X) (H)_"

### Assurdo
- _non è la dimostrazione per assurdo_
- il falso è ciò che non vale mai

**Introduzione**:
- dimostrare il falso --> impossibile

**Eliminazione**:
- sappiamo che vale il falso (qualcosa che non può valere)
- se le ipotesi vanno in contrasto tra di loro, nessuna tesi potrà soddisfarle tutte, quindi possiamo concludere qualunque cosa perché non c'è alcuna situazione in cui valga il falso
	- _se x è sia pari che dispari allora gli elefanti volano_
- dall'assurdo possiamo concludere qualunque cosa
- Matita: "_using (ABSURDUM nome) done_"

## Regole generali
### Abbreviazioni
- unione $\forall$ e $\implies$
	- di solito si abbreviano le formule, quindi per dimostrare $\forall x, P(X) \implies Q(x)$
	- ricordiamo che P è una proprietà che crea un certo sottoinsieme 
	- unendo il $\forall$ e il $\implies$ si scrive in breve: "_sia $x$ tale che $P(x)$_"
- combinazioni di ipotesi
	- si dice "_combinando tutte quelle ipotesi lì ottengo questo risultato_"
	- Matita: "_by H1, H2, ..., Hn we proved P (H)_"
	- di solito ciò che abbiamo appena dimostrato viene usato subito come ipotesi
		- ho dimostrato H7, unendo H7 con altri ipotesi ho ricavato H8, unendo H8 con altre ipotesi ...
		- si usa il "_quindi_" per fare prima

### Espansioni
- non è un passaggio logico, serve solo per rendere più comprensibile una dimostrazione
- si scrive: $P, \text{ ovvero } Q$
	- esempio $X \subseteq Y, \text{ ovvero } \forall Z, (Z \in X \implies Z \in Y)$
- Matita: "_P that is equivalent to Q_"

### Convenzioni
- se l'enunciato contiene variabili non associate a $\forall$ o $\exists$, si mette un $\forall$ all'inizio
	- in Matita tutto inizia con $\forall$

### Esplicitazione
- si deve esplicitare talvolta cosa dobbiamo dimostrare (soprattutto in testi lunghi in cui ci si può perdere)
- serve al lettore
- Matita: "_the thesis becomes P_"

### Ovvio
- c'è una dimostrazione, magari lunga, che viene omesso e che deve ricostruirsi il lettore per conto suo
- Matita: "_done_"

### Risultati intermedi
- si possono creare ipotesi rispettando le regole d'introduzione
- a partire da ipotesi, con regola d'introduzione di un qualunque "operatore" posso creare una nuova ipotesi
- es.
	- _per H1 e H2 si ha $A \land B$ (H3)_
	- _per H1 si ha $A \lor B$ (H3)_
- es. $X \in Y \implies X \in Y \cup Z$

## Esempi di dimostrazioni


## Referenze
[^1]: sulla stessa linea di principio della scomposizione in sottoproblemi dell'approccio [[Approccio top-down|top-down]]
[^2]: un po' come per le [[Interfaccia|interfacce]] informatiche, per cui non ci interessa la loro implementazione, ma solo che ci sono