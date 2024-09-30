---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 11-05-2024 15:47:58
links:
  - "[[Lecture 06052024131425]]"
  - "[[Lecture 09052024141025]]"
  - "[[Lecture 10052024144525]]"
---
# Forma quadratica
---
## Introduzione
> Sia $A \in M_{n}(\mathbb{R})$ una [[Matrice|matrice]] quadrata [[Matrice simmetrica|simmetrica]], ovvero tale che $A = A^{T}$, allora si definisce **forma quadratica** la funzione $q_{A} : \mathbb{R}^{n} \to \mathbb{R}$ definita come
> $$q_{A}(h) = <Ah, h> \in \mathbb{R}$$
> ovvero come il [[Prodotto scalare|prodotto scalare]] tra $Ah$ e $h$ stesso.

### Esempio
Presa $A = \begin{pmatrix}2 & 5 \\ 5 & 1\end{pmatrix}$, simmetrica, si ha
$$q_{A} = <\begin{pmatrix}2 & 5 \\ 5 & 1\end{pmatrix} \cdot (h_{1}, h_{2}), (h_{1}, h_{2})> = <(2h_{1} + 5h_{2}, 5h_{1} + h_{2}), (h_{1}, h_{2})> = 2h_{1}^{2} + 10h_{1}h_{2} + h_{2}^{2}$$

## Casi generali
### $n = 2$
> Per matrici $A \in M_{2}(\mathbb{R})$ simmetriche del tipo $A = \begin{pmatrix}a & b \\ b & c\end{pmatrix}$, la loro forma quadratica $q_{A}$ si definisce sempre come
> $$q_{A}(h) = ah_{1}^{2} + ch_{2}^{2} + 2bh_{1}h_{2}$$

<u>Nota bene</u>: lungo la diagonale ci sono i coefficienti moltiplicati per i quadrati di $h$, ossia $a$ e $c$.

#### Esempio
Possiamo, dato un polinomio di 2° grado, ricavare sempre la sua matrice associata. Si pensi a $p(h) = 3h_{1}^{2} + \frac{1}{3}h_{1}h_{2} - 7h_{2}^{2}$. Usando a ritroso la formulazione precedente possiamo ottenere la sua matrice $A$:
$$A = \begin{pmatrix}3 & \frac{1}{6} \\ \frac{1}{6} & -7\end{pmatrix}$$

### $n = 3$
Allo stesso modo per $n = 3$, preso il polinomio $p(h) = h_{1}^{2} - 3h_{3}^{2} + 3h_{1}h_{2} - 5h_{1}h_{3}$ possiamo scrivere la matrice associata $A$ come
$$A = \begin{pmatrix}1 & \frac{3}{2} & - \frac{5}{2} \\ \frac{3}{2} & 0 & 0 \\ - \frac{5}{2} & 0 & -3\end{pmatrix}$$

### $\forall n$
Per un $n$ qualsiasi vale
> $$q_{A}(h) = <Ah, h> = \sum\limits_{j=1}^{n}\left(\sum\limits_{k=1}^{n} A_{jk}h_{k}\right)h_{j} = \sum\limits_{j, k = 1}^{n} A_{jk}h_{j}h_{k}$$

## Segno
Una proprietà importante che si studia delle forme quadratiche è il loro **segno**. In particolare si ha che:
> Sia $A \in M_{n}(\mathbb{R})$ simmetrica ($A = A^{T}$), allora si dice che:
> 1. $A$ è _definita positiva_ se $<Ah, h> > 0 \ \ \forall h \neq \underline{0}$
> 2. $A$ è _definita negativa_ se $<Ah, h> < 0 \ \ \forall h \neq \underline{0}$
> 3. $A$ è _indefinita_ se $\exists h', h'' \in \mathbb{R}^{n}$ tali che $<Ah', h'> < 0 < <Ah'', h''>$

<u>Osservazione</u>: sono tutte disuguaglianze strette.

<u>Nota bene</u>: _può succedere che $A$ non soddisfi nessuna delle 3 proprietà_, in tal caso $A$ si dice _non definita_.

Sul segno di una forma quadratica si può ottenere una vera e propria [[Classificazione forme quadratiche|classificazione]].

### Esempi
#### $A > 0$
Presa $A = \begin{pmatrix}1 & 0 \\ 0 & 3\end{pmatrix}$ si ha che $q_{A}(h) = h_{1}^{2} + 3h_{2}^{2}$, e perciò che $q_{A}(h) > 0 \ \ \forall h \neq 0$: $A$ è definita positiva.

#### $A < 0$
Presa $A = \begin{pmatrix}-2 & 0 \\ 0 & -3\end{pmatrix}$ si ha che $q_{A}(h) = -2h_{1}^{2} - 3h_{2}^{2}$, ossia $q_{A}(h) < 0 \ \ \forall h \neq 0$: $A$ è definita negativa.

#### $A$ indefinita
Presa $A = \begin{pmatrix}1 & 0 \\ 0 & -2\end{pmatrix}$ si ha che $q_{A}(h) = h_{1}^{2} - 2h_{2}^{2}$, e prendendo due appositi $h', h''$ si scopre che $A$ è indefinita.

## Proprietà
### 1
> Sia $A \in M_{n}(\mathbb{R})$ simmetrica e definita positiva ($A > 0$), allora
> $$\exists \lambda > 0 : \ \ \forall h \in \mathbb{R}^{n} \ <Ah, h> \geq \lambda |h|^{2}$$

<u>Osservazione</u>: dal [[Teorema spettrale|teorema spettrale]] ricordiamo che $A = A^{T}$ ammette una famiglia di [[Autovalore|autovalori]] con corrispondenti [[Autovettore|autovettori]] [[Ortogonalità|ortogonali]]. Si verifica che $\lambda$ può essere scelto come il più piccolo degli autovalori (autovalore minimo), ed essendo $A$ definita positiva tutti i suddetti sono positivi.

<u>Osservazione</u>: se $h \neq \underline{0}$ si ha $$<Ah, h> \geq \lambda |h|^{2} \iff \frac{<Ah, h>}{|h|^{2}} \geq \lambda \iff <A \frac{h}{|h|}, \frac{h}{|h|}> \geq \lambda$$
ed essendo $v = \frac{h}{|h|}$ un [[Vettore|vettore]] [[Normalizzazione|normalizzato]] si ha equivalentemente che
$$<Av, v> \geq \lambda > 0 \ \ \forall v, |v| = 1$$

E' importante notare che quest'affermazione è più forte dell'ipotesi di $A$ definita positiva, ossia
$$<Ah, h> > 0 \ \ \forall h \neq \underline{0}$$
perché stiamo definendo un limite $\lambda > 0$ sotto la quale la forma quadratica non può andare.

#### Dimostrazione
Dimostriamo la proposizione in $\mathbb{R}^{2}$, in modo da sfruttare le [[Coordinate polari|coordinate polari]].
Scriviamo $v \in \mathbb{R}^{2}$ di [[Norma euclidea|norma]] unitaria come
$$v = (\cos{\theta}, \sin{\theta})$$
con $\theta \in [0, 2\pi]$.

Denotiamo $A = \begin{pmatrix}a & b \\ b & c\end{pmatrix}$ tale che sia definita positiva, ossia (per la [[Classificazione forme quadratiche|classificazione delle forme quadratiche]]) $a > 0$ e $\det(A) > 0$.
Devo dimostrare
$$\exists \lambda > 0 : <Av, v> \geq \lambda \ \ \forall v = (\cos{\theta}, \sin{\theta})$$

Allora sviluppiamo il prodotto scalare come
$$<Av, v> = a\cos^{2}{\theta} + 2b\cos{\theta}\sin{\theta} + c\sin^{2}{\theta} := g(\theta)$$

Ora sappiamo, per ipotesi, che $g(\theta) > 0 \ \ \forall \theta [0, 2\pi]$ e che:
- $[0, 2\pi]$ è un intervallo chiuso e limitato;
- $g$ è continua (perché composizione di funzioni continue).

Allora per il [[Teorema di Weierstrass|teorema di Weierstrass]] si ha che
$$\exists \bar{\theta} \in [0, 2\pi] : g(\theta) \geq g(\bar{\theta}) \ \ \forall \theta \in [0, 2\pi]$$
ossia che esiste un [[Massimo e minimo assoluto|punto di minimo assoluto]] $\bar{\theta}$.

Allora troviamo che
$$\lambda = g(\bar{\theta}) > 0$$
infatti
$$<Av, v> \geq g(\theta) = \lambda > 0 \ \ \forall v = (\cos{\theta}, \sin{\theta}), \theta \in [0, 2\pi]$$

**Qed**.

## Referenze
- [[Forma quadratica hessiana]]