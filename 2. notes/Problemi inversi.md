---
tags:
  - category/note
  - status/finished
  - topic/calcolo-numerico
date: 10-11-2024 17:59:53
links:
  - "[[Lecture 04112024131513]]"
---
# Problemi inversi
---
## Introduzione
> Per **problema inverso** si intende una _gamma di problemi modellati matematicamente dalla necessità, a partire dall'output e da un modello, di trovare l'input_.

Si trovano in svariate applicazioni della fisica, se per esempio si considera come input la causa, come modello la fisica stessa e come output l'effetto.

## Caso lineare
Solitamente, se consideriamo un fenomeno _lineare_, allora possiamo modellizzare il problema come: _x -> A -> y_, ovvero
$$Ax = y$$
dove:
- $A$ è la [[Matrice|matrice]] che rappresenta il modello, o il sistema di acquisizione;
- $y$ sono i dati acquisiti dal modello $A$;
- $x$ sono la causa di questi dati.

Il problema inverso di ciò consiste nel conoscere il modello $A$, l'output $y$, e trovare l'input $x$: _si vuole banalmente risolvere il [[Sistema lineare|sistema lineare]]_.

### Rumore
Nella realtà, i dati reali $y$ sono sempre affetti da un errore, in gergo **rumore**, modellizzato dal [[Vettore|vettore]] $\delta$. Questo avviene perché _i sistemi di acquisizione sono strumenti fisici, che per natura sono affetti da errore_ (senza considerare la digitalizzazione della misura analogica).

Per cui ciò che realmente si cerca di risolvere è il sistema
$$Ax = y + \delta = y^{\delta}$$
e questo errore dev'essere in qualche modo gestito!

### Risoluzione
La **maggior parte dei problemi inversi lineari ha una matrice $A$ [[Errore inerente|mal condizionata]]**, derivante dalle caratteristiche del sistema di acquisizione (come le grandi dimensioni). Per questo, anche se il rumore $\delta$ è piccolo, la risoluzione del sistema $Ax = y^{\delta}$ comporterebbe risultati completamente sbagliati.

Per cui, non possiamo usare gli [[Algoritmi per la risoluzione di sistemi lineari|algoritmi standard per la risoluzione di sistemi lineari]] in questo tipo di problemi (come la [[Fattorizzazione LU|fattorizzazione LU]] o [[Fattorizzazione di Cholesky|fattorizzazione di Cholesky]]).

Si preferisce, invece, **risolvere i problemi inversi passando per i [[Problema dei minimi quadrati|minimi quadrati]]**. Questo infatti ci dà la possibilità di usare un modello $A$ non quadrato ($m > n$), e di tenere conto dell'errore $\delta$!
Risolviamo quindi $$\min_{x} {\|Ax - y^{\delta}\|_{2}}^{2}$$
In particolare, sappiamo che _se la matrice $A$ ha rango massimo possiamo sia risolvere le equazioni normali con Cholesky sia usare la [[Fattorizzazione ai valori singolari|SVD]], mentre se $A$ non ha rango massimo possiamo usare solo quest'ultima_. Tuttavia, passare alle equazioni normali e usare Cholesky produrrebbe gli stessi problemi degli algoritmi di risoluzione standard: infatti **si utilizza sempre la decomposizione ai valori singolari, perché non viene dominata dal mal condizionamento di $A$ ed è possibile separare i dati $y$ dal rumore $\delta$**.

#### Naive
L'approccio naive consiste allora di risolvere il problema dei minimi quadrati tramite la SVD "standard". Considerato il problema $\min_{x} {\|Ax - y^{\delta}\|_{2}}^{2}$ e decomposta $A$ in $A = U \Sigma V^{T}$, la soluzione si calcola come
$$x^{*} = \sum\limits_{i=1}^{n} \frac{u_{i}^{T}y^{\delta}}{\sigma_{i}} v_{i}$$
Il risultato? _Inaccettabile_: la soluzione $x^{*}$ non è neanche lontanamente vicina a quella effettiva (considerando un [[Problema test|problema test]]), e _soprattutto è caratterizzata da delle forti oscillazioni_.

Cerchiamo di capire da dove derivano. Si vuole trovare la soluzione al problema
$$\min_{x} {\|Ax - y - \delta\|_{2}}^{2}$$
usando la sommatoria $x^{*} = \sum\limits_{i=0}^{n} \frac{u_{i}^{T}y^{\delta}}{\sigma_{i}} v_{i}$. Se dividiamo $y^{\delta}$ in $y^{\delta} = y + \delta$, otteniamo
$$x^{*} = \sum\limits_{i=1}^{n} \frac{u_{i}^{T}y^{\delta}}{\sigma_{i}} v_{i} = \sum\limits_{i=1}^{n} \frac{u_{i}^{T}y}{\sigma_{i}}v_{i} + \sum\limits_{i=1}^{n} \frac{u_{i}^{T}\delta}{\sigma_{i}}v_{i}$$
e _se la prima sommatoria è quella che produce il risultato desiderato, la seconda è proprio la causa delle oscillazioni_.

Lo si capisce dal grafico delle [[Condizioni discrete di Picard|condizioni discrete di Picard]].

#### Realtà
Gli algoritmi che risolvono problemi inversi lineari, utilizzano dei _metodi detti di [[Regolarizzazione|regolarizzazione]]_. In particolare se ne citano 3:
- _[[Fattorizzazione ai valori singolari troncata|TSVD]]_;
- _[[Regolarizzazione alla Tikhonov|regolarizzazione alla Tikhonov]]_;
- _[[Principio di massima discrepanza|principio di massima discrepanza]]_.

## Applicazioni
I problemi inversi sono spesso visti come il ponte che unisce la matematica ai dati: a partire dai dati osservati voglio determinare i parametri del modello, ossia la causa di questi dati.

Le applicazioni sono tantissime, tra cui:
1. [[Imaging|imaging]]
2. [[Geofisica|geofisica]]
3. [[Signal processing|signal processing]]

## Referenze