---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 29-12-2023 17:47:02
links:
  - "[[Lecture 13122023131453]]"
---
# Immagine di morfismo
---
## Introduzione
> Sia $f$ un [[Morfismo|morfismo]] da una [[Strutture algebriche|struttura algebrica]] $\mathcal{A}$ a un'altra $\mathcal{B}$. Si ha che l'[[Immagine di funzione|immagine]] $Imm(f)$ è una [[Sottostruttura algebrica|sottostruttura]] di $\mathcal{B}$.

## Dimostrazione
Prendiamo in considerazione due [[Monoide|monoidi]] $\mathcal{A} = (\mathbb{A}, \circ, a)$ e $\mathcal{B} = (\mathbb{B}, \bullet, b)$. Preso un morfismo $f: \mathcal{A} \to \mathcal{B}$ dobbiamo dimostrare che $Imm(f)$ è una sottostruttura algebrica di $\mathcal{B}$. Ovvero:
- tutte le costanti di $\mathcal{B}$ devono essere in $Imm(f)$;
- $Imm(f)$ dev'essere un [[Sottoinsieme chiuso|sottoinsieme chiuso]] rispetto a tutte le operazioni di $\mathcal{B}$

### Costanti
L'unica costante in $\mathcal{B}$ è $b$, ovvero l'[[Elemento neutro|elemento neutro]]. Dobbiamo assicurarci che $b \in Imm(f)$, ovvero $b \in \{y \in \mathbb{B} | \exists x. f(x) = y\}$. Prendiamo $a$ (l'elemento neutro di $\mathcal{A}$), e per la definizione di morfismo sappiamo che $f(a) = b$, per cui esiste un $x$ (proprio $a$) che viene mappato in $b$, quindi $b \in Imm(f)$.

**Qed**.

### Operazioni
L'unica operazione di $\mathcal{B}$ è $\bullet$. Dobbiamo assicurarci che $\forall y_{1}, y_{2} \in Imm(f). y_{1} \bullet y_{2} \in Imm(f)$. Essendo $y_{1}$ e $y_{2}$ in $Imm(f)$, ci saranno $x_{1}$ e $x_{2}$ tali che $f(x_{1}) = y_{1}$ e $f(x_{2}) = y_{2}$. Per la definizione di morfismo, allora, si ha che $f(x_{1} \circ x_{2}) = f(x_{1}) \bullet f(x_{2}) = y_{1} \bullet y_{2}$. Prendiamo $x_{3} = x_{1} \circ x_{2}$. Essendo $\mathcal{A}$ un monoide, siamo sicuri che $x_{3} \in \mathbb{A}$. Quindi esiste un elemento di $\mathcal{A}$ (proprio $x_{3}$) mappato in $y_{1} \bullet y_{2}$, e perciò $y_{1} \bullet y_{2} \in Imm(f)$.

**Qed**.

## Esempio
Presi i due monoidi $(\mathbb{N}, +, 0)$ e $(\mathbb{N}, *, 1)$ e il morfismo $f(n) = 2^{n}$, si ottiene che $Imm(f)$ è l'insieme delle potenze del 2, tale che $(Imm(f), *, 1)$ è un sottomonoide di $(\mathbb{N}, *, 1)$.

## Referenze