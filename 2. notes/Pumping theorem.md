---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 15-08-2025 19:37:31
links:
  - "[[Lecture 18102024090854]]"
---
# Pumping theorem
---
## Introduzione
Come per il [[Pumping lemma|pumping lemma]], il **pumping theorem viene usato al rovescio per dimostrare se un linguaggio non è libero**.

## Teorema
> Se $L$ è un [[Linguaggio libero|linguaggio libero]], allora $\exists N > 0$ tale che $\forall z \in L : |z| \geq N$, $\exists u, v, w, x, y$ tali che:
> - $z = uvwxy$
> - $|vwx| \leq N$
> - $|vx| \geq 1$
> - $uv^{k}wx^{k}y \in L \ \ \ \forall k \geq 0$

### Dimostrazione
Sia $G=(NT, T, R, S)$ una grammatica libera tale che $L = L(G)$. Sia ora $b$ il _massimo fattore di ramificazione in un [[Albero di derivazione|albero di derivazione]]_, ossia il numero massimo di simboli che compaiono nella parte destra di una produzione in $R$:
$$b = \max\{|\alpha| : A \to \alpha \in R\}$$
<u>Osservazione</u>: si assume $b \geq 2$, altrimenti la grammatica è banale.

Allora un albero di altezza $h$ (con 0 la radice) e fattore di ramificazione $b$, ha al più $b^{h}$ foglie, ossia $b^{h}$ caratteri che letti da sinistra a destra formano la stringa derivata.

Quindi fissiamo $N = b^{|NT|+1}$, così facendo, ogni albero di derivazione per una stringa $z$ tale che $|z| \geq N$ deve avere almeno un'altezza pari proprio a $|NT| + 1$.

Quindi prendiamo una stringa $z \in L$ tale che $|z| \geq N$ e consideriamo il suo albero di derivazione[^1]. Dalla lunghezza di $z$ sappiamo che:
- l'albero ha altezza $\geq |NT|+1$;
- esiste quindi un cammino da $S$ (radice) a una foglia con almeno $|NT|+2$ nodi;
- quel cammino attraversa $|NT|+1$ nodi interni etichettati con un nonterminale (solo la foglia, ultimo nodo, è un terminale);
- quindi, _almeno un nonterminale si ripete in quel cammino_.

Allora, la derivazione $S \implies^{*} z$ può essere divisa come
$$S \implies^{*} uAy \implies^{*} uvAxy \implies^{*} uvwxy$$

e quindi la derivazione $uAy \implies^{*} uvAxy$ può essere ripetuta più volte, o anche zero! O in altri termini abbiamo verificato che
$$uv^{k}wx^{k}y \in L \ \ \ \forall k \geq 0$$
![[pumping-theorem.png]]

Ci rimane da verificare gli ultimi vincoli:
- $|vwx| \leq N$, vero perché l'altezza dell'intero albero di derivazione è upperboundata da $|NT| + 1$, e quindi la sottostringa $uwx$ sarà composta da un numero di foglie non superiore a $b^{|NT|+1} = N$;
- $|vx| \geq 1$, ovvio, se entrambe le stringhe sono $\epsilon$, allora l'albero per $k = 0$ genererebbe sempre $z$ ($\epsilon^{0} = \epsilon$), ma avrebbe meno nodi, contraddicendo l'ipotesi di aver scelto l'albero più piccolo.

**Qed**.

## Contronominale
La sua versione contronominale è la seguente:
> $$\begin{align*}
	\forall N > 0. \exists z \in L : |z| \geq N \\
	\forall u,v,w, x, y. \ (z = uvwxy \land |vwx| \leq N \land |vx| \geq 1 \implies \exists k \geq 0 : uv^{k}wx^{k}y \notin L) \\
	\implies L \text{ non è libero}
\end{align*}$$

### Esempi
#### 1
Dimostriamo che il linguaggio
$$L = \{a^{n}b^{n}c^{n} | n \geq 0\}$$
non è libero usando il pumping theorem al rovescio.

Fissiamo un $N > 0$, e scegliamo $z = a^{N}b^{N}c^{N}$ ($\in L$) tale che $|z| \geq N$. Allora fissiamo $u,v,w,x,y$ tali che
- $z = uvwxy$;
- $|vwx| \leq N$;
- $|vx| \geq 1$;

Notiamo che le estremità della sottostringa $vwx$ non possono essere $a$ e $c$, altrimenti $|uwx| > N$. Quindi consideriamo i seguenti casi:
- $vwx$ non contiene $a$, ovvero tutte le $a$ stanno in $u$ $\implies$ per $k=2$ ho $uv^{2}wx^{2}y$ che contiene sicuramente un numero diverso di $b$ e $c$ ma non di $a$!
- $vwx$ non contiene $c$, ovvero tutte le $c$ stanno in $y$ $\implies$ per $k=2$ ho $uv^{2}wx^{2}y$ che contiene sicuramente un numero diverso di $a$ e $b$ ma non di $c$!

Di conseguenza, in ogni caso vale $uv^{2}wx^{2}y \notin L$.

#### 2
Dimostriamo la non-libertà del linguaggio
$$L = \{a^{n}b^{m}a^{n}b^{m} | n, m \geq 0\}$$

Fissiamo un $N > 0$, e scegliamo $z = a^{N}b^{N}a^{N}b^{N}$, appartenente al linguaggio e tale che $|z| \geq N$. Allora, fissati $u,v,w,x,y$ tali che valgano le 3 proprietà, notiamo che la sottostringa $vwx$ può essere:
- $vwx \in a^{*} \lor vwx \in b^{*}$;
- $vwx \in a^{*}b^{*} \lor vwx \in b^{*}a^{*}$;

Nel primo caso, è ovvio che scegliendo $k = 2$ la stringa $uv^{2}wx^{2}y \notin L$, infatti avrei un numero di $a$ diverso da $N$ (numero di $a$ del primo gruppo di $a$), e lo stesso si applica per $b$.
Nel secondo caso, ugualmente, scegliendo $k=2$ la stringa $uv^{2}wx^{2}y \notin L$. Infatti si aggiungerebbe un numero di $a$ e $b$ che differirebbe dal numero di $a$ e $b$ dell'altro blocco.

## Referenze

[^1]: se la grammatica è [[Grammatica ambigua|ambigua]] e quindi ce n'é più di uno prendiamo quello col minor numero di nodi.
