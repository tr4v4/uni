---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 05-10-2024 20:25:00
links:
  - "[[Lecture 01102024110253]]"
---
# Semantica operazionale strutturata
---
## Introduzione
Una volta che si è definita la [[Sintassi|sintassi]] di un [[Linguaggio di programmazione|linguaggio di programmazione]], attraverso le [[Grammatiche libere|grammatiche libere]], bisogna darle un significato: si fa con la [[Semantica|semantica]] ([[Semantica dinamica|dinamica]]).

In particolare uno dei due modi per definire la semantica è quello operazionale, che attraverso una specie di automa mostra l'effetto dell'esecuzione delle varie istruzioni.

> La **semantica operazionale strutturata** (o **S.O.S.**) è allora il _modello matematico che fornisce significato semantico alla sintassi di un linguaggio di programmazione_ (descritta da grammatica libera).

## Funzionamento
Per capire come opera la semantica operazione strutturata, _descriviamo la semantica di un semplice linguaggio esempio definito da grammatica libera_.

### Sintassi
La sintassi del linguaggio è composta da:
- _insieme di base_
- _insiemi derivati_

#### Insieme di base
Sono: 
- _booleani_: $\{\text{tt}, \text{ff}\}$, con metavariabili $t, t_{1}, t' \in \mathbb{B}$
- _[[Numeri naturali|naturali]]_: $\{0, 1, 2, \cdots\}$, con metavariabili $n, m, p \in \mathbb{N}$
- _variabili_: $\{a, b, c, \cdots, z\}$ (numero finito), con metavariabili $v \in \text{Var}$

#### Insiemi derivati
Definiti in grammatiche libere, sono:
- _espressioni aritmetiche_ $e \in \text{Exp}$: $e ::= m|v|e+e|e-e|e*e$, dove $m \in \mathbb{N}$ e $v \in \text{Var}$
- _espressioni booleane $b \in \text{Bexp}$_: $b ::= t|e=e|b \lor b| \neg b$
- _comandi $c \in \text{Com}$_: $c ::= \text{skip}|v:=e|c;c|\text{while b do c}|\text{if b then c else c}$

<u>Nota bene</u>: _tutte queste grammatiche sono fortemente [[Grammatica ambigua|ambigue]], ma scrivere la [[Sintassi concreta|sintassi concreta]] sarebbe estremamente complesso e di poco senso, quindi ci limitiamo a scrivere la [[Sintassi astratta|sintassi astratta]]_.

### Semantica
Per dare semantica alla sintassi, la semantica operazionale strutturata definisce un modello matematico detto [[Sistema di transizione|sistema di transizione]][^1].

Una volta compreso, è necessario definire un sistema di transizione per ogni categoria sintattica, quindi per _espressioni aritmetiche_, _espressioni booleane_ e _comandi_.

#### Espressioni aritmetiche
Definiamo il sistema di transizione delle espressioni aritmetiche come la tripla
$$(\Gamma_{e}, T_{e}, \to_{e})$$

ricordando che la grammatica libera per $e \in \text{Expr}$ è:
$$e ::= m|v|e+e|e-e|e*e$$

##### $\Gamma_{e}$
Semplicemente, l'insieme degli stati è definito come l'_associazione tra ogni espressione aritmetica $e \in \text{Expr}$ con il suo valore nello $\text{Store}$_ (rappresentato dalla funzione $\sigma$):
$$\Gamma_{e} = \{(e, \sigma) | e \in \text{Expr}, \sigma \in \text{Store}\}$$

##### $T_{e}$
Il sottoinsieme $T_{e} \subseteq \Gamma_{e}$ sarà costituito da tutte le _espressioni aritmetiche che sono giunte al loro termine_, ossia i numeri naturali associati allo store:
$$T_{e} = \{(n, \sigma) | n \in \mathbb{N}, \sigma \in \text{Store}\}$$

##### $\to_{e}$
Abbiamo detto che le relazioni di transizione sono descrivibili in modo finito attraverso [[Assioma|assiomi]] e [[Regole di inferenza|regole d'inferenza]]. In particolare, **per ogni produzione della grammatica $\text{Expr}$, sarà necessario fornire un'assioma o una regola d'inferenza che sviluppi il suo significato**.

$$\begin{prooftree}
\AxiomC{}
\LL{(Var)}
\UIC{$(v, \sigma) \to_{e} (\sigma(v), \sigma)$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{$(e_{0}, \sigma) \to_{e} (e_{0}', \sigma)$}
\LL{($\text{Sum}_{1}$)}
\UIC{$(e_{0}+e_{1}, \sigma) \to_{e} (e_{0}' + e_{1}, \sigma)$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{$(e_{1}, \sigma) \to_{e} (e_{1}', \sigma)$}
\LL{($\text{Sum}_{2}$)}
\UIC{$(m+e_{1}, \sigma) \to_{e} (m + e_{1}', \sigma)$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{}
\LL{($\text{Sum}_{3}$)}
\RL{$\ \ \ p = m + m'$}
\UIC{$(m+m', \sigma) \to_{e} (p, \sigma)$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{$(e_{0}, \sigma) \to_{e} (e_{0}', \sigma)$}
\LL{($\text{Sub}_{1}$)}
\UIC{$(e_{0}-e_{1}, \sigma) \to_{e} (e_{0}' - e_{1}, \sigma)$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{$(e_{1}, \sigma) \to_{e} (e_{1}', \sigma)$}
\LL{($\text{Sub}_{2}$)}
\UIC{$(m-e_{1}, \sigma) \to_{e} (m - e_{1}', \sigma)$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{}
\LL{($\text{Sub}_{3}$)}
\RL{$\ \ \ m \geq m' \ \land \ p = m - m'$}
\UIC{$(m-m', \sigma) \to_{e} (p, \sigma)$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{$(e_{0}, \sigma) \to_{e} (e_{0}', \sigma)$}
\LL{($\text{Prod}_{1}$)}
\UIC{$(e_{0}*e_{1}, \sigma) \to_{e} (e_{0}' * e_{1}, \sigma)$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{$(e_{1}, \sigma) \to_{e} (e_{1}', \sigma)$}
\LL{($\text{Prod}_{2}$)}
\UIC{$(m*e_{1}, \sigma) \to_{e} (m * e_{1}', \sigma)$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{}
\LL{($\text{Prod}_{3}$)}
\RL{$\ \ \ p = m * m'$}
\UIC{$(m*m', \sigma) \to_{e} (p, \sigma)$}
\end{prooftree}$$

###### Osservazioni
Ricaviamo le seguenti osservazioni:
1. _lo store $\sigma$ non viene mai modificato dalle espressioni aritmetiche_ (ovvio), questo perché gli assiomi non lo modificano, e per [[Induzione|induzione]] è facile dimostrare che se $(e_{0}, \sigma) \to_{e} (e_{0}', \sigma) \implies \sigma = \sigma'$ (se gli assiomi sono il caso base, e ogni regola di inferenza termina induttivamente in un assioma, allora lo store rimane lo stesso);
2. la [[Discipline di valutazione|disciplina di valutazione]] usata da $\text{Sum}_{1}$ e $\text{Sum}_{2}$ è la _IS_ (Interna Sinistra);
3. _la relazione di transizione $\to_{e}$ è deterministica_ (dimostrabile per [[Induzione strutturale|induzione strutturale]]), ossia $\gamma \to_{e} \gamma' \land \gamma \to_{e} \gamma'' \implies \gamma' = \gamma'' \ \ \ \forall \gamma, \gamma', \gamma''$ (questo ci dice che a partire da una configurazione $(e, \sigma)$, si arriva sempre su una sola configurazione terminale $(n, \sigma)$, dove $n$ è il valore di $e$ in $\sigma$).

Da quest'ultima osservazione, è possibile definire una [[Funzione parziale|funzione parziale]]
$$\text{eval}_{e}: \text{Expr} \times \text{Store} \to \mathbb{N}$$
che **dia semantica alle espressioni**. Questa è facilmente definita come:
$$\text{eval}_{e}(e, \sigma) = \begin{cases} m & (e, \sigma) \to^{*} (m, \sigma) \\ \text{indefinita} \end{cases}$$

<u>Nota bene</u>: solo se $\to_{e}$ è deterministica allora posso definire $\text{eval}$, perché se non lo fosse allora per una coppia $(e, \sigma)$ ci potrebbero essere due risultati $n_{1}, n_{2} \in \mathbb{N} : n_{1} \neq n_{2}$, e questo _violerebbe la definizione di funzione_.

<u>Nota bene</u>: dallo stato iniziale $(e, \sigma)$, una serie di [[Computazione|computazioni]] lo trasforma in quello finale $(m, \sigma)$. Quest'ultimo _è di fatto uno stato terminale, ossia $(m, \sigma) \in T_{e}$_. Si capisce perché _non esiste alcuna transizione $\in \to_{e}$ che prenda uno stato con $m \in \mathbb{N}$ e $\sigma \in \text{Store}$_: non esiste una computazione ulteriore.

Si tratta di una funzione parziale perché _su certi input $(e, \sigma)$ non è definito un output_. Per esempio, quando si ha una **sottrazione che dà risultato negativo**! Formalmente, il caso indefinito è prodotto da $\text{Sub}_{3}$ quando $m < m'$, e **produce uno stato bloccato ma non terminale**.

Definita la funzione $\text{eval}_{e}$, allora si può dare la definizione di equivalenza tra due espressioni aritmetiche come:
$$e \equiv e' \iff \forall \sigma \in \text{Store}. \ \ \ \text{eval}_{e}(e, \sigma) = \text{eval}_{e}(e', \sigma)$$

La funzione $\text{eval}_{e}$, in realtà, è definita rispetto a una disciplina di valutazione. Si dimostra che ${\text{eval}_{e}}_{\text{IS}} = {\text{eval}_{e}}_{\text{ID}}$; sulle altre discipline, come IP, ES, ED, ed EP, invece ci sono delle differenze, come il fatto che ${\to_{e}}_{\text{IP}}$ è _nondeterministica_: questo perché si possono prendere strade differenti per la valutazione di una stessa espressione aritmetica, ma _confluente_ perché sappiamo che a prescindere dall'ordine il risultato finale sarà sempre uguale (a parità di store).

#### Espressioni booleane
Passiamo alla descrizione del sistema di transizione delle espressioni booleane
$$(\Gamma_{b}, T_{b}, \to_{b})$$
sulla grammatica libera per $b \in \text{Bexpr}$
$$b ::= t|e=e|b \lor b| \neg b$$

##### $\Gamma_{b}$
L'insieme degli stati è semplicemente
$$\Gamma_{b} = \{(b, \sigma) | b \in \text{Bexpr}, \sigma \in \text{Store}\}$$

##### $T_{b}$
Gli stati terminali sono
$$T_{b} = \{(\text{tt}, \sigma), (\text{ff}, \sigma) | \sigma \in \text{Store}\}$$

##### $\to_{b}$
Anche qui per la relazione di transizione andiamo a specificare assiomi e regole d'inferenza.
$$\begin{prooftree}
\AxiomC{$(e_{0}, \sigma) \to_{e} (e_{0}', \sigma)$}
\LL{($\text{Eq}_{1}$)}
\UIC{$(e_{0} = e_{1}, \sigma) \to_{b} (e_{0}' = e_{1}, \sigma)$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{$(e_{1}, \sigma) \to_{e} (e_{1}', \sigma)$}
\LL{($\text{Eq}_{2}$)}
\UIC{$(m = e_{1}, \sigma) \to_{b} (m = e_{1}', \sigma)$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{}
\LL{($\text{Eq}_{3}$)}
\RL{$ \ \ \ t = \begin{cases} \text{tt} & m=m' \\ \text{ff} & m \neq m' \end{cases}$}
\UIC{$(m = m', \sigma) \to_{b} (t, \sigma)$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{$(b_{0}, \sigma) \to_{b} (b_{0}', \sigma)$}
\LL{($\text{Or}_{1}$)}
\UIC{$(b_{0} \lor b_{1}, \sigma) \to_{b} (b_{0}' \lor b_{1}, \sigma)$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{}
\LL{($\text{Or}_{2}$)}
\UIC{$(\text{tt} \lor b_{1}, \sigma) \to_{b} (\text{tt}, \sigma)$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{}
\LL{($\text{Or}_{2}$)}
\UIC{$(\text{ff} \lor b_{1}, \sigma) \to_{b} (b_{1}, \sigma)$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{$(b, \sigma) \to_{b} (b', \sigma)$}
\LL{($\text{Neg}_{1}$)}
\UIC{$(\neg b, \sigma) \to_{b} (\neg b', \sigma)$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{}
\LL{($\text{Neg}_{2}$)}
\RL{$\ \ \ t' = \begin{cases} \text{tt} & t=\text{ff} \\ \text{ff} & t = \text{tt} \end{cases}$}
\UIC{$(\neg t, \sigma) \to_{b} (t', \sigma)$}
\end{prooftree}$$

###### Osservazioni
1. _per $\text{Eq}_{1}, \text{Eq}_{2}, \text{Eq}_{3}$ si usa il sistema di transizione delle espressioni aritmetiche_ per poter valutare $e_{0}, e_{1} \in \text{Expr}$;
2. le _regole $\text{Or}_{1}, \text{Or}_{2}, \text{Or}_{3}$ sono definite in disciplina ES_;
3. anche qui, _la valutazione di un'espressione booleana non modifica lo store_;
4. si dimostra che anche _$\to_{b}$ è deterministica_;

Dal fatto che $\to_{b}$ è deterministica ricavo la definizione della funzione parziale
$$\text{eval}_{b}: \text{Bexpr} \times \text{Store} \to \mathbb{B}$$
come
$$\text{eval}_{b}(b, \sigma) = \begin{cases} t & (b, \sigma) \to^{*} (t, \sigma) \\ \text{indefinita} \end{cases}$$

Anche $\text{eval}_{b}$ è parziale perché dipende da $\text{eval}_{e}$! Infatti _$\text{Eq}_{1}$ potrebbe restituire un valore indefinito, quindi di stato bloccato, nel momento in cui $e_{0}$ viene valutato in un numero al di fuori del dominio dei naturali_ (negativo).

Ugualmente si definisce l'uguaglianza tra espressioni booleane come
$$b \equiv b' \iff \forall \sigma \in \text{Store}. \ \ \ \text{eval}_{b}(b, \sigma) = \text{eval}_{b}(b', \sigma)$$

Riguardo alla disciplina di valutazione, è importante notare una grande differenza rispetto alle espressioni aritmetiche. Se devo valutare lo stato
$$\gamma = ((3-5)=6 \lor \text{tt}, \sigma)$$
allora avrò che:
- $\gamma \not {\to_{b}}_{\text{ES}}$, perché sulla valutazione dell'espressione aritmetica $(3-5)$ rimane bloccato[^2];
- $\gamma {\to_{b}}_{\text{ED}} (\text{tt}, \sigma)$, perché si valuta prima $b_{1} = \text{tt}$.

In poche parole il risultato cambia a seconda della regola di valutazione. E in generale è possibile stabilire la seguente sequenza di disuguaglianze:
![[Drawing 2024-10-06 17.36.51.excalidraw|750]]

#### Comandi
Definiamo il sistema di transizione dei comandi
$$(\Gamma_{c}, T_{c}, \to_{c})$$
con grammatica di riferimento per $c \in \text{Com}$
$$c ::= \text{skip}|v:=e|c;c|\text{while b do c}|\text{if b then c else c}$$

##### $\Gamma_{c}$
$$\Gamma_{c} = \{(c, \sigma) | c \in \text{Com}, \sigma \in \text{Store}\}$$

##### $T_{c}$
$$T_{c} = \{\sigma|\sigma \in \text{Store}\} = \text{Store}$$

##### $\to_{c}$
$$\begin{prooftree}
\AxiomC{}
\LL{($\text{Skip}$)}
\UIC{$(\text{skip}, \sigma) \to_{c} \sigma$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{$(e, \sigma) \to^{*}_{e} (m, \sigma)$}
\LL{($\text{Ass}$)}
\RL{$ \ \ \ \sigma[m/v](v') = \begin{cases} m & v' = v \\ \sigma(v') & v' \neq v \end{cases}$}
\UIC{$(v := e, \sigma) \to_{c} \sigma[m/v]$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{$(c_{0}, \sigma) \to_{c} (c_{0}', \sigma')$}
\LL{($\text{Seq}_{1}$)}
\UIC{$(c_{0};c_{1}, \sigma) \to_{c} (c_{0}';c_{1}, \sigma')$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{$(c_{0}, \sigma) \to_{c} \sigma'$}
\LL{($\text{Seq}_{2}$)}
\UIC{$(c_{0};c_{1}, \sigma) \to_{c} (c_{1}, \sigma')$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{$(b, \sigma) \to^{*}_{b} (\text{tt}, \sigma)$}
\LL{($\text{If}_{1}$)}
\UIC{$(\text{if } b \text{ then } c_{0} \text{ else } c_{1}, \sigma) \to_{c} (c_{0}, \sigma)$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{$(b, \sigma) \to^{*}_{b} (\text{ff}, \sigma)$}
\LL{($\text{If}_{2}$)}
\UIC{$(\text{if } b \text{ then } c_{0} \text{ else } c_{1}, \sigma) \to_{c} (c_{1}, \sigma)$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{$(b, \sigma) \to^{*}_{b} (\text{tt}, \sigma)$}
\LL{($\text{Wh}_{1}$)}
\UIC{$(\text{while } b \text{ do } c, \sigma) \to_{c} (c;\text{while } b \text{ do } c, \sigma)$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{$(b, \sigma) \to^{*}_{b} (\text{ff}, \sigma)$}
\LL{($\text{Wh}_{2}$)}
\UIC{$(\text{while } b \text{ do } c, \sigma) \to_{c} \sigma$}
\end{prooftree}$$

###### Osservazioni
1. si dimostra ancora una volta che _$\to_{c}$ è deterministica_;
2. in questo sistema di transizione si ha che la **divergenza e il deadlock sono equiparati**.

Dal determinismo di $\to_{c}$ definiamo la funzione parziale
$$\text{exec}: \text{Com} \times \text{Store} \to \text{Store}$$
come
$$\text{exec}(c, \sigma) = \begin{cases} \sigma' & (c, \sigma) \to^{*}_{c} \sigma' \\ \text{indefinita} \end{cases}$$

### Problemi
La _divergenza_ è quando si ha un ciclo infinito, come
$$\gamma_{0} = (\text{while tt do skip}, \sigma)$$
Invece il _deadlock_ è quello stato di blocco che avviene in caso di sottrazione che produce un numero negativo, come
$$\gamma_{1} = (x := (3-5), \sigma)$$

Il punto è che
$$\text{exec}(\gamma_{0}, \sigma) = \text{indefinito} = \text{exec}(\gamma_{1}, \sigma)$$
e _questo non va affatto bene_.

#### Errori dinamici
Per ovviare a questa mancata distinzione tra divergenza e deadlock, è necessario introdurre gli **errori dinamici** (a **run-time**). In particolare è necessario estendere gli stati e gli stati terminali con uno stato di errore $\text{err}$:
$$\Gamma' = \Gamma \cup \{\text{err}\} \ \ \ \ \ T' = T \cup \{\text{err}\}$$

A questo punto si ridefiniscono
$$\begin{align}
& \text{eval}_{e}: \text{Exp} \times \text{Store} \to \mathbb{N} \cup \{\text{err}\} \\
& \text{eval}_{b}: \text{Bexp} \times \text{Store} \to \mathbb{B} \cup \{\text{err}\} \\
& \text{exec}: \text{Com} \times \text{Store} \to \text{Store} \cup \{\text{err}\} \\
\end{align}$$

<u>Nota bene</u>: _$\text{eval}_{e}$ e $\text{eval}_{b}$ diventano funzioni totali_! Invece _$\text{exec}$ rimane parziale per via della divergenza_ (cicli infiniti che non producono output).

Chiaramente le conseguenze si ripercuotono anche sui singoli sistemi di transizione. In particolare _vanno aggiunte le seguenti regole_ (assiomatiche e d'inferenza) _per gestire il nuovo stato dell'errore_.

$$\begin{prooftree}
\AxiomC{}
\LL{($\text{Sub}_{4}$)}
\RL{$ \ \ \ m < m'$}
\UIC{$(m - m', \sigma) \to_{e} \text{err}$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{$(e_{0}, \sigma) \to_{e} \text{err}$}
\LL{($\text{Sum}_{4}$)}
\UIC{$(e_{0}+e_{1}, \sigma) \to_{e} \text{err}$}
\end{prooftree}$$

$$\begin{prooftree}
\AxiomC{$(e_{1}, \sigma) \to_{e} \text{err}$}
\LL{($\text{Sum}_{5}$)}
\UIC{$(m+e_{1}, \sigma) \to_{e} \text{err}$}
\end{prooftree}$$

Analoghe per $\text{Bexp}$ e $\text{Com}$.

<u>Nota bene</u>: tutto questo per l'unico errore possibile di questo linguaggio, ossia la sottrazione con risultato negativo. Si pensi a quante regole servono per linguaggi più sofisticati!

### Nondeterminismo e Parallelismo
La grammatica dei comandi può essere estesa aggiungendo due produzioni:
$$c ::= \cdots|c \lor c| c \text{ par } c$$

dove:
- $c \lor c$ un comando che _esegue solo uno dei due sottocomandi_;
- $c \text{ par } c$ è un comando che _esegue in parallelo i due sottocomandi_;

La semantica di queste produzioni è facilmente catturabile dalle seguenti relazioni di transizione:
![[transizioni-nondeterminismo.png]]
![[transizioni-parallelismo.png]]

Si verifica, però, che $\to_{c}$ ora non è più deterministica. Si prenda in esempio l'esecuzione del sistema di transizione per
$$(x:=0; x:=x+1) \text{ par } x:=1$$

![[relazione-nondeterministica.png]]

Si può facilmente notare che si raggiungano due risultati finali differenti.: uno è raggiunto in due modi diversi, e potrebbe suggerire una _confluenza_ della relazione $\to_{c}$; ma dato che esiste una strada che porta a un risultato completamente diverso, si conclude che _$\to_{c}$ è nondeterministica_.

Per modellare questa situazione si usa la notazione:
$$\text{exec}: \text{Com} \times \text{Store} \to \mathscr{P}(\text{Store})$$
ossia il dominio di $\text{exec}$, ora è l'[[Assioma dell'insieme potenza|insieme delle parti]] di $\text{Store}$, ossia un suo possibile sottoinsieme.

## Referenze
[^1]: una specie di [[Automa|automa]]
[^2]: $\text{Sub}_{3}$ non è applicabile