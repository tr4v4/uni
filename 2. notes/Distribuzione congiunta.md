---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 11-10-2025 10:33:33
links:
  - "[[Lecture 09102025131347]]"
---
# Distribuzione congiunta
---
## Introduzione
> La **distribuzione congiunta** e' un modello di [[Machine learning|machine learning]] di classificazione basato sull'[[Approccio probabilistico|approccio probabilistico]].

Fondamentalmente e' proprio la [[Densita' congiunta discreta|densita' congiunta discreta]] di $n$ [[Variabile aleatoria discreta|variabili aleatorie]].

## Funzionamento
I passi sono i seguenti:
1. si _costruisce una tabella con tutte le possibili combinazioni dei valori delle features_;
2. _ad ogni combinazione si stima un valore di probabilita', anche detto parametro_ (tale quindi che la somma faccia 1).

Per cui, si capisce, che **se abbiamo $n$ features booleane dobbiamo stimare $2^{n} - 1$ parametri** (l'ultima combinazione sara' il complemento).

Una volta che abbiamo questa tabella di parametri, siamo in grado di _stimare la probabilita' di qualunque evento fornito come combinazione logica delle features_, in questo modo:
$$\mathbb{P}(E) = \sum\limits_{row \in E}{\mathbb{P}(row)}$$

Possiamo anche facilmente calcolare la probabilita' condizionata $\mathbb{P}(E_{1}|E_{2})$, nel seguente modo:
$$\mathbb{P}(E_{1}|E_{2}) = \frac{\mathbb{P}(E_{1} \cap E_{2})}{\mathbb{P}(E_{2})} = \frac{\sum\limits_{row \in E_{1} \cap E_{2}} \mathbb{P}(row)}{\sum\limits_{row \in E_{2}} \mathbb{P}(row)}$$

### Esempio
![[distribuzione-congiunta-1.png]]

Se volessimo calcolare la probabilita' che un maschio sia povero, allora cerchiamo $\mathbb{P}(M, poor)$, e questa e' data dalla somma delle probabilita' nelle righe in cui i maschi sono poveri:
$$\mathbb{P}(M, poor) = 0.33 + 0.13 = 0.46$$

## Machine learning
Ma nel machine learning, come si utilizza questo metodo? Ossia, dove sta l'approccio probabilistico?

E' molto semplice! Se vogliamo calcolare $\mathbb{P}(Y|X)$, ci basta **elencare le features $X$ in forma tabellare, e associare a ogni combinazione di feature il rispettivo $\mathbb{P}(Y = y_{i} | X = x_{j})$**.

Nell'esempio precedente, vediamo `health` come l'output $Y$, ossia ci vogliamo calcolare la probabilita' condizionata
$$\mathbb{P}(Y = wealth | X_{1} = gender, X_{2} = orelav.)$$
Ci uscirebbe, _stimati i parametri_, una tabella del genere:
![[distribuzione-congiunta-2.png]]

### Problemi
Questi parametri sono probabilita'... Per ottenere, quindi, valori statisticamente significativi, _dobbiamo avere molti esempi per ogni combinazione_.

Inoltre, il **numero di features e la loro molteplicita', sono un grande limite al modello**: se per esempio prendiamo la classificazione delle immagini del dataset [[MNIST]], abbiamo immagini `28 x 28`, e se consideriamo ogni pixel una feature, allora abbiamo `784` features (+ 10 colonne corrispondenti alle classi), ovvero una tabella con $2^{784}$ righe (se consideriamo i pixel con valori booleani). Assolutamente **irrealizzabile nella pratica**...

Il problema si risolve (circa) usando proprio la [[Formula di Bayes|formula di Bayes]]: i [[Classificatori bayesiani|classificatori bayesiani]].

## Referenze