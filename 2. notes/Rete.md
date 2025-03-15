---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
  - topic/ottimizzazione-combinatoria
date: 27-09-2024 16:16:10
links:
  - "[[Lecture 18092024131539]]"
  - "[[Lecture 20092024132015]]"
  - "[[Lecture 05032025091441]]"
---
# Rete
---
## Introduzione
> Una **rete** di calcolatori è un insieme di dispositivi di calcolo:
> - _autonomi_, in grado di fare decisioni in modo autonomi
> - _interconnessi_, in grado di parlare tra di loro grazie a linee di comunicazione

Per esempio, la _rete telefonica non è una rete di calcolatori_: non sono autonomi. La rete internet invece lo è. Ma lo è anche banalmente _due telefoni connessi tra di loro che si trasmettono informazioni in modo autonomo_ (il numero minimo è 2).
![[rete-generica.png]]

## Motivazioni
Una rete può essere creata per:
- la _comunicazione tra utenti_
- la _comunicazione tra calcolatori_

### Comunicazione tra utenti
Le reti nascono storicamente per la condivisione di informazioni e risultati scientifici, quindi per pura comodità.

Lo scambio di risorse "fisiche" si è col tempo sempre più traslato verso uno scambio di risorse software, meglio conosciute sotto il nome di _servizi_ (e-mail, [[Web|WWW]], ecc...).

### Comunicazione tra calcolatori
Le stampanti contribuirono molto all'evoluzione delle reti intesa come comunicazione tra calcolatori. Era impensabile infatti associare ad ogni utente una stampante, e si pensò allora di condividerne una per più utenti: _nasceva l'esigenza di condividere [[Risorsa|risorse]] di rete_.

L'innovazione tecnologica portò alla nascita del _calcolo distribuito_ e dei _sistemi scalabili_. Si ricorda il progetto **SETI@home** come primo esempio di calcolo distribuito che sfruttava i principi della scalabilità per suddividere il lavoro tra più macchine.

## Evoluzione
La prima rete nasce nel 1969, da un esperimento che prevedeva una connessione tra 4 calcolatori di 4 differenti università americane. La linea usata era quella telefonica, e per _trasferire così i bit nel canale telefonico_ si usava un dispositivo chiamato [[INP]] (prototipo di [[Modem|modem]]).

La crescita dei dispositivi connessi ad internet, inflazionata da [[IoT]] (Internet of Things), è _quadratica se non esponenziale_, tanto che si prevedono entro il 2025 oltre 60 miliardi di dispositivi.

## Componenti
Per connettere un calcolatore alla rete c'è bisogno di un _insieme minimo di componenti hardware e software_:
- _[[Scheda di rete|scheda di rete]]_
- _[[Mezzo di trasmissione|mezzo di trasmissione]]_
- _[[Connettore di rete|connettore di rete]]_
- _protocolli di rete_, ossia regole implementate sottoforma di software del calcolatore per garantire compatibilità e corretta gestione della comunicazione

## Matematica
> Nell'ambito matematico, una rete e' un [[Grafo|grafo]] $G = (N, A)$ [[Grafo orientato|orientato]] (solitamente) e [[Grafo pesato|pesato]].
> Gli archi sono interpretabili come canali in cui fluiscono oggetto rappresentati da grandezze
> - _discrete_ (per passeggeri, veicoli, ecc...)
> - _continue_ (per fluidi, ecc...)
> 
> I nodi, invece, indicano i punti di ingresso o di uscita della rete.

### Terminologia
#### Sbilanciamento
Ad ogni nodo $i \in N$ e' associato un **fattore di sbilanciamento $b_{i} \in \mathbb{R}$**, che puo' essere:
- _positivo_ --> il nodo richiede che arrivi del flusso e segnala la sua uscita, e $b_{i}$ viene detto _domanda_ di $i$; e' un **nodo di output**;
- _negativo_ --> il nodo segnala l'entrata di un certo flusso, e $b_{i}$ viene detto _offerta_ di $i$; e' un **nodo di input**;
- _nullo_ --> la quantita' di flusso entrante e uscente e' la stessa; e' un **nodo di trasferimento**.

<u>Nota bene</u>: _indichiamo lo sbilanciamento di ogni nodo con un arco fittizio su cui scriviamo $b_{i}$_, l'importante è che non sia collegato a niente, altrimenti si confonde con gli archi veri.

#### Archi
Ad ogni arco $(i, j) \in A$ associamo:
- _costo_ $c_{ij}$ indica quanto costa per un'unità di bene attraversare il canale (può anche essere negativo);
- _capacità inferiore_ $l_{ij}$ ossia un limite inferiore alla quantità di beni che possono fluire sul canale;
- _capacità superiore_ $u_{ij}$ ossia un limite superiore alla quantità di beni che possono fluire sul canale;

![[problema-di-rete.png]]

## Referenze
- [[Classificazione delle reti]]
- [[Prestazione delle reti]]
- [[Infrastruttura di rete]]
- [[Topologia di rete]]