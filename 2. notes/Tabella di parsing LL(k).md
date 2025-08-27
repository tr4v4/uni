---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 27-08-2025 22:50:38
links:
  - "[[Lecture 12112024110924]]"
---
# Tabella di parsing LL(k)
---
## Introduzione
> La **tabella di parsing $LL(k)$** e' una generalizzazione per [[Grammatiche LL(k)|grammatiche]] $LL(k)$ della [[Tabella di parsing LL(1)|tabella di parsing]] $LL(1)$. Si tratta quindi di una [[Matrice|matrice]] usata dai [[Parser top-down|parser top-down]] per risolvere il nondeterminismo nei linguaggi $LL(k)$, usando i meccanismi di [[Look-ahead|look-ahead]] di [[First e follow|first e follow]] pero' su $k$ caratteri.
> Formalmente si tratta di una matrice bidimensionale $M$ in cui:
> - _le righe contengono i nonterminali $NT$_;
> - _le colonne contengono gli elementi solo strettamente necessari di $\{w \in T^{*} | |w| \leq k\}$[^1]_;
> - _ogni casella $(A, w)$ contiene le produzioni che possono essere scelte dal parser mentre tenta di espandere $A$ (sulla pila) e l'input corrente e' $a$_.

Quindi, **se ogni casella contiene al piu' una produzione, e non esistono $w_{1}, w_{2}$ tale che $w_{1}$ e' prefisso di $w_{2}$ con le caselle corrispondenti su una riga entrambe riempite, allora $G$ e' $LL(k)$**.

<u>Nota bene</u>: e' fondamentale la questione del prefisso! Prendiamo in esempio la seguente grammatica, con relativi $\text{First}_{2}$ e tabella di parsing $LL(2)$:
![[tabella-di-parsing-ll2.png]]
Questa non ha ovviamente conflitti. Tuttavia, possiamo notare che $c$ e' prefisso di $cc$, e quindi sullo stato $A$ il parser non e' piu' deterministico! Infatti se sull'input c'e' $cc$ potrebbe sia leggere solo $c$ e sviluppare la produzione $A \to c$, sia leggere $cc$ e produrre $A \to cA$.
Di conseguenza, $G_{1}$ non e' $LL(2)$!

## Riempimento
Semplicemente, per ogni produzione $A \to \alpha$, $M[A, w]$ contiene $A \to \alpha$ per ogni $w \in \text{First}_{k}(\alpha)$ ($w \neq \epsilon$) e per ogni $w \in \text{Follow}_{k}(A)$ se $\epsilon \in \text{First}_{k}(\alpha)$.

## Referenze

[^1]: le colonne sono tante quanti i $w$ che appartengono a $\text{First}_{k}(\alpha)$ per $A \to \alpha$ o a $\text{Follow}_{k}(A)$ per $A \to \alpha$ se $\epsilon \in \text{First}_{k}(\alpha)$.
