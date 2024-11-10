---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 13-10-2024 14:42:25
links:
  - "[[Lecture 30092024161544]]"
  - "[[Lecture 03102024151447]]"
  - "[[Lecture 14102024161336]]"
---
# HTML
---
## Introduzione
### Guerre dei browser
[[Tim Berners-Lee]], con la sua invenzione del [[Web|web]], fa nascere anche un software in grado di far navigare le persone su di esso: il **browser**.

Si scatena, dal 1994 sino ad oggi, una continua "guerra" tra chi vuole monopolizzare questo nuovo campo:
1. 1994-2001, **Netscape vs. Microsoft Internet Explorer**: vince Microsoft, rilascia il codice in open-source che diventerà la base di Firefox (all'epoca Mozilla); il vero vincitore è W3C, il tavolo neutrale e decisore ultimo sul futuro degli standard del Web
	- fanno a gara a chi introduce più funzionalità, non [[Interoperabilità|interoperabili]]! diciamo l'anti-standard
	- il W3C decide di separare gli ambiti tra contenuto e aspetto, dividendo HTML da CSS --> pubblicherà un sacco di standard inerenti al web
	- nel 2001 tutto il mondo usa Internet Explorer, ma poi Microsoft si "siede", e smette di migliorarlo
2. 2005-2019, molti attori in gioco: Firefox contro Chrome, Safari contro Chrome (e quindi Apple contro Google); intanto esce Iphone, e si scatena la guerra delle piattaforme mobili contro PC desktop; soprattutto WHAT WG vs. W3C
	- Google nasce come motore di ricerca, ma poi fanno un browser loro così non hanno più problemi di compatibilità
	- W3C dice che HTML4.7 è la versione definitiva di HTML, mentre i browser non la pensano così --> in segreto sviluppano altre feature e si riuniscono sotto il nome WHAT WG --> vince il WHAT WG, che è formato dai monopoli dei browser
3. 2019-_in corso_: in realtà non è una guerra dei browser, anzi questi sono il campo di battaglia; da AngularJS si sviluppano tre grandi famiglie di librerie: Angular (completamente diversa da AngularJS, si irridisce tantissimo) (Google) (opinionato), React e React Native (Facebook) (non opinionato), VueJs (open-source) (è la parte di AngularJS che manca ad Angular); i browser diventano meno importanti rispetto al modello di sviluppo di applicazioni web --> è la guerra dei componenti
	- essendo così diversi Angular e React, un programmatore può diventare esperto solo di uno dei due!
	- ci sono altri framework: Svelte, Alpine

## Definizione
> Per definizione, **HTML** (_HyperText Markup Language_), è un linguaggio di [[Markup|markup]]. In particolare è un'istanza di [[SGML]] che si è particolarmente distinta per la scrittura di pagine web.

Tuttavia, dalla sua origine ad oggi, HTML ha subito una serie di modifiche così imponenti che lo hanno reso un vero e proprio linguaggio per la creazione di applicazioni. E per ragioni storiche, non ha senso dare un'unica definizione di HTML.

### Differenze
Esistono formalmente due HTML:
- _HTML 5.2_ (sospeso nel 2021) della [[W3C]]
- _HTML Living Standard_ del [[WHATWG]]

In particolare dopo l'uscita di HTML 4 la W3C si era fermata mentre i browser chiedevano la standardizzazione di nuove funzionalità. La W3C, nel 2000, propose XHTML 1.0, una riformulazione di HTML 4 come un'applicazione XML 1.0, che prevedeva quindi vincoli maggiori, con annidamenti corretti secondo la rigidità di XML. Tuttavia i browser non accettano e propongono sempre nuove funzionalità standardizzate per HTML: la W3C le boccia. E' così che nasce la WHATWG, che inizia a lavorare ad una versione intermedia di HTML con modifiche e features non approvate dal W3C. La WHATWG infatti voleva sistemare le cose di HTML piuttosto che riscrivere un nuovo linguaggio. Così la W3C è costretta a riconoscere la validità delle modifiche di WHATWG, e riapre il working group con l'intenzione di creare HTML 5. Tuttavia la WHATWG, senza avvertire la W3C, annuncia che l'HTML è un "living standard":
- i produttori di browser autonomamente adottano nuove features;
- viene quindi cambiato completamente il modello di sviluppo del linguaggio, non più democratico e sistematico come per il W3C;

In poche parole, vincono quindi i produttori di browser. Il W3C continua a rilasciare standardizzazioni di HTML, ma si accorge che anche se esce HTML 6, dato che i browser adottano gli standardi di WHATWG, non serve a niente! Così abbandona il progetto nel 2019, lasciando a WHATWG in mano la situazione. Oggi, di fatto, si è in pieno _HTML Living Standard_ (non HTML 5!).

Nella pratica, come conseguenza di questa storia, HTML si differenzia in:
- _teorico_, quello suggerito dagli standard --> i browser agiscono in **strict mode**;
- _pratico_, tag-soup di elementi non conformi agli standard --> i browser agiscono in **quirks mode**.

## Basi
Un documento HTML si struttura solitamente in:
- `<!DOCTYPE html>` - il meccanismo primario con cui il browser capisce come fare il parsing
- `html` - la radice dell'albero
- `head` - informazioni globali sul documento
- `body` - contenuto del documento

### Elementi
#### Elementi inline
Non spezzano il blocco (non vanno a capo), o si includono liberamente l'uno dentro l'altro. Si dividono in:
- _fontstyle_ - informazioni specifiche di rendering (molti deprecati, perché si usano in CSS)
	- `tt` (TeleType, font monospaziato), `i` (corsivo), `b` (grassetto), `u` (sottolineato, deprecato), `s` (bassato, deprecato) e `strike`, `big` e `small` (testo più grande e più piccolo)
- _phrase_

#### Elementi di blocco
Sono blocchi di testo che contengono elementi inline:
- `<p>`, `<div>`, `<pre>` (il whitespace, ossia `LF`, `CR`, `TAB` ecc..., è significativo! quindi non collassato su un unico spazio come per gli altri blocchi), `<address>`, `<blockquote>`
- blocchi con ruolo strutturale: `<h1>`, `<h2>`, `<h3>`, `<h4>`, `<h5>`, `<h6>`

Teoricamente i blocchi permetterebbero il contenimento, ossia una struttura gerarchica, cosa che nei word processor per esempio non c'è, tuttavia realmente questa gerarchia manca. Posso infatti mettere un `<h1>` dentro un `<h5>`!

#### Elementi di lista
Sono:
-  `<ul>` - lista non ordinata di elementi `<li>`
- `<ol>` - lista ordinata di elementi `<li>`
- `<dl>` - lista di definizioni composta da molti elementi `<dt>` (termine) e `<dd>` (dato)

#### Elementi generici
Sono privi di caratteristiche semantiche o presentazionali predefinite, ma assumono invece quelle desiderate con l'aiuto dei loro attributi (_style_, _class_, _lang_):
- `<div>` - mantiene la natura di elemento blocco
- `<span>` - mantiene la natura di tipo inline

#### Elementi di struttura
Introdotti in HTML 5, aiutano nella definizione del modello gerarchico, e quindi a organizzare il contenuto in blocchi semantici:
- `<main>`
	- `<section>`
	- `<article>`
- `<aside>`
- `<header>` e `<footer>`
- `<nav>` - barra di navigazione

#### Effetti grafici
Sono:
- `<hr>` - piccola riga orizzontale attraverso lo schermo (si può controllare larghezza e spessore)
- `<br>` - una andata a capo forzata

### Contenuti
#### Link ipertestuali
I link sono definiti come elementi `<a>`, sintatticamente un elemento inline. Ha come attributi:
- `href` - specifica l'[[URI]] di destinazione
- `name` - specifica un nome usato come destinazione di un link

#### Immagini
Un'immagine inline è definita con l'elemento `<img>`, completamente definito dai suoi attributi:
- `src`
- `alt`
- `name`
- `width`
- `height`
- `srcset` - per immagini responsive

Esiste poi l'elemento `<figure>`.

#### Embedding
Ci sono altri elementi simili a `<img>` per incorporare oggetti multimediali nella pagina HTML:
- `<video>`
- `<audio>`
- `<object>`
- `<embed>` - come `<object>` ma non richiede plug-in
- `<iframe>` - per fare embedding di una pagina HTML all'interno di un'altra pagina HTML

#### Tabelle e tabelle di layout
Con relativi tag e importante attenzione a `colspan` e `rowspan`.

#### Form e input
Per inserire valori da inviare a un server. In particolare:
1. il browser raccoglie dati dall'utente con un form;
2. crea una connessione [[HTTP]] con il server, specificando una ACTION (cioè un applicazione che funga da destinatario) a cui fare arrivare i dati;
3. il destinatario riceve i dati, li elabora e genera un documento di risposta, che viene spedito, tramite il server HTTP, al browser.

Gli elementi sono:
- `<form>`
- `<input>` (di tantissimi tipi), `<select>`, `<textarea>`
- `<button>`
- `<label>`

#### Attributi globali
Gli attributi globali di tutti gli elementi di HTML sono:
- _id_
- _class_
- _style_
- _title_

Altri sono:
- _i18n_: lang, dir
- _interattività_: accesskey, autofocus, tabindex, inputmode
- _evento_: onclick, ondoubleclick, onmouseover, onkeypress

#### Attributi `data-`
In HTML non esistono veri e propri errori di sintassi, ed è possibile inventare dei propri attributi facendoli formalmente riconoscere dal prefisso `data-`. Sono un set aperto di attributi definibile in ogni elemento HTML, usatissimi in _Bootstrap_.

Per accederci in [[CSS]] si aggiunge al selettore `['data-xxx']`. Per esempio:
```css
button['data-premimi'] {
	...
}
```

In [[Javascript]] bisogna fare attenzione al nome di questi attributi, perché vengono convertiti in notazione _camel case_ (non accetta variabili con `-` ed è _case sensitive_).

#### Attributi ARIA
Per i non vedenti sono stati introdotti degli attributi appositi che mitigassero la cattiva abitudine degli sviluppatori di usare tag non semantici come semantici, rendendo inaccessibili porzioni di pagine web.

Per esempio viene spesso usato `<span>` come bottone al posto di usare il tag appropriato `<button>`. Gli attributi ARIA vanno a definire il _ruolo_ di ogni tag, _esplicitandone la semantica_.

### Entità
L'ultima macro-categoria di elementi di HTML sono le sue entità. In particolare si tratta di _entità-carattere_. Esistono perché:
- alcuni caratteri sono proibiti in quanto usati in HTML --> serve un meccanismo di _escaping_;
- se il documento è codificato in [[ASCII]] 7 bit allora caratteri non sono rappresentabili.

<u>Nota bene</u>: se il documento è in [[UTF-8]], ovviamente, l'unico problema è l'escaping.

Per risolvere entrambi i problemi in un colpo solo, HTML consente di scrivere caratteri di questa categoria anteponendo l'ampersand `&`.

## Peculiarità
HTML presenta alcune peculiarità sintattiche che è bene conoscere:
- maiuscolo/minuscolo indifferente, mentre XHTML sì
- whitespace, HTML collassa tutti i caratteri di whitespace (`SPACE`, `TAB`, `CR`, `LF`) in un unico spazio (tranne quando si è dentro il tag `<pre>`)
- estensioni del linguaggio, si può estendere HTML con propri elementi e/o attributi
- bizzarrie sintattiche
	- _virgolette non obbligatorie_, ma noi sappiamo che lo sono quando gli attributi NON sono TOKEN
	- _assenza di tag_, si possono omettere `<html>` e `<body>`, ovviamente non valido in XHTML --> l'algoritmo di parsing della WHATWG (che ha contestato XHTML proposto da W3C) aggiunge automaticamente `<html>` e `<body>` all'interno delle pagine in cui è assente
	- _omissibilità del tag di chiusura_, si possono non chiudere i `<li>` (solo quel tag)
	- _attributi di solo valore_, caratteristica ereditata da SGML (e poi rimosso) in cui se il nome dell'attributo e il suo valore sono uguali si può omettere il valore e scrivere solo il nome

## Referenze