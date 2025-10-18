---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 14-10-2025 16:31:44
links:
  - "[[Lecture 07052025110754]]"
---
# Oggetti esistenziali
---
## Introduzione
I [[Tipi esistenziali|tipi esistenziali]], catturano l'information hiding e l'indipendenza dalla rappresentazione tipica degli [[Tipi di dato astratto|ADT]], ma _non nello stesso modo in cui lo fanno gli ADT_!

Infatti, una volta che l'implementazione e' stata spacchettata, **il nome del tipo astratto che nasconde l'implementazione e' "identificativo"**, e quindi un altro nome dell'implementazione dello stesso ADT risulterebbe diverso dal primo!

Per fare un esempio consideriamo il tipo esistenziale
$$CounterADT = \{\exists X. \{new: () \to X, get: X \to int, inc: X \to X\}\}$$

e immaginiamo di definire due implementazioni del tipo:
$$\{Counter, c\} = \{*int, \{new = 1, get = fn(i:int)\{i\}, inc=fn(i:int)\{i+1\}\}\} \text{ as } CounterADT$$
$$\{ACounter, ac\} = \{*\{c: int\}, \{new = \{c: 1\}, get = fn(i:\{c: int\})\{i.c\}, inc=fn(i:\{c: int\})\{\{c: i.c+1\}\}\}\} \text{ as } CounterADT$$

Entrambe sono implementazioni di $CounterADT$, tuttavia se faccio:
$$\begin{array}{}
c_{1} = c.new() \\
c_{2} = ac.new() \\
ac.inc(c_{1})
\end{array}$$
ottengo un errore: `Type mismatch error`, perche' $Counter$ e $ACounter$ sono visti come tipi diversi.

Questo **e' invece possibile negli ADT**!

## Definizione
> Per tale ragione nascono gli **oggetti esistenziali**, che forniscono una visione alternativa degli ADT per consentire a piu' implementazioni dello stesso tipo esistenziale di interagire.

A tal fine _e' necessario che le definizioni del tipo esistenziale diventino dei veri e propri tipi all'interno del programma_ (che facciano quindi parte del [[Sistema di tipi|sistema di tipi]]).

In tal modo possiamo definire degli oggetti come _tipi concreti che mantengono il loro stato_ (implementazione) _interno_ ma **portano anche con se' l'associazione con il loro tipo esistenziale**.

## Notazione
Per creare un oggetto esistenziale e' sufficiente modificare l'ADT ponendo al suo interno un campo $stato$:
$$Counter = \{\exists X. \{state: X, methods: \{ new: () \to X, get: X \to int, inc: X \to X\}\}\}$$

In questo modo possiamo definire le implementazioni
$$\begin{array}{l}
c_{1} = \{*int, \{state: 1, methods: \{get(int \ i)\{i\}, inc(\{*A, c\} \text{ as } Counter)\{c.get(c)+1\}\}\}\} \text{ as } Counter \\
c_{2} = \{*\{c: int\}, \{state: \{c: 1\}, methods: \{get(*\{c: int\} i)\{i.c\}, inc(\{*A, c\} \text{ as } Counter)\{\{c: c.get(c)+1\}\}\}\}\} \text{ as } Counter \\
\\
f(\{*A, a\} \text{ as } Counter, \{*B, b\} \text{ as } Counter) \{\{*A, \{state: a.inc(b), methods: a.methods\}\} \text{ as } Counter\}
\end{array}$$

e a questo punto posso tranquillamente fare
$$f(c_{1}, c_{2}) \ \ \ \ \ f(c_{2}, c_{1})$$

Fondamentalmente questo funziona perche' le funzioni $inc$ entrambe sono definite in modo generale, su dei generici $Counter$.

<u>Nota bene</u>: il motivo per cui manca il $new$ e' che lo stesso stato si trova all'interno di $state$!

## Oggetti vs. ADT
Gli ADT adottano una visione aperta dei tipi esistenziali e delle loro implementazioni: quando importiamo un'implementazione, la "apriamo" ("spacchettiamo") immediatamente, prima dell'uso, bindando il tipo alla sua implementazione. Il client ha l'implementazione diretta degli ADT.

Con gli oggetti, invece, l'oggetto e' sempre "chiuso", e usiamo solo ed esclusivamente i suoi metodi per accedere al suo stato interno. E' per questa ragione che, _dato che ogni oggetto ha la sua rappresentazione interna, il suo stato, e l'implementazione delle proprie operazioni, possiamo mescolare implementazioni diverse dello stesso tipo esistenziale_.

Questo meccanismo e' alla base del [[Sottotipaggio|sottotipaggio]].

## Referenze