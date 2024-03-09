---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 27-10-2023 19:56:23
links:
  - "[[Lecture 27102023135003]]"
---
# Classe C
---
## Definizione
> Definiamo [[Classe|classe]] $C^{k}$ l'insieme di tutte le funzioni $f^{k}$ _[[Funzioni continue|continue]]_ su $I$ e _[[Funzioni derivabili|derivabili]]_ $k$-volte su $I$:
> $$f \in C^{k}(I) \iff \begin{cases} f \text{ è derivabile } k \text{-volte su } I \\ f^{k} \text{ è continua su } I \end{cases}$$

<u>Nota bene</u>: il motivo per cui solo $f^{k}$ (ovvero _l'ultima derivata_) si richiede essere continua è perché le precedenti [[Funzioni derivabili#Rapporto con la continuità|essendo derivabili sono automaticamente continue]].

## Composizione
Avremo quindi che:
- $C^{0}(I) = \{f: I \to \mathbb{R} | f \text{ continua su I}\}$
	- da cui infatti abbiamo che tutte le funzioni continue su tutto il dominio $I$ appartengono a $C^{0}$[^2]
- $C^{1}(I) = \{f: I \to \mathbb{R} | f' \text{ continua su I}\}$
- $C^{2}(I) = \{f: I \to \mathbb{R} | f'' \text{ continua su I}\}$
- ...
- $C^{\infty}(I) := \bigcap_{k} C^{k}$ ([[Definizione di intersezione#Intersezione _n_-aria|intersezione n-aria]] di tutte le classi $C^{k}$)

Vale quindi che
$$C^{k}(I) \subsetneqq C^{k-1}(I)$$
![[classe-c-k.png]]

## Conseguenze
> Dalla definizione di classe $C^{k}$ ne deriva che nel momento in cui **ci chiediamo se una funzione è derivabile**, **stiamo implicitamente chiedendo se la derivata di tale funzione è continua**.

## Applicazioni
Abbiamo per esempio che:
- $f(x) = |x| \longrightarrow f \in C^{0}(\mathbb{R}) \land f \notin C^{1}(\mathbb{R})$
- $f(x) = x|x| \longrightarrow f \in C^{1}(\mathbb{R}) \land f \notin C^{2}(\mathbb{R})$
- ...

## Referenze
[^2]: [[Funzioni continue#Regola]]