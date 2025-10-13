---
tags:
  - category/note
  - status/finished
  - topic/introduzione-all-apprendimento-automatico
date: 01-10-2025 18:58:30
links:
  - "[[Lecture 26092025131224]]"
---
# Albero di decisione
---
## Introduzione
Il _training set_ di questi alberi, in quanto modelli supervisionati, e' l'insieme delle tuple
$$(x^{(i)}, y^{(i)})$$
dove:
- $x^{(i)} \in X$ sono gli input;
- $y^{(i)} \in Y$ sono gli output.

L'insieme degli output $Y$ puo' essere:
- _discreto_ - problema di [[Classificazione|classificazione]];
- _continuo_ - problema di [[Regressione|regressione]].

## Definizione
> Un **albero di decisione** e' un [[Albero informatico|albero]] che ha associato ad ogni nodo una [[Features di un dato|feature]], e i figli sono altri nodi o delle foglie (_label_, l'output della funzione). Gli archi che collegano i nodi, sono etichettati con i possibili valori _discreti_ assunti dalla feature genitore.

## Espressivita'
Ci chiediamo quanto siano espressivi gli alberi di decisione, ossia quanti problemi possano risolvere: la risposta e' _tanti quanti ne possono risolvere i connettivi booleani_!

Infatti con un albero di decisione posso rappresentare tutti i connettivi booleani.

## Overfit
Seppure espressivi, questi modelli non sono molto bravi a generalizzare! Fanno _[[Overfitting|overfit]] totale_, ossia una volta che e' stato costruito l'albero, _tanto piu' completo questo e' tanto meno sara' la sua capacita' di generalizzare nuovi dati_.

## Costruzione
Usiamo un [[Approccio top-down|approccio top-down]]:
1. assegno al nodo corrente la "migliore" feature $X_{i}$;
2. creo un nodo figlio per ogni possibile valore di $X_{i}$ e propago i dati verso i figli a seconda del loro valore;
3. per ogni nodo figlio, se tutti i dati del training set associato al nodo hanno una stessa etichetta (output) $y$, marco il nodo come foglia con etichetta $y$, altrimenti ripeto dal primo punto;

<u>Nota bene</u>: _posso non arrivare per forza alle foglie, fermando la computazione_. In tal caso interpreto il risultato di un nodo quasi-foglia come una [[Probabilita'|probabilita']].

La questione e' capire qual e' il "miglior" nodo $X_{i}$! Questo problema si chiama **ricerca della miglior feature**.

### Ricerca della miglior feature
Per comprendere in che modo e' possibile valutare la scelta di una feature migliore rispetto a un'altra, bisogna studiare la [[Teoria dell'informazione|teoria dell'informazione]].

L'idea di base è quella di _avere invece il massimo sbilanciamento nella separazione dei nipoti_, in modo che _se si interrompe la computazione dell'albero a quel livello ho una probabilità diversa dal 50%_, e quindi l'[[Entropia|entropia]] minima!

In particolare consideriamo questi 2 nodi:
![[albero-di-decisione-1.png]]

Se vogliamo abbassare l'entropia, allora dobbiamo massimizzare [[Guadagno informativo|guadagno informativo]] tra la variabile target $Y$ e il nodo $X$ da scegliere (potrebbe essere $A$ o $B$).

Calcoliamo intanto l'entropia di $Y$, guardando le probabilita' che $Y$ valga $+$ e che valga $-$ fino a quel punto della computazione dell'albero: in questo caso, in $\frac{29}{29+35}$ casi e' $+$, mentre nei restanti e' $-$.

Avremo che
$$H(Y) = -\frac{29}{64} \log_{2}{\frac{2​9}{64}} - \frac{35}{64} \log_{2}{\frac{​35}{64}} \approx 0.994$$
Altissima! Infatti i casi sono distribuiti quasi uniformemente...

Calcolando le restanti entropie condizionate, vediamo cosa si abbassa:
![[entropie-albero-decisionale-1.png]]

Scopriamo fondamentalmente, che se si sceglie $A$ l'entropia condizionata $H(Y|A)$ si abbbassa a $0.726$; se invece si sceglie $B$, si ha $H(Y|B) = 0.872$: di conseguenza, _il guadagno informativo, ossia la differenza tra l'entropia di $Y$ e di quella calcolata sulla base del nuovo nodo $X$, sara' maggiore con $A$_!

## Caso continuo
Per costruire alberi di decisione su features continue, le andiamo a _discretizzare con una soglia_ (threshold) $\Theta$.
![[alberi-decisionali-caso-continuo-1.png]]

Il problema diventa poi _come scegliere le soglie_... Potrei guardare il dataset, che e' comunque finito, e usare i valori assunti dalla feature come intervallo entro cui stabilire le soglie.

## Resoconto
Gli aspetti positivi sono i seguenti:
- modello explainable;
- poco preprocessing;
- costo predittivo basso (ricerca nell'albero);
- utilizzabile sia con features discrete che continue;

mentre quelli negativi:
- rischio elevato di overfitting;
- selezione degli attributi instabile al variare del dataset;
- facile costruire alberi profondamente sbilanciati --> specialmente con classi dominanti;

E' per questa ragione, che di solito gli alberi decisionali sono utilizzati all'interno di [[Random forest|random forests]].

## Referenze