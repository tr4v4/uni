---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 30-11-2023 16:44:00
links:
  - "[[Lecture 29112023131955]]"
  - "[[Lecture 30112023091742]]"
---
# Generalizzazione
---
## Introduzione
> La **generalizzazione** è un processo volto ad ottenere da una definizione o una relazione che si applica a certi casi una versione più [[Astrazione|astratta]] applicabile anche ad altri casi.

### Esempio in matematica
Presi ad esempio i due seguenti teoremi
$$\forall e \in \mathbb{N}. ((\forall x. x + e = x) \implies e = 0)$$
$$\forall e \in \mathbb{Z}. ((\forall x. e * x = x) \implies e = 1)$$
possiamo notare che hanno una struttura comune che può essere generalizzata nel **teorema G**:
$$\forall \mathbb{A}. \forall \circ : \mathbb{A} \times \mathbb{A} \to \mathbb{A}. \forall e_{r}, e_{l} \in \mathbb{A}. \ \ (\forall x. x \circ e_{r} = x) \land (\forall x. e_{l} \circ x = x) \implies e_{l} = e_{r}$$

Infatti quest'ultimo ci sta dicendo, a parole, che **se un'operazione binaria $\circ$ su $\mathbb{A}$ ha sia un [[Elemento neutro|elemento neutro]] $e$ a sinistra che uno a destra, allora questi coincidono**.

Questa generalizzazione non solo ci consente di esprimere le proprietà dei due precedenti teoremi, che di fatto si dicono _istanze di G (teorema)_, ma _ci permette di individuarne di altre_.

Per esempio si ha l'istanza
$$\forall e \in \mathbb{B}. ((\forall b. e \& b = b) \implies e = true)$$
che ci dice che $true$ è un elemento neutro (sia a destra che ha sinistra) dell'operatore $\&$ ([[AND]]).

Si scopre inoltre che _per certi operatori il teorema non è verificato_, come per la divisione $/$, che ha un solo elemento neutro a destra: $1$, infatti $4/1= 4$ ma $1/4 \neq 4$. E questo ci porta alla formulazione di un secondo **teorema H**: **se $\circ$ è un'operazione commutativa, allora se ha un elemento neutro $e$ a destra o a sinistra allora tale elemento è neutro**.

E a partire da questo si può andare avanti e scoprire per esempio che per G si ha che **se l'elemento neutro $e$ esiste, allora è unico**, che insieme ad H diventa: **se l'elemento neutro $e$ di un'operazione commutativa esiste, allora esso è unico**.

### Esempio in informatica
Consideriamo le due funzioni in [[Haskell]]:
```haskell
-- Data una lista di interi, restituirne la somma
sum [] = 0
sum (n:l) = n + sum l

-- Data una lista di booleani, restituirne la congiunzione
conj [] = True
conj (b:l) = conj l && b
```

Risolvono problemi simili con soluzioni simili, attraverso la [[Ricorsione strutturale|ricorsione strutturale]], ma non uguali (considerando l'ordine di somma e congiunzione).

Possiamo definire una funzione che generalizzi `sum`:
```haskell
foldr op e [] = e
foldr op e (n:l) = op n (foldr op e l)
```
dove:
- `op` è l'operatore `+`
- `e` è l'elemento neutro `0`

La somma di una lista di interi allora diventerà un'_istanza di `foldr`_, e allo stesso modo otterremo una versione diversa (con congiunzione a sinistra) di `conj`:
```haskell
sum = foldr (+) 0
conj' = foldr (&&) True
```

Se generalizzassimo invece `conj`, otterremmo:
```haskell
foldl op e [] = e
foldl op e (n:l) = op (foldl op e l) n
```
dove:
- `op` è l'operatore `&&`
- `e` è l'elemento neutro `True`

Per cui avremmo `conj` come _istanza di `foldl`_ e una versione modificata (con somma a destra) di `sum`:
```haskell
conj = foldl (&&) True
sum' = foldl (+) 0
```

Fatte le due seguenti generalizzazioni (`foldr` e `foldl`), possiamo analizzare delle proprietà delle istanze ad un livello più astratto. Pensiamo per esempio alla proprietà di `sum`:
$$\text{sum (l1 ++ l2) = sum l1 + sum l2}$$
Possiamo analizzarla ad un livello più alto, infatti essendo `sum` istanza di `foldr` ecco che si ha:
$$\text{foldr op e (l1 ++ l2) = op (foldr op e l1) (foldr op e l2)}$$
E <u>attenzione</u>, perché per poter dimostrare quest'ultimo teorema _si deve assumere che **`op` sia associativa** ed **`e` il suo elemento neutro a sinistra**_.

In poche parole **per dimostrare delle generalizzazioni è necessario rendere esplicite delle assunzioni che per le loro istanze erano implicite**. Questo ci aiuta a comprendere a fondo le proprietà delle istanze.

Si scopre anche che il teorema vale per `foldr` ma NON per `foldl`: **le due generalizzazioni non sono equivalenti**.

#### Risultati
Abbiamo appreso che la generalizzazione `foldl` è:
- _utile_: per esempio posso calcolare il prodotto dei numeri di una lista chiamando `foldl * 1`, o per trovare il minimo `foldl min max_int`
- _chiarificante_: spiega infatti in che ordine sono processati gli elementi
- _informativa_: tramite essa esplicitiamo delle ipotesi implicite

Ma esistono anche generalizzazioni che non sono utili, come funzioni che generalizzano solo su specifici casi attraverso [[Comandi condizionali|costrutti condizionali]]: non possono essere riutilizzate in altri casi.

Gli stessi risultati si possono ottenere attraverso le [[Type classes|type classes]], ovvero l'utilizzo di strutture algebriche in programmazione, così come l'applicazione dei [[Morfismo|morfismi]], sempre in programmazione.

## Referenze
- [[Astrazione]]