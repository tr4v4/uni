---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 28-08-2025 12:05:02
links:
---
# Parser LR
---
## Introduzione
> Un **parser $LR$** e' un [[Parser bottom-up|parser bottom-up]] che riconosce una _stringa leggendo da sinistra a destra ($L$) l'input e producendo una [[Derivazione canonica destra|derivazione canonica destra]] ($R$) al rovescio sulla sua [[Pila|pila]]_.

![[parser-lr.png]]

Come da immagine, gli ingredienti per costruire un parser LR sono:
- [[DFA dei prefissi viabili]];
- [[Tabella di parsing LR|tabella di parsing LR(0)]];

Una _configurazione_ di un parser LR e'
$$(s_{0} \cdots s_{n}, x_{1} \cdots x_{m}, a_{1} \cdots a_{k}\$)$$
dove:
- $s_{0} \cdots s_{n}$ e' lo **stack degli stati** (del DFA);
- $x_{1} \cdots x_{m}$ e' lo **stack dei simboli** (del [[Automa a pila|PDA]]);
- $a_{1} \cdots a_{k}$\$ e' il **resto dell'input**.

<u>Osservazione</u>: $x_{1} \cdots x_{m} a_{1} \cdots a_{k}$ e' una stringa intermedia della derivazione canonica destra.

<u>Nota bene</u>: per i parser LR assumiamo _sempre_ che la grammatica sia aumentata con un nuovo simbolo iniziale $S'$, tale che $S' \to S \in R$.

## Mosse
Il parser LR funziona sulla base delle seguenti mosse:
1. $s_{n}$ e' lo stato top della pila di stati del DFA, mentre $a_{i}$ e' il simbolo corrente dell'input;
2. consulta la tabella di parsing $LR$, in particolare la cella $M[s_{n}, a_{i}]$
	- se $M[s_{n}, a_{i}] = \text{shift} \ s$ allora la nuova configurazione sara' $$(s_{0} \cdots s_{n}s, x_{1} \cdots x_{m} a_{i}, a_{i+1} \cdots a_{k}\$)$$
	- se $M[s_{n}, a_{i}] = \text{reduce} \ A \to \beta$ allora la nuova configurazione sara' $$(s_{0} \cdots s_{n-r} s, x_{1} \cdots x_{m-r} A, a_{i}\cdots a_{k}\$)$$
		- dove $r = |\beta|$ e $M[s_{n-r}, A] = \text{goto} \ s$
		- quindi in particolare fa 3 passi:
			1. `pop` di $r$ elementi dai due stack;
			2. mette $A$ in cima alla pila dei simboli;
			3. calcola il nuovo stato top, guardando $M[s_{n-r}, A] = \text{goto} \ s$ e mette $s$ in cima alla pila degli stati;
	- se $M[s_{n}, a_{i}] = \text{accept}$ allora fine;
	- se $M[s_{n}, a_{i}] = \text{"bianco"}$ allora errore;

### Esempio
Prendiamo in considerazione la [[Grammatiche|grammatica]] $G$
$$S' \to S \ \ \ \ \ S \to (S)|()$$
che per chiarezza andremo ad indicizzare in questo modo:
1. $S' \to S$
2. $S \to (S)$
3. $S \to ()$

La tabella di parsing $LR(0)$ (in questo caso non servono simboli di [[Look-ahead|look-ahead]]), generata dal DFA dei prefissi viabili, e':
![[tabella-parsing-lr0-1.png]]

Se proviamo ad eseguire ora il parser sull'input $(())\$$, otteniamo:
![[parser-lr0-1.png]]

## Generico
Definiti il DFA dei prefissi viabili, e la corrispondente tabella di parsing $LR$, possiamo definire finalmente il generico parser $LR$:
- inizializza la pila con $\$s_{0}$ (la cima della pila e' a destra);
- inizializza $i_{C}$ con il primo carattere in input;
- `while (true)`:
	- $S = top(pila)$;
	- `case` $M[s, i_{C}]$:
		- `shift` $t$:
			- `push` $t$ sulla pila;
			- avanza $i_{C}$ sull'input;
		- `accept`:
			- `print('accept')`;
			- `break`;
		- `reduce` $A \to \alpha$:
			- `pop` $|\alpha|$ stati dalla pila;
			- $s_{1} = top(pila)$ ($s_{1}$ conterra' l'item $B \to \gamma . A \delta$);
			- $s_{2} = M[s_{1}, A]$ (ovviamente $M[s_{1}, A]$ e' `goto` $s_{2}$);
			- `push` $s_{2}$ sulla pila;
			- `print(`$A \to \alpha$`);
		- `else`:
			- `error()` (casella bianca);

<u>Nota bene</u>: usa solo lo stack degli stati (del DFA), e non quello dei simboli (del PDA)!

## Referenze