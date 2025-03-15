---
tags:
  - category/note
  - status/finished
  - topic/ottimizzazione-combinatoria
date: 02-03-2025 15:44:30
links:
  - "[[Lecture 24022025091339]]"
  - "[[Lecture 26022025091753]]"
---
# Vincoli di semi-assegnamento
---
## Introduzione
> I **vincoli di semi-assegnamento** sono vincoli solitamente usati nella [[Programmazione lineare intera|programmazione lineare intera]] per esprimere situazioni in cui e' necessario assegnare oggetti a luoghi. A differenza dei [[Vincoli di assegnamento|vincoli di assegnamento]], in questo caso **si impone solo che un oggetto sia assegnato a un solo luogo**, ma **non che a un luogo sia assegnato un solo oggetto**.
> In formule, si tiene soltanto la sommatoria sui luoghi fissato un oggetto:
> $$\sum\limits_{j=1}^{m} x_{ij} = 1$$

Se ogni oggetto puo' essere assegnato a uno specifico sottoinsieme di luoghi, allora si parla di [[Insiemi ammissibili|insiemi ammissibili]].

## Esempi
### Problema dei data center
- abbiamo $n$ server $1, \cdots, n$
- ogni server $i$ può lavorare in $m_{i} \in \mathbb{N}$ modalità operative diverse
- nella modalità $j \in \{1, \cdots, m_{i}\}$, il server $i$ riesce ad eseguire un numero di istruzioni al secondo pari a $S_{ij}$, consumando $W_{ij}$ watt
- vogliamo minimizzare il numero di watt complessivi del data center, garantendo però che questo offra un numero minimo di istruzioni al secondo pari a $k$
- risoluzione
	- variabili
		- $x_{ij} = \begin{cases} 1 & \text{server i usato secondo modalità j} \\ 0 & \text{altrimenti} \end{cases}$
		- $x_{ij} \in \mathbb{N}$
	- vincoli
		- sicuro almeno uno di semi-assegnamento, perché ogni server può lavorare solo in una modalità operativa, quindi $\forall i,  1 \leq i \leq n \ \ \ \sum\limits_{j=1}^{m_{i}} x_{ij} = 1$
		- $\sum\limits_{i=1}^{n} \sum\limits_{j=1}^{m_{i}} x_{ij} S_{ij} \geq k$
			- nota bene: avremmo potuto definire $p_{i} = \sum\limits_{j=1}^{m_{i}} x_{ij} S_{ij}$
		- $\forall 1 \leq i \leq n, \forall j \in \{1, \cdots, m_{i}\} \ \ \ 0 \leq x_{ij} \leq 1$
	- funzione obiettivo
		- $\min{\sum\limits_{i=1}^{n} \sum\limits_{j=1}^{m_{i}} x_{ij} W_{ij}}$

### Problema del docente di informatica
- progetti $t_{1} \leftarrow 1, \cdots, t_{n} \leftarrow n$ (sono i tempi di compilazione di ogni progetto)
- pc $1, \cdots, m$
- ogni pc può compilare qualunque progetto, in modalità sequenziale
- le prestazioni dei pc sono identiche
- vogliamo assegnare i progetti ai pc in modo da minimizzare il tempo complessivo (parallelo) di compilazione
- svolgimento
	- variabili
		- $x_{ij} = \begin{cases} 1 & \text{se il progetto i è compilato tramite il pc j} \\ 0 & \text{altrimenti} \end{cases}$
		- $x_{ij} \in \mathbb{N}$
		- $y =$ "limitazione superiore ai tempi di calcolo degli $m$ pc"
	- vincoli
		- vincolo di semi-assegnamento: $\forall i \sum\limits_{j=1}^{m} x_{ij} = 1$
		- $y \geq \sum\limits_{i=1}^{n} x_{ij} t_{i} \ \ \ \forall j$
	- funzione obiettivo
		- naive: $\min (\max_{j} \sum\limits_{i=1}^{n} x_{ij} t_{i})$, ma $\max$ non è una funzione lineare
		- per simulare questa cosa usiamo la variabile usiliaria $y$
		- reale: $\min y$
	- nota bene: di solito, **quando la funzione obiettivo non risulta lineare, si crea una nuova variabile associata a un vincolo che esprima quella non linearità**

## Referenze