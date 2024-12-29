---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 24-11-2024 19:32:24
links:
  - "[[Lecture 07112024151846]]"
---
# DOM
---
## Introduzione
> Il **DOM** (_Document Object Model_) è un'[[API]] del [[Browser|browser]] usato per la _rappresentazione di documenti strutturati ad [[Albero informatico|albero]]_, che permette di modificare la struttura, lo stile e il contenuto di un documento [[HTML]] o [[XML]].

Il [[Parsing|parsing]] di HTML è complicato perché deve tenere conto di tutte le possibili versioni. Per questo è stato introdotto il _DOM, un riassunto della pagina realizzato dal browser cui costruzione è comune a tutte le pagine web_. Con questo modello, i programmatori possono costruire documenti, navigare attraverso la loro struttura, aggiungere, modificare o cancellare elementi.

L'idea del DOM non è originaria di [[WHATWG]], ma è stata presa da [[JQuery]].

## Composizione
Il DOM è una struttura ad albero, composta da _DOM Node_ (classe astratta), che si istanziano in classi concrete.
![[dom-struttura.png]]

<u>Nota bene</u>: è un albero ordinato, perché _i figli sono ordinati_.

Le classi principali che estendono la classe astratta _DOM Node_ sono:
- _Element_: rappresenta un elemento HTML
- _Text_: rappresenta il contenuto di un elemento
- _Comment_: rappresenta un commento HTML
- _Document_: rappresenta l'intero documento
- _Attribute_: rappresenta un attributo del documento
- ...

### DOM Node
La classe _DOM Node_ specifica attributi e metodi comuni a tutti gli oggetti del DOM:
- attributi
	- `nodeName`
	- `nodeType`
	- `parentNode`
	- `childNodes`
	- ...
- metodi
	- `insertBefore()`
	- `removeChild()`
	- `appendChild()`
	- `replaceChild()`
	- ...

### DOM Document
La classe _Document_ rappresenta l'intero documento, e ha attributi e metodi specifici:
- attributi
	- `documentElement`
	- `docType`
	- ...
- metodi
	- `createElement()`
	- `createTextNode()`
	- `createAttribute()`
	- `getElementById()`
	- `getElementsByName()`
	- `getElementsByTagName()`
	- `querySelector()`
	- `querySelectorAll()`
	- ...

### DOM Element
La classe _Element_ rappresenta un elemento HTML, e ha attributi e metodi specifici:
- attributi
	- `nodeName`
	- ...
- metodi
	- `setAttribute()`
	- `getAttribute()`
	- `removeAttribute()`
	- ...

### InnerHTML e OuterHTML
Il DOM per HTML permette di accedere e modificare il contenuto di un elemento tramite le proprietà `innerHTML` e `outerHTML`:
- `innerHTML`: rappresenta il contenuto HTML del sottoalbero di un elemento;
- `outerHTML`: rappresenta il contenuto HTML dell'elemento stesso, compreso quindi il suo tag di apertura e chiusura (oltre che il sottoalbero).

### Selettori
Il DOM mette a disposizione metodi per selezionare elementi HTML:
- `getElementById()`
- `getElementsByName()`
- `getElementsByTagName()`
- `getElementsByClassName()`
- `querySelector()`
- `querySelectorAll()`

### Eventi
Il DOM permette di associare degli eventi agli elementi HTML, per esempio:
```javascript
document.getElementById("myBtn").addEventListener("click", myFunction);
// oppure attraverso il metodo onclick e il passaggio di una funzione
document.getElementById("myBtn").onclick = myFunction;
```

#### Bubbling
Il _bubbling_ è un meccanismo di propagazione degli eventi in un albero DOM, che prevede che un evento scatenato da un elemento si propaghi ai suoi genitori.

## Referenze