---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 24-09-2024 17:14:05
links:
  - "[[Lecture 19092024151357]]"
---
# Web
---
## Definizione
> Il **web**, spesso conosciuto come **World Wide Web** (_WWW_), è un'_infrastruttura di internet_, un sistema per la _presentazione a schermo_ di _documenti multimediali_ e l'utilizzo di _link ipertestuali per la navigazione_.

## Accenni storici
Viene introdotto da [[Tim Berners-Lee]] negli anni '90, quando lavorando al [[CERN]] di Ginevra, si rese conto della necessità di semplificare la condivisione di informazioni di natura scientifica tra gli studiosi del centro di ricerca. Unì ciò che aveva a disposizione, ossia
- _[[Architettura client-server|architettura client-server]]_
- _ipertesto_
- _internet_

creando il web.

## Ruoli
### Client
Il client nel web è il **browser**, un visualizzatore di contenuti. All'inizio il browser consentiva solo di visualizzare, e non modificare i contenuti in visualizzazione. Prevedevano inoltre la possibilità di integrare dei plug-in per visualizzare formati "speciali". L'evoluzione dei browser questi a supportare un linguaggio di script lato client, [[Javascript]], il quale rese possibile lo sviluppo di _applicazioni web_.

### Server
Il server nel web è quell'attore che fa da **intermediario tra il file-system e le richieste che arrivano dai client**. In architetture più complesse il server può anche collegarsi ad _applicazioni server-side_ e agire dal browser come se l'applicazione fosse sul computer locale.

## Protocolli
I protocolli/standard di base che compongono il web sono:
- [[URI]] - standard per identificare in maniera generale risorse di rete e poterle specificare all'interno di documenti ipertestuali
- [[HTTP]] - il protocollo di comunicazione state-less[^1] e client-server per la trasmissione delle risorse ipertestuali
- [[HTML]]/[[XHTML]] (basato su SGML, ora XML) - un linguaggio specifico per la realizzazione dei documenti ipertestuali visualizzabili

## Evoluzioni
Il WWW ha attraversato diverse fasi evolutive che lo hanno portato ad essere quello che è oggigiorno. In particolare, se all'inizio i contenuti di ogni pagina web erano divisi per sezione (testo, immagini, video, audio, ecc...), per una questione di facilità di scrittura e di visualizzazione, ora i browser sono così evoluti da supportare vere e proprie applicazioni web:
- _inclusione di oggetti_: Mosaic è il primo browser a introdurre immagini in-line, quindi testo+immagini; inoltre Mosaic introduce i form, lasciando però sempre la logica applicativa server-side (quindi per un semplice controllo del form è lato server, con conseguente rallentamenti); Netscape introduce i plug-in, che mettono in crisi il settore per la sicurezza
- _client scripting_: per questo problema Netscape introduce LiveScript (ribattezzato Javascript), per realizzare applicazioni client-side; viene dopo standardizzato il linguaggio, dando vita a ECMAscript, padre del Javascript moderno e di tutti gli altri derivati
- _stili tipografici_: si forzava HTML per inserire formule matematiche o per modificare il font, finché non si introdusse un linguaggio apposito a gestire gli aspetti di visualizzazione del documento, CSS
- _gestione delle transazioni_: si supera lo state-less dell'HTTP perché le applicazioni si complicano, e quindi per gestire la continuità delle richieste si introducono i cookie; Ajax introduce XMLHTTPRequest, un meccanismo per richiedere informazioni HTTP (frammenti di contenuti) senza la navigazione da una pagina all'altra (API)
- _siti web dinamici_: le applicazioni server-side (CGI-BIN) evolvono e si fondono, diventando veri e propri linguaggi o ambienti di programmazione: PERL, ASP, PHP, Python, Ruby; queste applicazioni generano dinamicamente le pagine web, a seconda di informazioni richieste dall'utente; non appena approdano le librerie di accesso ai database (ODBC, JDBC, EJB, ActiveModel, ecc...) nasce l'architettura a tre livelli (user-interface, application logic, data storage); in definitiva il browser diventa l'interfaccia di eccellenza per applicazioni gestionali distribuite
- _strutturazione dei documenti_: HTML aveva limiti nella visualizzazione e nella strutturazione, la sua versione più astratta XML ha permesso di definire linguaggi di markup più adatti alla gestione di dati non sequenziali (come i paragrafi in HTML)
- _framework di sviluppo_: oggigiorno esistono ambienti integrati di sviluppo dotati di ricche API e librerie per la realizzazione semplificata di applicazioni client-side e server-side; in particolare Django per Python, Rails per Ruby, tutti i framework Ajax (Prototype, JQuery, Ext, Dojo, ecc...); GWT (Google Web Toolkit) è un framework che cercò di integrare i modelli di progettazione delle parti client-side e server-side, prevedeva un unico linguaggio di programmazione (Java) per lato server e lato client, per cui da Java si passava a Javascript per farlo leggere al browser, e questo creava problemi di complessità pazzeschi in fase di debugging
	- problema di interoperabilità tra browser: ECMAscript funziona su tutti, perché è lo standard, ma ogni browser ha la sua versione di Javascript --> i framework di sviluppo consentono di semplificare questo aspetto

### Mode del passato e del presente
Il mondo web, per via della sua varietà e forte evoluzione, ha incessantemente sfornato mode che hanno influenzato lo stile di molti siti e applicazioni web per molto tempo.

#### Trucchi di HTML
In passato HTML era estremamente elementare, limitando i programmatori a una scarsa personalizzazione della pagina. Questi non si diedero per vinti e svilupparono degli stratagemmi per ovviare a queste mancanze:
- si caricava l'immagine del testo con il font personalizzato (che non era personalizzabile in HTML) al posto del testo stesso --> problema per non vedenti
- _tabelle di layout_, un uso geniale ma sbagliatissimo per ottenere una grafica più sofisticata
- _spacer_ (single-pixel gif), spazi vuoti formati da immagini, inquinano la pagina
- _blockquote_
- _tag \<FONT\>_, mai stato standardizzato
- _frame_
- _estensioni di singoli browser (\<marquee\>)_, tradotto come sottopancia, movimento orizzontale di testo come sotto il giornalista

<u>Nota bene</u>: tutte queste tecniche sono state sostituite da standard di [[CSS]].

#### MEAN/MERN stack
I nuovi stack protocollari del web, in sostituzione a LAMP, sono [[MEAN]] e [[MERN]]. Il primo è composto dal seguente stack:
- MongoDB
- ExpressJS
- Angular
- NodeJs

Il secondo da:
- MongoDB
- ExpressJS
- React.js
- NodeJs

#### Component-based design
Si utilizzano delle vere e proprie estensioni di HTML, dei template con classi CSS e codice Javascript già pronte per l'utilizzo e completamente autosufficienti.

I framework più comuni sono:
- [[AngularJS]] è il primo framework, poi divenuto [[Angular]] (supportato da Google)
- [[React]] (supportato da Facebook)
- [[Vue]] (indipendente)

#### Altre mode
Tra le altre mode si ricordano:
- [[LAMP]];
- [[REST]];
- [[AJAX]];
- [[NodeJs]];
- _Semantic Web_;
- _Linked Data_ (concretizzato nel _Open Linked Data_);
- _Mobile first_ - si sviluppano le applicazioni prima con supporto mobile, poi per PC;
- _Responsive web design_ - ci sono nuovi schermi e dimensioni, è necessario rendere "responsive" la pagina web, cioè adattabile a ogni schermo al meglio;
- _Single page web sites_ - zero navigazione, o ridotta al minimo, tutto in una pagina;
- _Typescript_ - Javascript è molto odiabile, così si diffondono estensioni che risolve alcuni difetti di progettazione, tra cui Typescript: più rigido e rigoroso, aggiunge controlli sui tipi e altre cose (obbligatorio per Angular);
- _CLI_ - si usa la Command Line Interface per configurare un progetto web in modo veloce e automatico;
- _WebPack_ - è un web bundler, un compilatore che aggrega tutte le tecnologie necessarie ad eseguire un'applicazione; permette di compilare, riorganizzare il codice, introdurre automaticamente librerie e dipendenze, offuscare il codice;
- _Browserify_;
- _Progressive web applications_;
- Opinionated vs. non-opinionated frameworks;
- _Static site generators_ - per pre-compilare script destinati ad essere eseguiti client-side sul server, così da scaricare il peso dal client.

## Principi architetturali
Il WWW si appoggia su solidi principi architetturali, riassumibili in 3 parole:
- **identificazione**: ogni elemento del web è chiamato risorsa ed è identificato da un identificatore globale chiamato URI
- **interazione**: si usa un protocollo di comunicazione chiamato HTTP, che permette di scambiare messaggi su una rete informatica
- **formato**: la disponibilità di apposite applicazioni sul computer ricevente per identificare e decodificare i dati in un certo formato, per consentire l'accesso in modo chiaro e non ambiguo

## Referenze
[^1]: dettaglio importante, l'idea è che il client mantiene le informazioni riguardanti la comunicazione con il server, ossia le richieste sono separate e indipendenti, non viene mantenuto lo stato della comunicazione dal server