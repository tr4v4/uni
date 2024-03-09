---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 06-11-2023 21:27:52
links:
  - "[[Lecture 31102023161330]]"
  - "[[Lecture 02112023091408]]"
  - "[[Lecture 08112023131119]]"
---
# Semantica classica
---
## Introduzione
> La **semantica classica** è un tipo di [[Semantica|semantica]] fondata sui principi della [[Logica classica|logica classica]], che associa quindi ad ogni [[Connotazione|connotazione]] un _valore di verità_. Si basa sul **ragionamento ipotetico**, ovvero sull'associazione da determinati **[[Mondo|mondi]]** (_[[Insieme|insiemi]] fissati di configurazioni_) a un _valore di verità_.

Quando faccio un ragionamento ipotetico _escludo dal ragionamento tutti i mondi in cui le ipotesi non si verificano_. Le **ipotesi**, di fatto, **caratterizzano il mondo**, su cui si vuole verificare la validità di una tesi (capire se è vera o falsa per quel mondo).

In altre parole:
- le _variabili_[^1] variano per ogni mondo
- i _connettivi logici_ hanno senso costante per ogni mondo

## Definizione
> Dato un _mondo_ $v$, la _semantica_ $[[\cdot]]^{v} : \mathcal{F} \to \{0, 1\}$ (ovvero la _classica_)[^2], è definita per [[Ricorsione strutturale|ricorsione strutturale]] sulle _connotazioni_ come segue:
> - $[[\bot]]^{v} = 0$ (in ogni mondo $v$)
> - $[[\top]]^{v} = 1$ (in ogni mondo $v$)
> - $[[A]]^{v} = v(A)$ (dipende dal mondo, _richiamiamo la [[Funzione informatica|funzione]] $v$ che ci restituisce il valore di $A$_)
> - $[[\neg F]]^{v} = 1 - [[F]]^{v}$ (utilizzo la ricorsione strutturale) (lo faccio in questo modo per mantenere possibile la scalabilità tra $[0, 1]$)
> - $[[F_{1} \land F_{2}]]^{v} = \min\{[[F_{1}]]^{v}, [[F_{2}]]^{v}\}$
> - $[[F_{1} \lor F_{2}]]^{v} = \max\{[[F_{1}]]^{v}, [[F_{2}]]^{v}\}$
> - $[[F_{1} \implies F_{2}]]^{v} = \max\{1 - [[F_{1}]]^{v}, [[F_{2}]]^{v}\}$ (per capirla dobbiamo comprendere che l'implicazione non mette in rapporto di casualità $F_{1}$ e $F_{2}$)

### Alternativa
La definizione di semantica classica può anche essere scritta usando la _meta-logica_, in quella che si chiama **semantica tarskiana**:
- $[[\bot]]^{v}$ è _falsa_
- $[[\top]]^{v}$ è _vera_
- $[[A]]^{v} = v(A)$
- $[[\neg F]]^{v}$ è vera sse $[[F]]^{v}$ _non_ è vera
- $[[F_{1} \land F_{2}]]^{v}$ è vera sse $[[F_{1}]]^{v}$ è vera _e_ $[[F_{2}]]^{v}$ è vera
- $[[F_{1} \lor F_{2}]]^{v}$ è vera sse $[[F_{1}]]^{v}$ è vera _o_ $[[F_{2}]]^{v}$ è vera
- $[[F_{1} \implies F_{2}]]^{v}$ è vera sse _se_ $[[F_{1}]]^{v}$ è vera _allora_ $[[F_{2}]]^{v}$ è vera

Il problema di questa semantica è proprio che _utilizza la meta-logica per spiegare la logica_: non ci insegna nulla di nuovo, di fatto potremmo ridefinire la definizione di semantica usando a sua volta la _meta-meta-logica_, senza concludere nulla di fatto.

La comodità della definizione di semantica con la _meta-matematica_, invece, ci aiuta a fare un passo ulteriore, di avere una base pressoché solida su cui costruire la logica, che a sua volta giustificherà la meta-matematica.

## Teoremi
> Definita $Var(F)$ una funzione definita per ricorsione strutturale che restituisce, di una formula $F$ le sue variabili:
> - $Var(\top) = \varnothing$
> - $Var(\bot) = \varnothing$
> - $Var(A) = \{A\}$
> - $Var(B) = \{B\}$
> - ...
> - $Var(\neg F) = Var(F)$
> - $Var(F_{1} \land F_{2}) = Var(F_{1}) \cup Var(F_{2})$
> - $Var(F_{1} \lor F_{2}) = Var(F_{1}) \cup Var(F_{2})$
> - $Var(F_{1} \implies F_{2}) = Var(F_{1}) \cup Var(F_{2})$

si hanno i seguenti teoremi:
1. **$Var(F)$ è sempre un insieme finito qualunque sia $F$**
2. **per calcolare $[[F]]^{v}$ l'interpretazione $v$ viene invocata solamente sulle variabili proposizionali $X \in Var(F)$** --> quindi si fa $v(X)$ solo per le $X$ che sono variabili della proposizione $F$

### Conseguenze
Alla luce dei due teoremi notiamo che si possono rappresentare, su [[Tabella di verità|tabelle di verità]], _non solo i connettivi logici ma anche delle intere proposizioni_ $[[F]]^{v}$ al variare del mondo $v$.

Infatti i connettivi logici della semantica classica hanno un numero finito di argomenti (_zero-ari_, _unari_, _binari_), e il _[[Dominio di interpretazione|dominio di interpretazione]]_ è $\{0, 1\}$: con $2^{n}$ righe è possibile rappresentare la semantica classica.

E, sfruttando i due teoremi si ha che:
- dal primo teorema so che il numero di righe della tabella sarà $2^{n}$ dove $n = |Var(F)|$
- dal secondo teorema sono sicuro che ciò che cambia della tabella, e che costituisce le righe, sono solo le chiamate al mondo $v$ sull'insieme finito delle variabili in $Var(F)$

In conclusione abbiamo una tabella di verità in cui _ogni riga rappresenta un insieme di mondi che concordano, quindi hanno la stessa configurazione, su un numero finito di variabili ($Var(F)$), e il numero di tali insiemi è finito ($2^{|Var(F)|}$)_[^3].

Le problematiche legate alle tabelle di verità si riassumono in:
- _limitatezza_, infatti non scalano perché funzionano per valori finiti ($2^{n}$)
- _inestendibilità_, perché se si cambia logica in una con dominio $[0, 1]$ non vanno più bene (non si possono rappresentare tutte le infinite combinazioni); allo stesso modo, se si ha un insieme infinito di ipotesi $\Gamma = A, B, C, ...$, si avrebbe $Var(\Gamma) = Var(A) \cup Var(B) \cup Var(C) \cup ...$
- _scomodità_, sono lunghe
- _inutilità_, non ci insegnano nulla

Per questi motivi **hanno un uso limitato in logica**, anche se servono per dimostrare la [[Conseguenza logica|conseguenza logica]].

#### Osservazione
Tra tutte le tabelle di verità, quella dell'[[Implicazione|implica]] è l'unica a non catturare la **nozione di causalità**. _Sfugge infatti alla nostra intuizione_[^4].

## Referenze
[^1]: vedi la [[Logica proposizionale#Sintassi|sintassi della logica proposizionale]]
[^2]: si vede dal dominio di interpretazione ($\{0, 1\}$)!
[^3]: stiamo considerando l'[[Insieme quoziente|insieme quoziente]] di tutte le [[Classe di equivalenza|classi di equivalenza]] dei mondi possibili cui [[Relazione di equivalenza|relazione di equivalenza]] è avere la stessa configurazione di $Var(F)$
[^4]: si veda il [[Teorema di deduzione semantica|teorema di deduzione semantica]]