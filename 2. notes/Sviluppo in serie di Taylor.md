---
tags:
  - category/note
  - status/finished
  - topic/analisi-I
date: 12-11-2023 17:21:28
links:
  - "[[Lecture 10112023134301]]"
  - "[[Lecture 13112023094129]]"
  - "[[Lecture 17112023134446]]"
  - "[[Lecture 03052024102451]]"
  - "[[Lecture 06052024131425]]"
  - "[[Lecture 09052024141025]]"
---
# Sviluppo in serie di Taylor
---
## Introduzione
L'idea alla base degli **sviluppi in serie di Taylor** è di _approssimare una funzione con un polinomio_, in modo tale che _ai fini del [[Limite|limite]] l'errore non conti_. Per intenderci, ottenuto un polinomio che approssima una funzione, l'_errore dev'essere piccolo rispetto al polinomio_.

Per poter definire queste serie, è necessario avere bene a mente i concetti di [[Infiniti|infiniti]], di [[Infinitesimi|infinitesimi]] e di [[O-piccolo|o-piccolo]].

## Principio
### 1° ordine
Cominciamo con il voler approssimare una generica [[Funzione matematica|funzione]] $f(x)$ [[Funzioni derivabili|derivabile]] con un polinomio di 1° grado (_una retta_) in $x = 0$. Vogliamo trovare il polinomio che meglio approssimi la funzione, sempre per $x = 0$.

Si comincia allora dall'unica ipotesi a disposizione: $f(x)$ derivabile. Si avrà per cui che
$$\lim_{x \to 0} \frac{f(x) - f(0)}{x} = f'(0) \in \mathbb{R}$$

Ora, portiamo la derivata prima a sinistra dell'uguale e otteniamo
$$\lim_{x \to 0} \frac{f(x) - f(0) - f'(0) \cdot x}{x} = 0$$

Notiamo che il **numeratore $f(x) - f(0) - f'(0) \cdot x$ è un o-piccolo di $x$**. Quindi possiamo scrivere
$$f(x) - f(0) - f'(0) \cdot x = o(x)$$

che trasformato ci diventa
$$f(x) = f(0) + f'(0) \cdot x + o(x)$$

Questo è il polinomio di primo grado che meglio approssima la funzione! Notare che _$o(x)$ rappresenta la generica funzione d'errore_, in breve la differenza (in termini di distanza numerica) tra i valori della funzione originaria e il polinomio. _In $x = 0$ le due funzioni coincideranno; più ci si allontanerà dall'origine più l'errore $o(x)$ influirà sul polinomio_.

L'errore è "ben accetto" perché, anche se grande, essendo all'approssimazione del primo ordine, e quindi lineare, esso tende a 0 più velocemente di $x$.

### 2° ordine
Se ora volessimo ottenere un'approssimazione polinomiale di $f(x)$ con un polinomio di grado 2, significherebbe ottenere
$$f(x) = f(0) + f'(0) \cdot x + a_{2}x^{2} + E_{2}(x)$$
dove $E_{2}(x)$ è l'errore.

L'idea è di trovare un $a_{2} \in \mathbb{R}$ tale che $E_{2}(x)$ tenda a 0 più velocemente di $x^{2}$ (affinché esso sia accettabile). Quindi abbiamo
$$E_{2}(x) = o(x^{2})$$

Riscrivendo la formula abbiamo quindi
$$f(x) - f(0) - f'(0) \cdot x - a_{2}x^{2} = o(x^{2})$$
da cui, imponendo la definizione di o-piccolo otteniamo
$$\lim_{x \to 0} \frac{f(x) - f(0) - f'(0) \cdot x - a_{2}x^{2}}{x^{2}} = 0$$

Per risolvere il limite ([[Forme indeterminate|forma indeterminata]]) usiamo [[Teorema di de l'Hopital|Hopital]], per arrivare ad avere
$$\frac{f''(0)}{2} - a_{2} = 0$$

Noi vogliamo imporre questa condizione, per cui si conclude con
$$a_{2} = \frac{f''(0)}{2}$$
da cui si ottiene la formula finale
$$f(x) = f(0) + f'(0) \cdot x + \frac{f''(0)}{2} \cdot x^{2} + o(x^{2})$$

### $n$-esimo ordine
Reiterando $n$ volte l'ultimo passaggio si ottiene un'espressione che è facilmente rappresentabile attraverso una [[Sommatoria|sommatoria]]: il [[Teorema di Peano|teorema di Peano]].

Il grado $n$ per cui si sceglie di reiterare il processo è detto **ordine dello sviluppo**, e _deve coincidere con il grado dell'errore_, quindi con l'o-piccolo.

## Utilizzo
> L'applicazione degli sviluppi di Taylor consiste, principalmente, nel **calcolare l'ordine di grandezza di un infinitesimo**, ovvero nell'**approssimare un'infinitesimo** (usando polinomi) **al primo ordine di sviluppo $n$ che corrisponda ad almeno un monomio**.

Se abbiamo, per esempio, una _funzione infinitesima_ composta _da più funzioni elementari_ sviluppabili con Taylor, prese queste singolarmente si devono sviluppare fino al primo ordine di sviluppo che garantisca, sostituito lo sviluppo al posto della sua funzione, che il risultato complessivo abbia almeno un monomio.

In caso in cui, quindi, sviluppassimo una funzione elementare fino a un grado $n$, e _sostituendo lo sviluppo nella funzione principale ottenessimo come risultato solo un o-piccolo, dovremmo aumentare il grado di sviluppo_.

I passi sono quindi:
1. di una funzione $f$ identifichiamo le sottofunzioni $g$ che vogliamo sviluppare
2. sviluppiamo al primo ordine le funzioni $g$ e sostituiamo il risultato in $f$
3. se il risultato non ha almeno un monomio, reiterare dal punto 2 aumentando il grado di sviluppo ($+1$)
4. altrimenti il risultato è trovato

L'obiettivo finale è quello di ottenere un _infinitesimo equivalente a $f$_, quindi un polinomio che tenda a 0 alla stessa velocità a cui ci tende $f$!

<u>Nota</u> che **trovato il primo monomio non serve più sviluppare per un grado maggiore**, in quanto si andrebbero ad aggiungere informazioni inutili rispetto al monomio già trovato. La velocità di avvicinamento a 0 è infatti data dal monomio di grado maggiore, dal più influente per $x \to x_{0}$, quindi quelli di grado più alto possono non essere considerati.

### Esempio
Mettiamo caso di avere l'infinitesimo
$$e^{x} - 1 - x$$
dove quindi per $x \to 0$ esso vale 0.

Vogliamo sapere il suo ordine di grandezza, ovvero trovare un infinitesimo equivalente, espresso come polinomio di Taylor. Per farlo consideriamo $e^{x}$ e sviluppiamolo al prim'ordine:
$$e^{x} = 1 + x + o(x)$$
Quindi sostituiamo il risultato a $e^{x}$ e otteniamo
$$1 + x + o(x) - 1 - x$$
ovvero
$$o(x)$$

Stiamo così dicendo che $e^{x} - 1 - x$ è un infinitesimo equivalente a $o(x)$: questo _non ci dice assolutamente niente di specifico per la funzione_.

Per cui sviluppiamo $e^{x}$ al secondo ordine
$$e^{x} = 1 + x + \frac{x^{2}}{2} + o(x^{2})$$
e sostituiamo il risultato, ottenendo
$$1 + x + \frac{x^{2}}{2} + o(x^{2}) - 1 - x$$
ovvero questa volta
$$\frac{x^{2}}{2} + o(x^{2})$$

Ora sì che diamo un'informazione tangibile sulla funzione: stiamo dicendo che $e^{x} - 1 - x$ è un infinitesimo equivalente a $\frac{x^{2}}{2} + o(x^{2})$. Queste due funzioni si avvicinano a 0 alla stessa velocità, e per questo, _ai fini di un [[Calcolo dei limiti con Taylor|eventuale calcolo del limite]]_, sono **interscambiabili**.

Se noi decidessimo di voler sviluppare ancora una volta $e^{x}$ (per un grado maggiore), otterremmo alla fine
$$\frac{x^{2}}{2} + \frac{x^{3}}{6} + o(x^{3})$$
che di per sé non è sbagliata, ma _semplicemente ininfluente_. Infatti ciò che più condiziona il comportamento della funzione per $x \to 0$ è il monomio di grado inferiore, in questo caso $\frac{x^{2}}{2}$: tutti gli altri monomi, che _sicuramente approssimano con più precisione $e^{x}$_, _non costituiscono però ai fini del limite una precisazione utile, significativa_.

## Resto di Lagrange
Finora abbiamo preso in considerazione e analizzato solo quella che viene definita _formula di Taylor con resto secondo Peano_. Esiste tuttavia un altro sviluppo di Taylor, equivalente a quello di Peano, più generale: la **formula di Taylor di ordine 2 con resto di Lagrange**.

Questa è fondamentale per lo [[Studio del gradiente|studio delle funzioni a più variabili]], e in particolare _per dimostrare che la classificazione dei punti critici può avvenire sulla base dello studio del segno della [[Forma quadratica|forma quadratica]] della [[Matrice hessiana|matrice hessiana]]_.

<u>Nota bene</u>: _di ordine 2_ perché ci interessa studiare fino al secondo ordine di sviluppo.

### Formula
La formula di Peano per lo sviluppo di Taylor di ordine 2 è
$$f(\bar{x}+h) = f(\bar{x}) + f'(\bar{x})h + \frac{f''(\bar{x})}{2}h^{2} + o(h^{2}) \ \ \ \ \ h \to 0$$

Invece si ha che la formula dello sviluppo di Taylor di ordine 2 con resto secondo Lagrange si esprime come:
> Sia $f: \mathbb{R} \to \mathbb{R}$ con $f', f''$ continue, allora fissato $\bar{x} \in \mathbb{R}$ e $h \in \mathbb{R}$, allora si ha che
> $$\exists \theta \in ]0, 1[ \ : \ \  f(\bar{x} + h) = f(\bar{x}) + f'(\bar{x})h + \frac{f''(\bar{x} + \theta h)}{2}h^{2}$$

<u>Osservazione</u>: _manca l'o-piccolo_!

<u>Osservazione</u>: il [[Teorema di Lagrange|teorema di Lagrange]] dimostra che $\exists \theta \in ]0, 1[$ tale che $f(\bar{x} + h) = f(\bar{x}) + f'(\bar{x} + \theta h)h$. Infatti si ha $f'(\bar{x} + \theta h) = \frac{f(\bar{x}+h) - f(\bar{x})}{h}$ e $c = \bar{x} + \theta h \in ]\bar{x}, \bar{x}+h[$.

<u>Osservazione</u>: posso ovviamente scrivere anche questa formula di Taylor con $x = \bar{x} + h$, ottenendo $$f(x) = f(\bar{x}) + f'(\bar{x})(x - \bar{x}) + \frac{f''(c)}{2}(x - \bar{x})^{2}$$
con $c \in ]x, \bar{x}[$

### Differenze
La più importante differenza tra le due formulazioni di Taylor è che:
- _con resto di Peano_ --> la formula vale _solo per $h \to 0$_, ossia per punti $x$ molto vicini a $\bar{x}$;
- _con resto di Lagrange_ --> la formula vale _per qualsiasi $h$_, ossia per ogni punto $x$, che sia lontano o vicino a $\bar{x}$ (questo ci è garantito dal teorema di Lagrange).

### Dimostrazione
Vogliamo dimostrare l'equivalenza tra le due formule, e in particolare che quella con il resto di Lagrange $\implies$ quella con il resto di Peano, ossia
$$\exists \theta \in ]0, 1[ \ : \ \  f(\bar{x} + h) = f(\bar{x}) + f'(\bar{x})h + \frac{f''(\bar{x} + \theta h)}{2}h^{2}$$
$$\implies$$$$f(\bar{x}+h) = f(\bar{x}) + f'(\bar{x})h + \frac{f''(\bar{x})}{2}h^{2} + o(h^{2}) \ \ \ \ \ h \to 0$$
Ciò che facciamo è allora sottrarre la seconda dalla prima. Otteniamo:
$$\frac{f''(\bar{x} + \theta h)}{2}h^{2} - \frac{f''(\bar{x})}{2}h^{2} + o(h^{2}) = 0$$
Per cui ci basta verificare che $\frac{f''(\bar{x} + \theta h)}{2}h^{2} - \frac{f''(\bar{x})}{2}h^{2}$ sia un o-piccolo di $h^{2}$, ovvero
$$\lim_{h \to 0} \left(\frac{f''(\bar{x} + \theta h)}{2}h^{2} - \frac{f''(\bar{x})}{2}h^{2}\right) \cdot \frac{1}{h^{2}} = 0$$
ossia
$$\lim_{h \to 0} \left(\frac{f''(\bar{x} + \theta h)}{2} - \frac{f''(\bar{x})}{2}\right) = 0$$
e avendo $h \to 0$ e _$f''$ continua_
$$\frac{f''(\bar{x})}{2} - \frac{f''(\bar{x})}{2} = 0$$
il che è ovvio.

**Qed**.

### In $\mathbb{R}^{n}$
Lo sviluppo di Taylor di ordine 2 con resto di Lagrange vale anche per [[Funzione a più variabili|funzioni a più variabili]].
> Data $f: \mathbb{R}^{n} \to \mathbb{R}$, $\bar{x} \in \mathbb{R}^{n}$, $\partial^{2}_{jk}f$ continue $\forall j, k \in \{1, \cdots, n\}$, allora per ogni $h \in \mathbb{R}^{n}$ si ha che $$\exists \theta \in ]0, 1[ \ : \ \ f(\bar{x} + h) = f(\bar{x}) + < \nabla f(\bar{x}), h > + \frac{1}{2} <Hf(\bar{x} + \theta h)h, h>$$

<u>Nota bene</u>: posso ugualmente scrivere lo sviluppo di Taylor in $\mathbb{R}^{n}$ di ordine 2 con il resto di Peano, ottenendo
$$\forall \bar{x}, \bar{x}+h \in \mathbb{R} \ : \ \ f(\bar{x}+h) = f(\bar{x}) + <\nabla f(\bar{x}), h> + \frac{1}{2} <Hf(\bar{x})h, h> + o(|h|^{2})$$

<u>Osservazione</u>: in entrambe le equazioni, _graficamente parlando si ottiene un paraboloide o un'iperboloide che approssima la funzione in $\bar{x}$_.

#### Dimostrazione
Per dimostrare la validità della formula considero una [[Curva|curva]] $r: \mathbb{R} \to \mathbb{R}$ definita come $r(t) = f(\bar{x} + th)$. Scrivo Taylor per $r$ nell'intervallo $[0, 1]$:
$$\exists \theta \in ]0, 1[ \ : \ \ r(1) = r(0) + r'(0)(1-0) + \frac{1}{2}r''(0 + \theta1)(1-0)^{2} = r(0) + r'(0) + \frac{1}{2}r''(\theta)$$

Ma io so che $r(1) = f(\bar{x} + h)$ e $r(0) = f(\bar{x})$, allora voglio riscrivere lo sviluppo di $f$ usando $r$, ma prima mi serve sapere quanto vale $r'(0)$ e $r''(\theta)$: calcolo la [[Derivata lungo una curva|derivata lungo una curva]].

In particolare
$$r'(t) = \frac{d}{dt}f(\bar{x}+th) = <\nabla f(\bar{x}+th), \frac{d}{dt}(\bar{x}+th)> = <\nabla f(\bar{x}+th), h>$$
da cui, srotolando il prodotto scalare ottengo
$$<\nabla f(\bar{x} + th), h> = \sum\limits_{j=1}^{n} \partial_{j}f(\bar{x} + th)h_{j}$$
Allora $r'(0)$ sarà uguale a
$$r'(0) = \sum\limits_{j=1}^{n} \partial_{j}f(\bar{x})h_{j} = <\nabla f(\bar{x}), h>$$

Mi manca
$$r''(t) = \frac{d}{dt} \sum\limits_{j=1}^{n} \partial_{j}f(\bar{x} + th)h_{j} = \sum\limits_{j=1}^{n} \frac{d}{dt} \partial_{j}f(\bar{x} + th)h_{j} = \sum\limits_{j=1}^{n} <\nabla \partial_{j}f(\bar{x} + th), h> h_{j} = \sum\limits_{j=1}^{n} \sum\limits_{k=1}^{n} \partial_{kj}f(\bar{x} + th)h_{k}h_{j} = <Hf(\bar{x} + th)h, h>$$
da cui
$$r''(\theta) = <Hf(\bar{x} + \theta h)h, h>$$

Quindi, riunendo i pezzi, si ha infine
$$f(\bar{x} + h) = f(\bar{x}) + <\nabla f(\bar{x}), h> + \frac{1}{2}<Hf(\bar{x} + \theta h)h, h>$$

**Qed**.

## Referenze
- [[Polinomi di Taylor]]