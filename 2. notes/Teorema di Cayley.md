---
tags:
  - category/note
  - status/ongoing
  - topic/logica-per-informatica
date: 30-12-2023 13:32:56
links:
  - "[[Lecture 14122023092114]]"
---
# Teorema di Cayley
---
## Introduzione
> Il **teorema di Cayley** ci dice che _ogni [[Gruppo|gruppo]] di sostegno $\mathbb{A}$ è [[Isomorfismo|isomorfo]] a un [[Sottostruttura algebrica|sottogruppo]] del [[Gruppo di permutazioni|gruppo delle permutazioni]] $Perm(\mathbb{A})$_.
> Preso in esempio un generico gruppo $(\mathbb{Z}, +, 0, \cdot^{-1})$, la funzione $\pi_{\cdot}$ che mappa ogni elemento da $\mathbb{Z}$ a $Perm(\mathbb{Z})$ è un isomorfismo tra $(\mathbb{Z}, +, 0, \cdot^{-1})$ e un sottogruppo di $(Perm(\mathbb{Z}), \circ, id, \cdot^{-1})$.

### Esempio
Prendiamo in esempio un gruppo $\mathcal{A} = (\mathbb{A}, \circ, e, \cdot^{-1})$, quale sostegno è definito come
$$\mathbb{A} = \{R, G, B\}$$

E definiamo una funzione $\pi_{\cdot}: \mathbb{A} \to Perm(\mathbb{A})$ che mappa ogni elemento di $a \in \mathbb{A}$ a una permutazione $\pi_{a}$ di $Perm(\mathbb{A})$. In particolare definiamo il criterio di _traslatura_ rispetto ad $a$, del tipo:
- $\pi_{R}$ trasla di 0 tutti gli elementi di $\mathbb{A}$ ([[Funzione identità|funzione identità]] $id$)
- $\pi_{G}$ trasla di 1 tutti gli elementi di $\mathbb{A}$
- $\pi_{B}$ trasla di 2 tutti gli elementi di $\mathbb{A}$

Avremo quindi:
- $\pi_{R}: \{R, G, B\} \to \{R, G, B\}$
- $\pi_{G}: \{R, G, B\} \to \{B, R, G\}$
- $\pi_{B}: \{R, G, B\} \to \{G, B, R\}$

Come si vede dal grafico sottostante, si ottiene una corrispondenza [[Biiettività di una funzione|biunivoca]] tra ogni elemento di $\mathbb{A}$ e un sottoinsieme stretto di $Perm(\mathbb{A})$:
![[Drawing 2023-12-30 16.20.21.excalidraw|800]]

Per cui, in quanto $\pi_{\cdot}$ _isomorfa_, è possibile trattare $\mathcal{A}$ come il sottogruppo di permutazioni di $\mathbb{A}$, o in gergo:
$$(\mathbb{A}, \circ, e, \cdot^{-1}) \cong (Sub(Perm(\mathbb{A})), \bullet, id, \cdot^{-1})$$

## Dimostrazione
Fissiamo un gruppo $\mathcal{A} = (\mathbb{A}, \circ, e, \cdot^{-1})$. Definiamo $\pi_{\cdot}: \mathbb{A} \to Perm(\mathbb{A})$ come la funzione che mappa un elemento di $\mathbb{A}$ nella sua corrispondente permutazione in $Perm(\mathbb{A})$, in questo modo:
$$\pi_{a}(b) = a \circ b \ \ \ \ \ \ \ \ \ a, b \in \mathbb{A}$$
Questa funzione è da interpretare in questo modo: $a$ è un elemento statico, che determina la $a$-esima permutazione; $b$ rappresenta un qualunque elemento di $\mathbb{A}$ che viene permutato su $a$.

Per dimostrare che questa funzione sia un _isomorfismo_ tra $\mathcal{A}$ e il suo gruppo di permutazioni, dobbiamo:
- dimostrare che $\pi_{a}$ sia biiettiva, quindi sia [[Iniettività di una funzione|iniettiva]] che [[Suriettività di una funzione|suriettiva]]
- dimostrare che $\pi_{a}$ sia un morfismo tra $\mathcal{A}$ e il suo gruppo di permutazioni

### Biiettività
#### Iniettività
Per dimostrare l'iniettività di $\pi_{a}: \mathbb{A} \to Perm(\mathbb{A})$ dobbiamo verificare che
$$\pi_{a}(b) = \pi_{a}(c) \ \ \implies \ \ b = c$$

## Conseguenze
Come conseguenza fondamentale del teorema si ha che **ogni gruppo può essere visto come un gruppo di permutazioni**.

## Referenze