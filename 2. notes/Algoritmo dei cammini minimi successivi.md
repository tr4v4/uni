---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 24-03-2025 20:52:29
links:
  - "[[Lecture 19032025092241]]"
  - "[[Lecture 20032025131726]]"
---
# Algoritmo dei cammini minimi successivi
---
## Introduzione
> L'**algoritmo dei cammini minimi successivi** è un [[Algoritmo|algoritmo]] per risolvere il [[Problema del flusso di costo minimo|problema del flusso di costo minimo]], basata sulla nozione di _pseudoflusso minimale_.

## Algoritmo
1. definiamo $x$ uno pseudoflusso minimale;
2. se lo sbilanciamento complessivo è 0 ($g(x) = 0$) terminiamo e restituiamo $x$;
3. cerchiamo un cammino di costo minimo $P$ da un nodo $i \in O_{x}$ e $j \in D_{x}$; se non esiste termina perché il problema è vuoto;
4. $x = x(P, \min\{\theta(P, x), e_{x}(i), - e_{x}(j)\})$;
5. torna al punto 2.

Si dimostra che in questo algoritmo _lo pseudoflusso rimane minimale ad ogni passo_.

### Funzionamento
Il primo punto consiste nel trovare "manualmente" uno pseudoflusso minimale. Ma e' facile farlo se non si bada agli sbilanciamenti! Basta considerare lo pseudoflusso $x$ definito come
$$x_{ij} = \begin{cases} 0 & c_{ij} \geq 0 \\ u_{ij} & c_{ij} < 0 \end{cases}$$

E' ovvio intuitivamente, e si dimostra che e' uno pseudoflusso minimale perche' il [[Grafo residuo|grafo residuo]] $G_{x}$ non  conterra' archi di costo negativo --> di conseguenza non potra' avere cicli  aumentanti di costo negativo, e per [[Problema del flusso di costo minimo#Lemma|questo lemma]] si avra' che $x$ e' minimale.

Nel punto 3 si cerca un cammino di costo minimo: possiamo usare gli algoritmi sui [[Cammino minimo|cammini minimi]]. In particolare, il grafo residuo di ogni pseudoflusso, in quanto preservata la minimalita', non conterra' mai archi di costo negativo: si puo' sempre usare l'[[Algoritmo di Djikstra|algoritmo di Dijkstra]]!

## Correttezza
Dal [[Problema del flusso di costo minimo#Preservazione della minimalita'|teorema di preservazione della minimalita']] sappiamo che il flusso $x$ rimane minimale. Se l'algoritmo termina, allora significa $g(x) = 0$, ovvero che $x$ e' uno pseudoflusso minimale con sbilanciamento $e_{x}$ nullo --> e' un flusso di costo minimo!

## Terminazione
Se assumiamo che gli sbilanciamenti $b$ e le capacita' degli archi $u$ siano tutti interi, allora:
- lo pseudoflusso iniziale $x$ e' intero;
- la capacita' residua $\theta(x, P)$ rimane intera;
- lo pseudoflusso $x$ rimane intero ad ogni iterata;
- _ad ogni passo $g(x)$ diminuisce di almeno 1_.

Quindi, ci basta trovare un upperbound allo sbilanciamento iniziale $\bar{g}$. Ma vale, ovviamente, che
$$\bar{g} \leq \sum\limits_{b_{i} > 0} b_{i} + \sum\limits_{c_{ij} < 0} u_{ij}$$

Di conseguenza, le iterazioni dell'algoritmo saranno al piu' $\bar{g}$. Il costo computazionale di ogni iterazione e' dominato dalla ricerca di un cammino minimo, eseguibile in tempo $O(NA)$. Di conseguenza, l'algoritmo sara' di [[Complessità computazionale|complessita']]
$$O(\bar{g}NA)$$

## Referenze