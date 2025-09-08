---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 28-08-2025 13:12:56
links:
---
# DFA dei prefissi viabili
---
## Introduzione
> Il **[[DFA]] dei [[Prefisso viabile|prefissi viabili]]**, anche detto **automa canonico $LR(0)$** e' uno pseudo-DFA usato dai [[Parser bottom-up|parser bottom-up]], in particolare gli [[Parser LR|LR]], per costruire le [[Tabella di parsing LR|tabelle di parsing]] $LR(0)$.

Un parser ([[Automa a pila|PDA]]) puo' consultare il (ossia la [[Tabella di parsing LR|tabella di parsing]] $LR(0)$ costruita a partire da esso) per decidere cosa fare:
- se la pila contiene un prefisso viabile completo --> **reduce**;
- se la pila contiene un prefisso viabile incompleto --> **shift**;
- se la pila non contiene un prefisso viabile --> _errore_.

A seconda di come e' fatto il DFA, il parser puo' risultare deterministico o meno (sfruttando informazioni di [[Look-ahead|look-ahead]] e sui [[First e follow|follow]] dei nonterminali per ottenere determinismo).

Teoricamente, _ad ogni modifica della pila dei simboli (del PDA), il DFA la riscandisce da capo per determinare come sia fatto il prefisso viabile corrente_: tuttavia **questo non e' necessario, perche' ogni prefisso di un prefisso viabile e' un prefisso viabile**!
In particolare, la pila viene modificata in 2 modi:
- **shift** --> la pila passa da $\$\gamma$ a $\$\gamma x$; in tal caso il DFA si trova nello stato $s$ dopo aver elaborato $\$\gamma$ $\implies$ basta far ripartire il DFA da $s$ con input $x$;
- **reduce** --> la pila passa da $\$\gamma \alpha$ a $\$\gamma A$; in tal caso il DFA si trova nello stato $s$ dopo aver elaborato $\$\gamma \alpha$ $\implies$ non c'e' bisogno di far ripartire il DFA dalla base della pila, basta ripristinare lo stato in cui si trovava subito prima di elaborare il primo simbolo di $\alpha$ e fornirgli il simbolo $A$ in input.

E' per questa ragione che **serve lo stack degli stati del DFA**![^1].

## Costruzione
### Stato
Uno stato del DFA dei prefissi viabili e' costituito da un insieme di **item $LR(0)$**.

#### Item $LR(0)$
> Un **item $LR(0)$** e' una produzione con indicata, tramite un punto $.$, una posizione della sua parte destra.

Per esempio, la produzione $A \to XYZ$ genera 4 item:
1. $A \to .XYZ$
2. $A \to X.YZ$
3. $A \to XY.Z$
4. $A \to XYZ.$

Il **punto $.$ indica quanta parte della produzione e' gia' stata analizzata**! Infatti:
- se l'item $A \to \alpha . \beta$ e' nello stato del DFA in cima alla pila, significa che $\alpha$ e' sulla pila dei simboli e che ci si aspetta che l'input da leggere contenga (o possa venir ridotto a) $\beta$ --> _caso del prefisso viabile incompleto_;
- se l'item $A \to \alpha.$ e' nello stato del DFA in cima alla pila, significa che sulla pila dei simboli c'e' la _maniglia_ $\alpha$ e possiamo fare la _reduce_ --> _caso del prefisso viabile completo_.

### NFA
Partiamo quindi con la costruzione dell'[[NFA]] dei prefissi viabili. Fissiamo una grammatica libera $G = (NT, T, S, R)$, e aumentiamola con un nuovo simbolo iniziale $S'$ e una produzione $S' \to S$.

Allora l'NFA dei prefissi viabili si ottiene cosi':
- $[S' \to .S]$ e' lo stato/item iniziale;
- da $[A \to \alpha . X \beta]$ c'e' una transizione verso $[A \to \alpha X . \beta]$ etichettata $X$, per $X \in T \cup NT$;
- da $[A \to \alpha . X \beta]$, per $X \in NT$ e per ogni produzione $X \to \gamma$, c'e' una transizione-$\epsilon$ verso $[X \to . \gamma]$.

<u>Osservazione</u>: non serve definire gli stati finali. Di fatto non si tratta formalmente di un vero e proprio NFA, ma solo di un ausilio al parser.

#### Esempio
Prendiamo la grammatica:
1. $S' \to S$
2. $S \to (S)$
3. $S \to ()$

e generiamo gli item $LR(0)$ per ognuna delle 3 produzioni:
- $S' \to .S | S.$
- $S \to .(S)|(.S)|(S.)|(S).$
- $S \to .()|(.)|().$

Usando ora le regole definite sopra creiamo il seguente NFA:
![[nfa-prefissi-viabili-1.png]]

### Automa canonico $LR(0)$
Il reale automa canonico $LR(0)$, adesso, non e' altro che **il DFA che si ottiene dall'NFA dei prefissi viabili mediante [[Costruzione per sottoinsiemi|costruzione per sottoinsiemi]]**.

In realta' c'e' un altro sistema per calcolare in modo diretto il DFA a partire dal NFA: si utilizzano le due funzioni `Clos(I)` e `Goto(I, X)`, dove $I$ e' un insieme di item (stati del NFA) e $X \in T \cup NT$.

#### `Clos(I)`
- ripeti finche' $I$ e' modificato:
	- per ogni item $A \to \alpha . X \beta \in I$:
		- per ogni produzione $X \to \gamma$:
			- aggiungi $X \to .\gamma$ ad $I$;
- ritorna $I$;

Notare che sta letteralmente calcolando la **$\epsilon$-closure** di $I$.

#### `Goto(I, X)`
- inizializza $J = \varnothing$;
- per ogni item $A \to \alpha . X \beta \in I$:
	- aggiungi $A \to \alpha X . \beta$ a $J$;
- ritorna `Clos(J)`;

Notare che sta letteralmente calcolando la **$\epsilon$-closure della mossa** di $I$.

#### Costruzione
- inizializza $\mathbb{S} = \{\text{Clos}(\{S' \to .S\})\}$;
- inizializza $\delta = \varnothing$;
- ripeti finche' $\mathbb{S}$ o $\delta$ vengono modificati:
	- per ogni $I \in \mathbb{S}$:
		- per ogni item $A \to \alpha . X \beta \in I$:
			- sia $J = \text{Goto}(I, X)$;
			- aggiungi $J$ a $\mathbb{S}$;
			- aggiungi $\delta(I, X) = J$ a $\delta$;
- ritorna $\mathbb{S}$ e $\delta$;

#### Esempi
##### 1
L'NFA calcolato in precedenza
![[nfa-prefissi-viabili-1.png]]
diventa semplicemente
![[dfa-prefissi-viabili-1.png]]

##### 2
Prendiamo la grammatica $G$
1. $S' \to S$
2. $S \to (S)$
3. $S \to A$
4. $A \to a$

che genera il linguaggio $L(G) = \{(^{n} a )^{n} | n \geq 0\}$

Il DFA dei prefissi viabili sara'
![[dfa-prefissi-viabili-2.png]]

in cui notiamo che (essendo la grammatica $LR(0)$) possiamo associare un'azione ad ogni stato:
- _shift_ per 1, 3, 6;
- _reduce_ per 2, 5, 7;
- _accept_ per 4.

### Caso $LR(1)$
Per le [[Grammatiche LR(1)|grammatiche]] $LR(1)$ sappiamo che non basta l'automa canonico $LR(0)$. **Serve fare in modo che ogni item di ogni stato sia associato a un carattere di look-ahead**!

#### Item $LR(1)$
> Un **item $LR(1)$** e' una [[Coppia ordinata|coppia]] formata da:
> - _un item $LR(0)$ (anche detto nucleo o core)_;
> - _un simbolo di look-ahead in $T \cup \{\$\}$_.

#### Intuizione
L'idea e' che se l'automa canonico $LR(1)$ si trova in uno stato che contiene l'item $LR(1)$
$$[A \to \alpha.\beta, x]$$
allora significa che:
- sta cercando di riconoscere la maniglia $\alpha \beta$ (vuole completare il prefisso viabile);
- della maniglia gia' si trova $\alpha$ sulla pila;
- sull'input si aspetta una stringa derivabile da $\beta x$ $\implies$ quindi $x$ puo' _davvero_ essere fatta in _questa_ derivazione;

Quando con $SLR(1)$ usavo il $\text{Follow}(A)$, sapevo solo che esisteva una derivazione che produce $x \in \text{Follow}(A)$, ma non e' detto che sia proprio quella che sto esaminando!

Se invece l'automa si trova nello stato che contiene l'item $LR(1)$
$$[A \to \alpha ., x]$$
allora faccio la reduce $A \to \alpha$ _solo_ se c'e' $x$ in input.

#### NFA $LR(1)$
L'NFA $LR(1)$ si ottiene nel seguente modo:
- gli stati sono item $LR(1)$ della _grammatica aumentata_;
- $[S' \to .S, \$]$ e' lo stato iniziale;
- dallo stato $[A \to \alpha. X \beta, a]$ c'e' una transizione allo stato $[A \to \alpha X . \beta, a]$ etichettata $X$, per $X \in T \cup NT$;
- dallo stato $[A \to \alpha . X \beta, a]$, per $X \in NT$ e per ogni produzione $X \to \gamma$, c'e' una transizione-$\epsilon$ verso lo stato $[X \to .\gamma, b]$ per ogni $b \in \text{First}(\beta a)$;

<u>Nota bene</u>: $\text{First}(\beta a) \subseteq T \cup \{\$\}$.

#### Automa canonico $LR(1)$
Il DFA corrispondente si ricava sempre per costruzione per sottoinsiemi oppure usando delle funzioni `Clos` e `Goto` modificate.

##### `Clos(I)`
- ripeti finche' $I$ e' modificato:
	- per ogni item $[A \to \alpha . X \beta, a] \in I$:
		- per ogni produzione $X \to \gamma$:
			- per ogni $b \in \text{First}(\beta a)$:
				- aggiungi $[X \to .\gamma, b]$ ad $I$;
- ritorna $I$;

##### `Goto(I, X)`
- inizializza $J = \varnothing$;
- per ogni item $[A \to \alpha . X \beta, a] \in I$:
	- aggiungi $[A \to \alpha X . \beta, a]$ a $J$;
- ritorna `Clos(J)`;

<u>Osservazione</u>: il `Goto` non agisce sul carattere di look-ahead, ma solo sull'item $LR(0)$ (core) dell'item $LR(1)$ (salvo poi fare la `Clos(J)`).

Lo _stato iniziale dell'automa canonico $LR(1)$ sara' allora $Clos([S' \to S, \$])$_.

#### Esempio
Prendiamo la grammatica:
0. $S' \to S$
1. $S \to CC$
2. $C \to cC$
3. $C \to d$

E' una grammatica regolare (genera linguaggio $c^{*}dc^{*}d$), e inoltre e' anche $LR(0)$[^2]. Di fatto non ci sono conflitti neanche nella tabella di parsing $LR(0)$. L'automa canonico $LR(0)$ e' il seguente:
![[automa-canonico-lr0-per-lr1.jpg]]

mentre la tabella di parsing $LR(0)$ e':

|     | $c$  | $d$  | $\$$  | $S$  | $C$  |
| --- | ---- | ---- | ----- | ---- | ---- |
| $0$ | $s3$ |      |       | $g1$ | $g2$ |
| $1$ |      |      | $acc$ |      |      |
| $2$ | $s3$ | $s4$ |       |      | $g5$ |
| $3$ | $s3$ | $s4$ |       |      | $g6$ |
| $4$ | $r3$ | $r3$ | $r3$  |      |      |
| $5$ | $r1$ | $r1$ | $r1$  |      |      |
| $6$ | $r2$ | $r2$ | $r2$  |      |      |

Notiamo anche che la tabella $SLR(1)$ della stessa grammatica e' assolutamente identica! Infatti i follow di $C$ sono $\{c, d, \$\}$.

Guardiamo la produzione $S \to CC$. In generale sappiamo che $C$ come follow ha $\{c, d, \$\}$, ma in una derivazione reale, in realta':
- la prima $C$ ha come follow $\{c, d\}$ (perche' ha la $C$ davanti);
- la seconda $C$ ha come follow $\$$ (perche' e' il follow di $S$!).

Di conseguenza, nella realta' dei fatti, se seguiamo i reali follow dei nonterminali otteniamo strade differenti e comportamenti differenti, che ci consentono di risolvere molti conflitti shift-reduce! In questa grammatica non ci sono conflitti, ovviamente, ma in altre non $LR(0)$ e neanche $SLR(1)$, questi ci sono eccome!

L'automa canonico $LR(1)$ ottenuto a partire dalla grammatica e' allora il seguente:
![[automa-canonico-lr1-1.png]]

Notiamo che ci sono _molti piu' stati_! Infatti $I_{6}$ e $I_{3}$ sono separati sulla base dei loro "reali" follow:
- se da $I_{0}$ (stato iniziale) leggiamo $c$, allora stiamo leggendo la prima $C$, che come follow ha solo $\{c, d\}$;
- se invece da $I_{2}$ leggiamo $c$, allora stiamo leggendo la seconda $C$, che come follow ha solo $\{\$\}$.

Nell'automa $LR(0)$ corrispondente, le coppie di stati $(I_{6}, I_{3})$, $(I_{8}, I_{9})$ e $(I_{4}, I_{7})$ collassano in un unico stato!

## Referenze

[^1]: tecnicamente basta solo quello... non serve piu' lo stack dei simboli del PDA, ma per ragioni didattiche lo teniamo lo stesso

[^2]: non per niente: e' libero deterministico (in quanto regolare) e gode anche della prefix-property $\implies$ e' $LR(0)$!
