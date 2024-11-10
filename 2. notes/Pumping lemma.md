---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 28-10-2024 11:07:40
links:
  - "[[Lecture 15102024110302]]"
  - "[[Lecture 17102024120438]]"
---
# Pumping lemma
---
## Introduzione
Come facciamo a distinguere i [[Linguaggio regolare|linguaggi regolari]] da quelli non-regolari? Esiste una proprietà unica dei linguaggi regolari che non hanno quelli non-regolari?

Partiamo da un esempio.
Il linguaggio
$$L = \{a^{n}b^{n} | n \geq 0\}$$
è [[Linguaggio libero|libero]], infatti è [[Linguaggio generato|generato]] dalla [[Grammatiche libere|grammatica libera]]
$$S \to \epsilon | aSb$$

Si dimostra che è libero ma non regolare[^1]. Intuitivamente, se è regolare allora esiste un [[Automa a stati finiti|automa a stati finiti]] in grado di [[Linguaggio accettato|accettare]] il linguaggio. Questo automa, pensandoci, deve leggere $n$ volte $a$, e non appena trova una $b$, leggere esattamente $n$ volte $b$. Questo _richiede che l'automa sia composto da infiniti stati_:
![[automa-stati-infiniti.png]]

Per definizione, un [[NFA]]/[[DFA]] ha un numero di stati finito, per cui tale automa non esiste $\implies$ $L$ non può essere regolare[^2].

Invece il linguaggio
$$L = \{a^{n}b^{m} | n, m \geq 0\}$$
è regolare. Infatti è [[Linguaggio denotato da un'espressione regolare|denotato]] dall'[[Espressione regolare|espressione regolare]]
$$a^{*}b^{*}$$

Esiste il DFA associato:
![[dfa-linguaggio-regolare.png]]

## Teorema
> Il **pumping lemma** è una proprietà [[Algoritmo|algoritmica]] di tutti i linguaggio regolari. Formalmente dice che se $L$ è un linguaggio regolare, allora
> $$\exists N > 0. \forall z \in L : |z| \geq N. \exists u, v, w :$$
> - $z = uvw$
> - $|uv| \leq N$
> - $|v| \geq 1$
> - $\forall k \geq 0 \ \ \ uv^{k}w \in L$
> 
> Inoltre, si ha che $N \leq |Q_{\min}|$, dove $|Q_{\min}|$ è il numero di stati del [[Minimizzazione di DFA|DFA minimo]] che accetta $L$.

### Dimostrazione
Supponiamo $L$ linguaggio regolare, e fissiamo $N = |Q_{\min}|$, ossia il numero di stati del DFA minimo che accetta $L$ (notare che per forza $N > 0$).
Fissiamo $z \in L$ tale che
$$z = a_{1}a_{2} \cdots a_{m} \in L$$
con $m \geq N$.
Allora, per definizione di linguaggio accettato, esiste un cammino del DFA tale che partendo da $q_{0}$ e leggendo ogni carattere di $z$ arrivo a $q_{m} \in F$ (stato finale):
![[pumping-lemma-1.png]]

Il numero di stati attraversati è $m+1$, per cui $m+1 > N$. Ma sapendo che $N = |Q_{\min}|$, allora tra gli stati attraversati $q_{0}, \cdots, q_{m}$, per forza almeno due sono uguali. Formalmente
$$\exists i, j. \ i \neq j : q_{i} = q_{j}$$
ossia nel percorso di stati attraversati ne esistono almeno due che sono lo stesso stato. E queso è ovvio: alcuni stati devono per forza essere uguali, dato che se ne attraversa un numero strettamente maggiore di quanti ce ne sono! E' _importante notare che la ripetizione dello stato deve avvenire entro $N+1$ stati attraversati nella lettura di $z$_. In altri termini
$$0 \leq i < j \leq N$$
![[pumping-lemma-2.png]]

Quindi dallo stato $q_{0}$ leggo $i$ caratteri e arrivo allo stato $q_{i}$. Qui leggo dal carattere $a_{i+1}$ al carattere $a_{j}$, passando su $j-i$ stati ma "atterrando" sempre su $q_{i}$ ($= q_{j}$). Quindi leggo i restanti caratteri da $a_{j+1}$ fino a $a_{m}$, arrivando sullo stato finale $q_{m}$.

Questo ci consente di dimostrare il lemma. Infatti se consideriamo $u = a_{1} \cdots a_{i}$, $v = a_{i+1} \cdots a_{j}$, $w = a_{j+1} \cdots a_{m}$, allora si ha proprio
$$z = uvw$$

Sapendo che $j \leq N$, allora
$$|uv| = |a_{1} \cdots a_{i} \cdots a_{j}| = j \leq N$$
ossia sto leggendo i primi $j$ caratteri, per cui non posso superare $N$ stati!

Inoltre avendo $i \neq j$ e in particolare $i < j$, per forza
$$|v| \geq 1$$

Non ci resta che dimostrare di poter "pompare" $v$, ma questo deriva direttamente dalle proprietà dei DFA e dalle equivalenze regolari. Infatti:
- $k = 0$ devo dimostrare che $uv \in L$, ma è ovvio perché esiste il percorso di stati $q_{0}, \cdots, q_{i}=q_{j}, \cdots, q_{m}$ che accetta $uv$;
- $k > 0$ è ovvio, perché dallo stato $q_{i}=q_{j}$ posso ciclare $k$ volte e decidere poi di proseguire verso $q_{m}$;

**Qed**.

### Osservazioni
#### 1.
Se $L$ è finito non ho modo di scegliere una $z \in L$ tale che $|z| \geq N$, perché _il DFA minimo associato non conterrebbe cicli (ma solo diramazioni) e quindi non potrebbe riconoscere una stringa più lunga del numero dei suoi stati_. Data che la premessa è falsa, la tesi è vera.

#### 2.
Viceversa, se $\exists z \in L$ tale che $|z| \geq N$, allora il DFA associato riconosce per forza un linguaggio infinito (perché deve esistere un ciclo).

## Utilizzo
Il pumping lemma non lo usiamo per riconoscere se un linguaggio è regolare. Non sarebbe possibile logicamente. Al contrario, usiamo la _contronominale_ per dimostrare che se un linguaggio non è regolare.
$$\neg \text{pumping lemma} \implies \neg \text{linguaggio regolare}$$

### Contronominale
Negando il pumping lemma si ha:
$$
\begin{align*}
	\forall N > 0. \exists z \in L : |z| \geq N \\
	\forall u,v,w. \ (z = uvw \land |uv| \leq N \land |v| \geq 1 \implies \exists k \geq 0 : uv^{k}w \notin L) \\
	\implies L \text{ non è regolare}
\end{align*}
$$

In altre parole significa: _se per ogni automa che riconosca una stringa appartenente al linguaggio con lunghezza maggiore o uguale al suo numero di stati, se valgono i presupposti del pumping lemma ma esiste un $k$ per il quale non vale il "pompaggio", allora $L$ non è regolare_.

#### Esempio
##### 1.
Dimostriamo che
$$L = \{a^{n}b^{n} | n \geq 1\}$$
non è regolare.
Fissiamo un $N > 0$ e scegliamo $z = a^{N}b^{N}$, così da assicurare che $z \in L$ e $|z| \geq N$. Ora fisso $u, v, w$ tali che $z = uvw$, $|uv| \leq N$ e $|v| \geq 1$. Noto che $v$ può solo contenere $a$, allora dico $v = a^{j}$ con $j \geq 1$.
Non mi resta che determinare un $k \geq 0$ tale che $uv^{k}w \notin L$. Semplice, scelgo $k = 2$. Così facendo ho
$$uv^{2}w = uvvw = a^{N+j}b^{N} \notin L$$

##### 2.
Dimostriamo che
$$L = \{a^{n} | n \text{ è un quadrato perfetto}\} = \{a^{n^{2}} | n \geq 0\}$$
non è regolare
Fissiamo $N > 0$ e scegliamo $z = a^{N^{2}}$. A questo punto dalle condizioni $|uv| \leq N$ e $|v| \geq 1$, ricavo $1 \leq |v| \leq N$ (ovvio).
Scelgo allora $k = 2$, ossia la stringa $uv^{2}w$. Noto che
$$|z| = N^{2} < |uv^{2}w| = |z| + |v| \leq N^{2} + N < N^{2} + 2N + 1 = (N+1)^{2}$$
per cui ho dimostrato che
$$N^{2} < |uv^{2}w| < (N+1)^{2}$$
da cui
$$uv^{2}w \notin L$$

##### 3.
Dimostriamo che
$$L = \{a^{n} | n \text{ è una potenza del 2}\} = \{a^{2^{n}} | n \geq 0\}$$
non è regolare.
Fissiamo $N > 0$ e scegliamo $z = a^{2^{N}}$. Considero $z = uvw$, e dalle solite condizioni ricavo $1 \leq |v| \leq N$.
Scelgo $k = 2$, infatti
$$|z| = 2^{N} < |uv^{2}w| = |z| + |v| \leq 2^{N} + N < 2^{N} + 2^{N} = 2^{N+1}$$
per cui ho dimostrato che
$$2^{N} < |uv^{2}w| < 2^{N+1}$$
da cui
$$uv^{2}w \notin L$$

##### 4.
Dimostriamo che
$$L = \{ww | w \in \{a, b\}^{*}\}$$
non è regolare.
Fissiamo $N > 0$ e scegliamo $z = a^{N}b^{N}a^{N}b^{N}$. Considero $z = uvw$ e noto che $v$ può essere composto solo di $a$, allora suppongo $v = a^{j}$ con $j \geq 1$.
Scelgo $k = 2$, e ottengo
$$uv^{2}w = uvvw = a^{N+j}b^{N}a^{N}b^{N} \notin L$$

##### 5.
Dimostriamo che
$$L = \{ww^{R} | w \in \{a, b\}^{*}\}$$
non è regolare.
Fissiamo $N > 0$ e scegliamo $z = a^{N}b^{N}b^{N}a^{N} = a^{N}b^{2N}a^{N}$. Scompongo $z = uvw$ e noto che $v$ contiene solo $a$, quindi $v = a^{j}$ con $j \geq 1$.
Scelgo $k = 2$ e ottengo
$$uv^{2}w = uvvw = a^{N+j}b^{2N}a^{N} \notin L$$

##### 6.
Dimostriamo che
$$L = \{a^{n} | n \text{ è un numero primo}\}$$
non è regolare.
Fissiamo $N > 0$ e scegliamo $z = a^{p}$ con $p$ primo e $p \geq N+2$ (per evitare il 2). Scompongo $z = uvw$, $|uv| \leq N$ e $|v| \geq 1$. Deve essere $1 \leq |v| \leq N$.
Sia $m = |v|$, allora
$$|uv^{0}w| = |uw| = p - m$$
che deve essere primo se $uv^{0}w \in L$.
Ora consideriamo $k = p-m$:
$$|uv^{p-m}w| = |uw| + (p-m)|v| = (p-m) + (p-m)m = (p-m)(m+1)$$
che non è primo! Infatti $(m+1) \geq 2$ e $(p - m) \geq 2$.
Ottengo quindi che
$$uv^{p-m}w \notin L$$

## Referenze
[^1]: ricordando che i linguaggi regolari sono un sottoinsieme di quelli liberi.
[^2]: per via delle [[Equivalenze regolari|equivalenze regolari]].