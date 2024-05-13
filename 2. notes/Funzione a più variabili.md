---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 26-03-2024 17:27:50
links:
  - "[[Lecture 18032024130735]]"
---
# Funzione a più variabili
---
## Introduzione
> Una **funzione a più variabili** è una funzione matematica $f: A \to B$ dove $A \subseteq \mathbb{R}^{n}$ e $B \subseteq \mathbb{R}^{q}$, con $n, q \in \mathbb{N}$. Una qualunque funzione a più variabili $f$ è sempre riconducibile a due casi modello, per cui non è necessario studiare ogni $n, q$:
> 1. $f: \mathbb{R}^{n} \to \mathbb{R} = \mathbb{R}^{1}$ dette _funzioni scalari_;
> 2. $f: \mathbb{R} \to \mathbb{R}^{q}$ dette _cammini in $\mathbb{R}^{q}$_.

Si parte dal presupposto che una [[Funzione matematica|funzione]] è un concetto [[Insieme|insiemistico]], per cui parlare di funzioni in $\mathbb{R}^{n}$ (nello [[Spazio euclideo|spazio euclideo]]) è lecito.

## Grafico
Per studiare queste funzioni spesso e volentieri torna utile il [[Grafico di una funzione|grafico di una funzione]].

### Esempio
Per esempio prendiamo in esame la funzione $f: \mathbb{R}^{2} \to \mathbb{R}$ definita come
$$f(x, y) = x^{2}+y^{2}$$
allora il grafico $G(f)$ sarà
$$G(f) = \{(x, y, f(x, y)) | (x, y) \in \mathbb{R}^{2}\} = \{(x, y, x^{2}+y^{2}) | (x, y) \in \mathbb{R}^{2}\}$$

Per capire com'è fatto questo grafico lo intersechiamo prima con il piano $y, z$ definito dall'equazione $x = 0$, ovvero
$$G(f) \cap \{\text{piano y z}\} = \{(x, y, x^{2}+y^{2}) | (x, y) \in \mathbb{R}^{2}\} \cap \{x = 0\} = \{(0, y, y^{2}) | y \in \mathbb{R}\}$$
da cui otteniamo la parabola
$$z = y^{2}$$
Quindi lo intersechiamo anche con il piano $x, z$ definito dall'equazione $y = 0$, ovvero
$$G(f) \cap \{\text{piano x z}\} = \{(x, y, x^{2}+y^{2}) | (x, y) \in \mathbb{R}^{2}\} \cap \{y = 0\} = \{(x, 0, x^{2}) | x \in \mathbb{R}\}$$
da cui otteniamo la parabola
$$z = x^{2}$$

Graficamente parlando le due parabole si visualizzano nel piano tridimensionale nel seguente modo:
![[Drawing 2024-03-29 15.08.20.excalidraw|750]]

Perciò il grafico effettivo $G(f)$ non sarà altro che la rotazione delle due parabole sull'asse $z$. Di fatto è proprio
![[grafico-funzione-a-due-variabili.png]][^1]


## Curve di livello
Un altro modo per analizzare delle funzioni a più variabili è attraverso i suoi [[Insieme di livello|insiemi di livello]] associati alla [[Controimmagine|controimmagine]] per determinati punti $b$.

## Referenze
[^1]: funzioni di questo tipo si chiamano [[Funzione radiale|radiali]]