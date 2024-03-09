---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 07-10-2023 10:55:57
links:
  - "[[Lecture 06102023134057]]"
---
# Dimostrazione successioni monotone hanno limite
---
## Introduzione
Ricordando le definizioni di [[Successione monotona|successioni monotone]] e di [[Estremo superiore|sup]] e [[Estremo inferiore|inf]], dobbiamo dimostrare che per una successione _crescente_ si avrà
$$\lim_{n \to +\infty} a_{n} = \sup \{a_{n} | n \in \mathbb{N}\}$$

e che invece per una successione _decrescente_ vale
$$\lim_{n \to +\infty} a_{n} = \inf \{a_{n} | n \in \mathbb{N}\}$$

## Dimostrazioni
### Crescente
Vogliamo dimostrare che se la successione è crescente il suo limite è il suo _estremo superiore_. Ovvero
$$L := \sup \{a_{n} | n \in \mathbb{N}\}$$

Per cui coesistono due casi:
- $L = +\infty$
- $L \in \mathbb{R}$

#### $L = +\infty$
In questo caso stiamo dicendo che l'insieme degli elementi della successione ($A$) non ammette [[Maggiorante|maggioranti]], per cui **non è superiormente limitato**.

Si tratta allora di provare
$$\lim_{n \to +\infty} a_{n} = +\infty$$

Applicando la definizione di [[Limite di successione|limite]] otteniamo
$$\forall k \in R_{+} : \exists \delta > 0 : \forall n > \delta : a_{n} \geq k$$

Per la definizione stessa di $A$, non ammettendo maggioranti non esisterà mai un valore di $k$ superiore a un generico $a_{n}$. Per cui, per quanto grande possa essere $k$, ad ogni modo vale che
$$\exists a_{\bar{n}} : a_{\bar{n}} > k$$

Ovvero troviamo sempre un numero più grande di $k$ (appunto $a_{\bar{n}}$).

Ora, essendo $a_{n} \uparrow$ avremo che
$$\forall n > \bar{n}, \ a_{n} \geq a_{\bar{n}} > k$$

Per cui si comunque $a_{n}$, essendo crescente, supera $k$. **Cvd**.

#### $L \in \mathbb{R}$
In quest'altro caso invece l'insieme degli elementi della successione $A$ ammette maggioranti, per cui è superiormente limitato.

Si tratta di provare
$$\lim_{n \to +\infty} a_{n} = L$$

Ovvero dalla definizione
$$\forall \epsilon > 0: \exists \delta \in \mathbb{R}_{+} : \forall n > \delta : |a_{n} - L| < \epsilon$$

Estendendola dobbiamo provare
$$L - \epsilon < a_{n} < L + \epsilon$$

Considerando $L + \epsilon > a_{n}$ il risultato è automatico: sapendo che $L$ è $\sup$ e quindi il minimo dei maggioranti, allora $L + \epsilon$ sarà per forza un maggiorante, per cui maggiore di $a_{n}$ qualunque valore esso sia.

Considerando invece $L - \epsilon < a_{n}$, dobbiamo trovare un valore per il quale valga la disequazione. Sapendo che $L$ è $\sup$, concludiamo che $L - \epsilon$ non può essere un maggiorante di $A$. Per cui dovrà esistere un valore $a_{\bar{n}} > L - \epsilon$, dal quale si ricava $\delta = \bar{n}$. Unendo ciò al fatto che $a_{n}$ è crescente, avremo
$$L - \epsilon < a_{\bar{n}} \leq a_{n}$$

Da questo si ricava ovviamente $L - \epsilon < a_{n}$. **Cvd**.

### Decrescente
Vogliamo dimostrare che se la successione è decrescente il suo limite è il suo _estremo inferiore_. Ovvero
$$L := \inf \{a_{n} | n \in \mathbb{N}\}$$

Per cui coesistono due casi:
- $L = -\infty$
- $L \in \mathbb{R}$

#### $L = -\infty$
In questo caso stiamo dicendo che l'insieme degli elementi della successione ($A$) non ammette [[Minorante|minoranti]], per cui **non è inferiormente limitato**.

Si tratta allora di provare
$$\lim_{n \to +\infty} a_{n} = -\infty$$

Applicando la definizione di [[Limite di successione|limite]] otteniamo
$$\forall k \in R_{+} : \exists \delta > 0 : \forall n > \delta : a_{n} \leq k$$

1. $A$ non ammette minoranti
2. quindi $k$ non è un minorante
3. allora $\exists a_{\bar{n}} : a_{\bar{n}} < k$
4. $a_{n} \downarrow \implies \forall n > \bar{n}, \ a_{n} \leq a_{\bar{n}}$
5. da cui $a_{n} \leq k$

**Cvd**.

#### $L \in \mathbb{R}$
In quest'altro caso invece l'insieme degli elementi della successione $A$ ammette minoranti, per cui è inferiormente limitato.

Si tratta di provare
$$\lim_{n \to +\infty} a_{n} = L$$

Ovvero dalla definizione
$$\forall \epsilon > 0: \exists \delta \in \mathbb{R}_{+} : \forall n > \delta : |a_{n} - L| < \epsilon$$

Estendendola dobbiamo provare
$$L - \epsilon < a_{n} < L + \epsilon$$

Considerando $L - \epsilon < a_{n}$ il risultato è automatico: sapendo che $L$ è $\inf$ e quindi il massimo dei minoranti, allora $L - \epsilon$ sarà per forza un minorante, per cui minore di $a_{n}$ qualunque valore esso sia.

Considerando invece $L + \epsilon > a_{n}$, dobbiamo trovare un valore per il quale valga la disequazione. Sapendo che $L$ è $\inf$, concludiamo che $L + \epsilon$ non può essere un minorante di $A$. Per cui dovrà esistere un valore $a_{\bar{n}} < L + \epsilon$, dal quale si ricava $\delta = \bar{n}$. Unendo ciò al fatto che $a_{n}$ è decrescente, avremo
$$a_{n} \leq a_{\bar{n}} < L + \epsilon$$

Da questo si ricava ovviamente $L + \epsilon > a_{n}$. **Cvd**.

## Corollario
Per questo teorema vale allora che
> - $a_{n} \nearrow$ e _superiormente limitata_ $\implies$ $a_{n}$ **convergente** a $\sup$
> - $a_{n} \searrow$ e _inferiormente limitata_ $\implies$ $a_{n}$ **convergente** a $\inf$

## Referenze