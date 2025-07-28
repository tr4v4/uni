---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 13-07-2025 16:27:28
links:
  - "[[Lecture 29042025152102]]"
  - "[[Lecture 05052025111914]]"
  - "[[Lecture 06052025152121]]"
---
# MAC
---
## Introduzione
> Il **protocollo MAC** (**Media Access Control**) è un [[Protocollo di rete|protocollo di rete]] del [[Livello MAC-LLC|livello MAC-LLC]] che si occupa della _gestione dell'accesso al mezzo trasmissivo in una rete locale_.

## Caso Ethernet
Il protocollo MAC nelle reti cablate si chiama [[Ethernet]], definito dallo standard IEEE 802.3.

## Caso Wi-Fi
Il protocollo Ethernet non potrebbe funzionare sulle reti wireless: questo perche' **ogni comunicazione e' in broadcast**, quindi _il rischio di collisioni è altissimo e si rischia di rallentare molto le comunicazioni_.

Oltretutto, nel mondo delle comunicazioni radio, non e' possibile fare **collision detection** (_CD_), per via del fatto del decadimento quadratico (se non cubico) del segnale ([[Path loss|path loss]]!). Un'idea per riacquisire CD potrebbe essere quella di _inviare_, insieme ai dati, una "_nota di fondo_". Ascoltando quest'ultima, e' possibile accorgersi di collisioni: ma **viene sprecato un intero canale, e' troppo costoso**! In aggiunta a questo, l'impossibilita' di fare CD e' anche dovuta al cosiddetto [[Problema del terminale nascosto|problema del terminale nascosto]]: _se due dispositivi comunicano a un terzo condiviso, possono non accorgersi che lo stanno facendo contemporaneamente, magari sono troppo distanti, la collision detection può non funzionare_.

Bisogna inventare qualcosa di alternativo alla collision detection: si chiamera' **collision avoidance** (_CA_).

### Protocolli
I protocolli che implementano il protocollo MAC wireless si dividono in categorie:
- **contention free**
	- _centralized static_
		- c'è un coordinatore, il "re", che controlla tutto;
		- per comunicare devo dire al re quanto devo trasmettere;
		- questo può fare TDMA, FDMA o CDMA (con quest'ultimo assegna un chipping sequence ad ogni comunicante);
		- a questo punto il coordinatore alloca le risorse, quindi i tempi di trasmissione staticamente;
		- il re e' [[SPOF]];
	- _distributed dynamic_
		- non c'è coordinatore, le risorse sono allocate dinamicamente (trasmette di più chi ha più cose da trasmettere);
		- è basata su token, parlo solo se ho il token, serve una lista ciclica tra gli host, creata dal sistemista o dal protocollo;
		- non funziona: il token viene perduto troppo spesso (si tratta pur sempre di trasmissioni wireless!);
- **distributed contention based**
	- _deterministic_
		- si hashano i [[Indirizzo MAC|MAC address]] delle schede di rete -> il valore dell'hash è il canale;
		- questo ovviamente non garantisce la non collisione, ma appena me ne accorgo cambio il canale;
	- _probabilistic_
		- controllo della contesa (_contention control_);
		- si basa sull'accesso casuale, sullo stile di Ethernet;
		- se ho capito che ci sono collisioni o c'è alto rischio, si applica meccanismo di controllo della contesa o della risoluzione della contesa (aspetto tempo random);

![[wireless-mac-protocols.png]]

Fondamentalmente, nelle comunicazioni _contention free_, in qualche modo (indipendentemente o tramite un coordinatore) **si stabilisce chi può trasmettere e quando, evitando collisioni**. Invece, nelle comunicazioni _contention based_, **si lascia che tutti possano trasmettere, ma si gestiscono le collisioni**.

L'idea del [[Wi-Fi]] (IEEE 802.11) è di _unire le due categorie_! Il coordinatore centrale (di solito [[Access point|access point]]) permette di evitare le collisioni, ma se il coordinatore non c'è, si passa al probabilistic, ossia si parla sgomitando, parlando dinamicamente. Questa è una soluzione _fallback_.

### Storia
Sin dal principio, l'idea di implementazione della _collision avoidance_ (visti i problemi della collision detection), consisteva nel cercare di **ridurre il tempo di vulnerabilita' dei frame**, ossia il tempo in cui possono avvenire le collisioni.
Tutti i seguenti protocolli sono di tipo _probabilistic_ (contention based).

#### Protocolli temporali
I protocolli che agiscono sul dominio del tempo sono:
- [[ALOHA]]
- [[Slotted ALOHA]]
- [[CSMA]]
- [[Slotted CSMA]]

![[mac-wireless-time-protocols-comparison.png]]

#### Protocolli spaziali
I protocolli che agiscono sul dominio dello spazio sono:
- [[RTS-CTS]] - meccanismo di base per i successivi
- [[MACA]]
- [[MACAW]]

## Protocollo
Il protocollo MAC attuale, usato nel Wi-Fi, combina alcuni dei protocolli precedenti. Fondamentalmente si alterna tra 2 fasi:
- [[DCF]]
- [[PCF]]

![[protocollo-mac.png]]

Questi due protocolli, [[Mutua esclusione|mutualmente esclusivi]], possono coesistere mediante il cosiddetto **superframe**, una struttura temporale che permette l'alternanza tra i due protocolli.

### Alternanza
![[pcf-dcf-cycle.png]]

Il _CFP_ e' il periodo in cui la comunicazione e' senza contesa, centralizzata; il _CP_ e' il periodo in cui la comunicazione e' con contesa, distribuita. E' importante che il _CFP repetition interval_ contenga anche il CP per **consentire ai nuovi entranti nella rete di mettersi in lista dal coordinatore** per poter comunicare.

Ciclo:
- CFP --> il coordinatore invia un **Beacon**, con cui avvisa che e' lui il coordinatore centrale, comunica il nome ([[SSID]]) e avvisa che per i prossimi tot. secondi, ci sarà un CFP;
- scade il CFP, il coordinatore si mette latente e "lascia che governi l'anarchia";
- quando il CFP repetition interval scade, il coordinatore manda il Beacon, zittendo tutti.

#### Beacon
Il Beacon, nel dettaglio, contiene anche i ricevitori e i trasmettitori durante il prossimo CFP. Quelli che non appartengono a questa lista vanno in **NAV** (_Network Allocation Vector_): mettono il dispositivo radio in stato di _idle_ per risparmiare energia.
Non sempre conviene andare in idle, perche' il risveglio non e' lineare e consuma molta energia. Infatti, all'interno del Beacon viene comunicato ad ogni host in NAV per quanto tempo non sara' coinvolto, in modo che questi _possano decidere se conviene andare in idle o meno_.

Ma **come fa il coordinatore a zittire tutti col Beacon**?

#### SIFS, PIFS, DIFS
Questi sono 3 intervalli di tempo (chiamati IFS, _Inter Frame Spaces_) usati per gestire le comunicazioni e l'alternanza tra DCF e PCF. Vale intanto che
$$\text{SIFS} < \text{PIFS} < \text{DIFS}$$
e che
- _dopo un SIFS_ può parlare
	- la _stazione pollata_ (in caso di PCF);
	- la _stazione interpellata_ (in caso di DCF o PCF, quando manda ACK);
- _dopo un PIFS_ può parlare l'_access point_, ed eventualmente prendere il controllo del canale (mandando un Beacon e poi i poll);
- _dopo un DIFS_ possono parlare _tutti_, parte il DCF.

Per costruzione, ovviamente, la differenza tra SIFS, PIFS e DIFS è fatta in modo tale da essere _superiore al propagation delay_, per evitare collisioni.
![[sifs-pifs-difs.png]]

Quindi in poche parole:
- dopo che avviene una trasmissione in DCF, il ricevente attende un SIFS poi manda l'ACK; quindi tutti aspettano un DIFS, e:
	- se entro un PIFS ($\subset$ DIFS) l'access point non manda un Beacon, allora c'e' ancora DCF (a cui ci si accede usando CSMA-CA con Binary Exponential Backoff);
	- se invece l'access point manda un Beacon, allora si passa a PCF, ossia il coordinatore centrale prende il controllo del canale e manda i poll; quando scade il CFP, e' sufficiente che l'access point aspetti un DIFS, e poi si torna in DCF.

## Referenze