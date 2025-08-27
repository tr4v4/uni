---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 25-08-2025 20:19:36
links:
  - "[[Lecture 07112024120244]]"
  - "[[Lecture 12112024110924]]"
---
# First e follow
---
## Introduzione
> I **first e follow** sono delle funzioni ausiliarie usate dai [[Parser top-down|parser top-down]] per calcolare i simboli di [[Look-ahead|look-ahead]] ed eliminare quindi il nondeterminismo.

## First
> Data una [[Grammatiche libere|grammatica libera]] $G$ e $\alpha \in (T \cup NT)^{*}$ diciamo che $\text{First}(\alpha)$ è l'_insieme dei terminali che possono stare in prima posizione in una stringa che si deriva da $\alpha$_.
> Formalmente
> - per $a \in T$ si ha che $$a \in \text{First}(\alpha) \iff \alpha \implies^{*} a\beta$$ per $\beta \in (T \cup NT)^{*}$;
> - se $\alpha \implies^{*} \epsilon$ allora $\epsilon \in \text{First}(\alpha)$.

Per esempio, se consideriamo le produzioni
$$A \to \alpha_{1} | \alpha_{2}$$
e se calcoliamo che
$$\text{First}(\alpha_{1}) \cap \text{First}(\alpha_{2}) = \varnothing$$
allora significa che **con 1 simbolo di look-ahead posso scegliere in modo deterministico la produzione corretta**!

Le produzioni
$$A \to aB | bc$$
hanno come first
- $\text{First}(aB) = \{a\}$
- $\text{First}(bc) = \{b\}$

e $\{a\} \cap \{b\} = \varnothing$. Infatti _con un solo simbolo di look-ahead posso scegliere deterministicamente la produzione da sviluppare_!

Tuttavia **solo il first puo' non bastare**: ci sono casi in cui e' necessario conoscere cosa segue un nonterminale, ossia i follow!

### Calcolo
Considera $N(G) \subseteq NT$ l'insieme dei [[Produzioni epsilon#Simbolo annullabile|simboli annullabili]] della grammatica $G$. Allora calcoliamo i first come segue:
- per ogni $x \in T$, $\text{First}(x) = \{x\}$;
- per ogni $X \in NT$, inizializza $\text{First}(X) = \varnothing$;
	- ripeti il seguente ciclo finche' nessun $\text{First}(X)$ viene piu' modificato in un'iterazione
		- per ogni produzione $X \to Y_{1}\cdots Y_{k}$
			- per ogni $i$ da $1$ a $k$
				- se $i = 1$ o $(Y_{1}, \cdots, Y_{i-1} \in N(G))$
					- $\text{First}(X) := \text{First}(X) \cup (\text{First}(Y_{i}) \setminus \{\epsilon\})$
- per ogni $X \in N(G)$, $\text{First}(X) := \text{First}(X) \cup \{\epsilon\}$

e quindi si puo' estendere $\text{First}$ a $\alpha \in (T \cup NT)^{*}$ come segue:
- $\text{First}(\epsilon) = \{\epsilon\}$;
- $\text{First}(X\beta) = \text{First}(X)$ se $X \notin N(G)$;
- $\text{First}(X\beta) = (\text{First}(X) \setminus \{\epsilon\}) \cup \text{First}(\beta)$ se $X \in N(G)$.

Nella pratica, se $A \to \alpha_{1}|\cdots|\alpha_{k}$, allora
$$\text{First}(A) = \text{First}(\alpha_{1}) \cup \cdots \cup \text{First}(\alpha_{k})$$

#### Esempi
Consideriamo la grammatica
$$S \to Ab | c \ \ \ \ \ A \to aA | \epsilon$$
e calcoliamo
- $\text{First}(S) = \text{First}(Ab) \cup \text{First}(c) = (\text{First}(A) \setminus \{\epsilon\}) \cup \text{First}(b) \cup \{c\} = \{a\} \cup \{b\} \cup \{c\} = \{a, b, c\}$;
- $\text{First}(A) = \text{First}(aA) \cup \text{First}(\epsilon) = \{a\} \cup \{\epsilon\} = \{a, \epsilon\}$.

## Follow
> Data una grammatica libera $G$ e $A \in NT$, diciamo che $\text{Follow}(A)$ e' l'_insieme dei terminali che possono comparire immediatamente a destra di $A$ in una forma sentenziale_.
> Formalmente
> - per $a \in T$ si ha che $$a \in \text{Follow}(A) \iff S \implies^{*} \alpha Aa\beta$$
>   per $\alpha, \beta \in (T \cup NT)^{*}$;
> - \$ $\in \text{Follow}(A)$ se $S \implies^{*} \alpha A$ (e quindi poiche' $S \implies^{*} S$ allora \$ $\in \text{Follow}(S)$).

### Calcolo
La procedura per calcolare i follow di ogni $X \in NT$ e' la seguente:
- per ogni $X \in NT$ inizializza $\text{Follow}(X) = \varnothing$;
- $\text{Follow}(S) = \$$;
- ripeti questo ciclo finche' nessun $\text{Follow}(X)$ viene piu' modificato in un'iterazione:
	- per ogni produzione $X \to \alpha Y \beta$
		- $\text{Follow}(Y) := \text{Follow}(Y) \cup (\text{First}(\beta) \setminus \{\epsilon\})$;
	- per ogni produzione $X \to \alpha Y$ e per ogni produzione $X \to \alpha Y \beta$ con $\epsilon \in \text{First}(\beta)$
		- $\text{Follow}(Y) := \text{Follow}(Y) \cup \text{Follow}(X)$;

#### Esempio
Consideriamo la grammatica
$$S \to ABC \ \ \ \ \ A \to aaA|\epsilon \ \ \ \ \ B \to b | \epsilon \ \ \ \ \   C \to cC|\epsilon$$
e calcoliamo sia i first che i follow:

|     | $\text{First}$      | $\text{Follow}$ |
| --- | ------------------- | --------------- |
| $S$ | $a, b, c, \epsilon$ | $\$$            |
| $A$ | $a, \epsilon$       | $b, c, \$$      |
| $B$ | $b, \epsilon$       | $c, \$$         |
| $C$ | $c, \epsilon$       | $\$$            |

## Generalizzazione a $k$ caratteri
Le definizioni fornite fino ad adesso di first e follow lavorano esclusivamente sui primi caratteri delle forme sentenziali. Quindi consentono di costruire solo [[Tabella di parsing LL(1)|tabelle di parsing]] $LL(1)$... ma per grammatiche piu' complesse, come le [[Grammatiche LL(k)|grammatiche]] $LL(k)$, e' necessario fornire una definizione piu' generale di first e follow, per ogni $k$ caratteri.

### $\text{First}_{k}$
> Data $\alpha \in (T \cup NT)^{*}$, allora
> $$w \in \text{First}_{k}(\alpha) \iff \alpha \implies^{*}w\beta$$
> con $|w| = k, w \in T^{*}, \beta \in (T \cup NT)^{*}$ oppure
> $$w \in \text{First}_{k}(\alpha) \iff \alpha \implies^{*}w$$
> con $|w| \leq k, w \in T^{*}$.

### $\text{Follow}_{k}$
> Dato un nonterminale $A \in NT$, allora
> $$w \in \text{Follow}_{k}(A) \iff S \implies^{*} \alpha A w \beta$$
> con $|w| = k, w \in T^{*}, \alpha, \beta \in (T \cup NT)^{*}$ oppure
> $$w \in \text{Follow}_{k}(A) \iff S \implies^{*} \alpha A w$$
> con $|w| \leq k, w \in T^{*}, \alpha \in (T \cup NT)^{*}$.

## Referenze