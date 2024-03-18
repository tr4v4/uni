---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 29-12-2023 19:33:12
links:
  - "[[Lecture 13122023131453]]"
---
# Teorema fondamentale dei morfismi
---
## Introduzione
> Il **teorema fondamentale dei morfismi** asserisce che per ogni [[Morfismo|morfismo]] $f: \mathcal{A} \to \mathcal{B}$ si ha che:
> 1. $\mathbb{A}_{/\sim_{f}}$ è il sostegno di una struttura algebrica dello stesso tipo;
> 2. $\mathbb{A}_{/\sim_{f}}$ è [[Isomorfismo|isomorfo]] a $Imm(f)$;
> 
> dove $p: \mathbb{A} \to \mathbb{A}_{/\sim_{f}}$ è la [[Definizione di proiezione|proiezione]] di $\mathbb{A}$ sulla [[Definizione di relazione di equivalenza indotta di un morfismo|relazione di equivalenza indotta]] del morfismo $f$.
> Equivalentemente è possibile dire che _c'è una corrispondenza [[Funzione biiettiva|biunivoca]] tra le [[Classe di equivalenza|classi di equivalenza]] di_ $\mathbb{A}_{/\sim_{f}}$ _e_ $Imm(f) \subseteq \mathbb{B}$.

Graficamente si produce il seguente schema:
![[Drawing 2023-12-29 21.26.53.excalidraw|800]]

e significa che possiamo trattare $\mathbb{A}_{/\sim_{f}}$ allo stesso modo di $Imm(f)$.

### Esempio
Prendiamo in esempio il [[Monoide|monoide]] $\mathcal{Z} = (\mathbb{Z}, *, 1)$, e la funzione $|\cdot|: \mathbb{Z} \to \mathbb{Z}$, che calcola il valore assoluto di un $z \in \mathbb{Z}$. Si ha che $|\cdot|$ è un morfismo per $\mathcal{Z}$ e se stesso, infatti:
1. $|1| = 1$
2. $\forall x, y. |x * y| = |x| * |y|$

Ora, per via dell'[[Immagine di morfismo|immagine di morfismo]] si ottiene che $Imm(|\cdot|) = \mathbb{N}$ è un sottomonoide di $\mathcal{Z}$.
Ma il risultato più importante si ha considerando il codominio della proiezione $\mathbb{Z}_{/\sim_{|\cdot|}}$, che ha esso stesso la struttura di monoide $(\mathbb{Z}_{/\sim_{|\cdot|}}, \circ, [1]_{\sim_{|\cdot|}})$ dove $[x]_{\sim_{|\cdot|}} \circ [y]_{\sim_{|\cdot|}} = [x*y]_{\sim_{|\cdot|}}$.

I due monoidi sono isomorfi, rispetto alla funzione $h(n) = \{-n, n\}$.

## Dimostrazione
L'idea alla base della dimostrazione sta nel costruire una funzione $g: \mathbb{A}_{/\sim_{f}} \to \mathbb{B}$ (nel disegno $i$) mostrando che è _iniettiva_ e _suriettiva_ restringendo il codominio a $Imm(f)$. In questo modo, ottenendo la _biiettività_, $g$ si definisce isomorfa.

## Referenze
- si usa anche per semplificare la visualizzazione del [[Codice di Hamming|codice di Hamming]]...!