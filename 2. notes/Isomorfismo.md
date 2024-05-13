---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
  - topic/algebra-e-geometria
date: 02-12-2023 14:57:02
links:
  - "[[Lecture 30112023091742]]"
  - "[[Lecture 21032024111439]]"
  - "[[Lecture 09042024091802]]"
---
# Isomorfismo
---
## Introduzione
> Un **isomorfismo** tra due [[Strutture algebriche|strutture algebriche]] dello stesso tipo è un _[[Morfismo|morfismo]] dalla prima alla seconda che sia una [[Funzione biiettiva|funzione biiettiva]] la cui [[Funzione inversa|inversa]] sia anch'essa un morfismo_.

Nell'ambito dell'[[Algebra lineare|algebra lineare]] si ha che due [[Spazio vettoriale|spazi vettoriali]] $V, W$ si dicono isomorfi se esista un'[[Applicazione lineare|applicazione lineare]] $f: V \to W$ biiettiva (quindi sia iniettiva che suriettiva). Per cui un'applicazione lineare $f: V \to W$ se è [[Funzione inversa|invertibile]] è anche isomorfismo.

La proprietà fondamentale di due strutture isomorfe è che **è possibile trattarle come uguali**: tutte le operazioni effettuate su di una possono essere effettuate sull'altra, _a seconda di cosa sia più conveniente_[^1].

### Esempio
I due [[Left unital magma|left unital magma]] $(\mathbb{R}_{0}^{+}, +, 0)$ e $(\mathbb{R}^{+}, *, 1)$ hanno come funzione isomorfa $f(n) = e^{n}$, testimoniata dalla sua inversa $f(n) = \ln(n)$.

Come conseguenza fondamentale acquisisco che _invece che moltiplicare numeri molto grandi posso passare alla scala logaritmica e sommare numeri piccoli_.

## Proposizioni
### Dimensione
> Due spazi vettoriali $V, W$ si dicono isomorfi $\iff$
> $$\dim(V) = \dim(W)$$
> ovvero se hanno stessa [[Dimensione|dimensione]].

#### Dimostrazione
Primo verso dell'implicazione: suppongo che esista un $f: V \to W$ iniettiva e suriettiva, per cui $\ker(f) = \{\underline{0}\}$ e $\Im(f) = W$. Devo dimostrare $\dim(V) = \dim(W)$. Per il [[Teorema della dimensione|teorema della dimensione]] ho
$$\dim(V) = \dim(\ker(f)) + \dim(\Im(f))$$
perciò, avendo $\dim(\ker(f)) = 0$ e $\dim(\Im(f)) = \dim(W)$, ottengo proprio
$$\dim(V) = 0 + \dim(W) \iff \dim(V) = \dim(W)$$

Secondo verso dell'implicazione: suppongo $\dim(V) = \dim(W)$. Per il [[Teorema di esistenza e unicità di un'applicazione lineare|teorema di esistenza e unicità di un'applicazione lineare]], so che $\exists! f: V \to W | f(v_{1}) = w_{1}, \cdots, f(v_{n}) = w_{n}$ dove $\{v_{1}, \cdots, v_{n}\}$ è base di $V$ e $\{w_{1}, \cdots, w_{n}\}$ base di $W$; allora costruisco questa $f$ t.c. sia suriettiva e iniettiva.
Per dimostrare $f$ suriettiva mi riduco a dimostrare che $\dim(\Im(f)) = \dim(W)$, sfruttando [[Immagine di funzione#Spazio generato dell'immagine|questa proposizione]], per cui ho
$$\Im(f) = \langle f(v_{1}), \cdots, f(v_{n}) \rangle$$
e quindi per la definizione di $f$
$$\Im(f) = \langle w_{1}, \cdots, w_{n} \rangle$$
da cui, essendo $\{w_{1}, \cdots, w_{n}\}$ base di $W$, $\Im(f) = W$, e quindi $\dim(\Im(f)) = \dim(W) \implies f \text{ su}$.

Ora, per il [[Teorema della dimensione#Iniettività $ iff$ suriettività|corollario del teorema della dimensione]], avendo $\dim(V) = \dim(W)$ e $f$ suriettiva, automaticamente ho $f$ iniettiva. Perciò $f$ è biunivoca, e quindi un isomorfismo tra $V$ e $W$.

**Qed**.

## Referenze
[^1]: la [[Teoria della rappresentazione|teoria della rappresentazione]] si basa sull'isomorfismo