---
tags:
  - category/note
  - status/finished
  - topic/introduzione-all-apprendimento-automatico
date: 11-10-2025 13:51:53
links:
  - "[[Lecture 10102025131023]]"
  - "[[Lecture 16102025131029]]"
---
# Naive Bayes gaussiano
---
## Introduzione
> Il **Naive Bayes gaussiano** e' la versione del [[Naive Bayes|naive Bayes]] in cui le [[Features di un dato|features]] $X_{i}$ sono continue. L'approccio tradizionale consiste nel supporre che $\mathbb{P}(X_{i} | Y)$ abbia una [[Distribuzione normale|distribuzione normale]].

Si fa ciò perché la **distribuzione normale è quella che ha maggiore [[Entropia|entropia]]**.

### Esempio
Supponiamo di voler classificare i _cani_ dai _gatti_ sulla base del loro _peso_. Assumiamo che questo sia rappresentato da una [[Variabile aleatoria continua|variabile aleatoria continua]] $X$, e che la sua distribuzione sia appunto una normale.

A questo punto assumiamo di essere riusciti a calcolare i parametri della gaussiana di $X$ che modellizza il peso dei cani e il peso dei gatti, ossia:
- $\mu_{1}, \sigma_{1}$ --> parametri peso cani;
- $\mu_{2}, \sigma_{2}$ --> parametri peso gatti;

dove ricordiamo che $\mu = \mathbb{E}[X]$ (il [[Valore atteso|valore atteso]]) e $\sigma^{2} = Var[X]$ (la [[Varianza|varianza]]).

Il grafico delle due distribuzioni risulta essere, per esempio, il seguente:
![[naive-bayes-gaussiano-esempio.png]]

La curva blu è la [[Densita' continua|densità continua]] del peso dei gatti (ovviamente); la curva arancione invece è quella dei cani.

A questo punto, la classificazione si fa nientemeno che impostando una **decision boundary**: una riga verticale che separa le due curve nel "miglior" modo possibile. Se il peso di un nuovo animale supera la decision boundary, allora è un cane, altrimenti è un gatto.

Questo chiaramente dà luogo a molteplici errori: c'è per esempio una bassa ma esistente probabilità che un gatto abbia un peso abbastanza alto da essere classificato come cane; così come è presente una ben più ampia probabilità che un cane sia classificato come un gatto. Questo fenomeno avviene in quanto **le curve si intersecano**, e dà luogo alle 4 seguenti definizioni:
- **True Positive** (**TP**) - il modello classifica _correttamente_ come _positivo_ (cane);
- **True Negative** (**TN**) - il modello classifica _correttamente_ come _negativo_ (gatto);
- **False Positive** (**FP**) - il modello classifica _erroneamente_ come _positivo_ (in realtà era un negativo, gatto);
- **False Negative** (**FN**) - il modello classifica _erroneamente_ come _negativo_ (in realtà era un positivo, cane);

![[naive-bayes-gaussiano-errori.png]]

## Metriche
Sulla base delle definizioni di TP, TN, FP e FN, si definiscono le seguenti metriche.

### Accuratezza
Ci dice **quante istanze sono state classificate correttamente** (indipendentemente se in positivo o in negativo):
$$\text{Accuracy} = \frac{TP + TN}{ALL}$$

### Precisione
E' applicabile ai positivi o ai negativi. Nel caso dei positivi, per esempio, ci dice **quanti positivi sono stati classificati correttamente rispetto a quanti sono stati classificati come positivi**:
$$\text{Precision} = \frac{TP}{TP + FP}$$

### Richiamo
Anche questo applicabile ai positivi o ai negativi. Per i positivi, per esempio, ci dice **quanti positivi sono stati classificati correttamente rispetto a quanti erano effettivamente i positivi**:
$$\text{Recall} = \frac{TP}{TP + FN}$$

### F1
E' la [[Media armonica|media armonica]] tra precisione e richiamo:
$$\text{F1} = 2\frac{\text{Precision} \cdot \text{Recall}}{\text{Precision} + \text{Recall}}$$

### Applicazioni
Notiamo lo stretto ma ortogonale rapporto tra la precisione e il recall.
> Se spostiamo la soglia di classificazione nel grafico, aumentiamo la precisione, ma a scapito del richiamo: ci sbagliamo sicuramente di meno perché abbiamo una soglia molto alta di classificazione, e quindi **i classificati positivi saranno molto simili a quelli classificati correttamente come positivi**; tuttavia **scarteremo anche un sacco di positivi reali, che classificheremo erroneamente come negativi**, diminuendo il richiamo.

## Funzionamento
Assumiamo che per ogni valore $y_{k}$ di $Y$ la variabile aleatoria $\mathbb{P}(X_{i}|Y = y_{k})$ abbia una distribuzione normale $$\mathcal{N}(x|\mu_{ik}, \sigma_{ik}) = \frac{1}{\sigma_{ik}\sqrt{2\pi}}e^{- \frac{(x-\mu_{ik})^{2}}{2 \sigma_{ik}^{2}}}$$
### Training
La fase di training consiste semplicemente nello stimare i parametri
$$\mu_{ik} \ \ \ \sigma_{ik} \ \ \ \pi_{k} = \mathbb{P}(Y = y_{k})$$
Per farlo possiamo, per esempio, usare sempre la [[MLE]].

### Classificazione
La classificazione di un nuovo dato $x^{new} = (a_{1}, \cdots, a_{n})$ diventa
$$Y^{new} = \arg\max_{k} \pi_{k} \cdot \prod_{i} \mathcal{N}(a_{i} | \mu_{ik}, \sigma_{ik})$$

## Referenze