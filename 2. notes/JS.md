---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 16-11-2024 19:17:07
links:
  - "[[Lecture 24102024153025]]"
  - "[[Lecture 04112024161118]]"
  - "[[Lecture 07112024151846]]"
  - "[[Lecture 11112024161208]]"
  - "[[Lecture 14112024131613]]"
---
# JS
---
## Introduzione
> **JavaScript** (**JS**) è un _[[Linguaggio di programmazione|linguaggio di programmazione]]_ [[Interprete|interpretato]], [[Linguaggio di programmazione orientato a oggetti|orientato agli oggetti]] e agli eventi, comunemente utilizzato per aggiungere interattività alle _pagine [[Web|web]]_.

Vedremo che JS è un linguaggio molto versatile, che può essere utilizzato sia lato _client_ che lato _server_ (routing).

## Utilizzo
Ci sono due modalità principali di esecuzione di script JS:
- _sincrono_: il [[Browser|browser]] esegue lo script (specificato nel tag `<script>` o in un file) immediatamente, "bloccando" il caricamento del resto della pagina
- _asincrono_: ci sono 3 sottomodalità
	1. _eventi_: lo script viene eseguito in seguito a un evento (es. click su un bottone)
	2. _operazione_: lo script viene eseguito in seguito a un'operazione (es. caricamento di una pagina), vedremo meglio con [[AJAX]] e la gestione delle _callback_
	3. _timeout_: lo script viene eseguito dopo un certo tempo

Per mandare in output gli script ci sono differenti approcci:
- `document.write(string)`, sfrutta il [[DOM]] per scrivere una stringa direttamente nella pagina;
- `console.log(string)`, scrive una stringa nella console del browser;
- `alert(string)`, mostra una finestra di dialogo con la stringa;
- `document.getElementById(id).innerHTML = string`, sfrutta sempre il DOM ma per scrivere direttamente in un elemento specifico della pagina.

### Accorgimenti
Se il browser carica uno script, specificato magari in un tag `<script>` all'inizio del `<body>` o da un link nel `<head>`, prima del caricamento dell'HTML, si rischia di incorrere in problematiche non indifferenti: _lo script potrebbe non trovare gli elementi che cerca di manipolare (per esempio associandoci funzioni di callback), perché non sono ancora stati caricati_!

Quindi, al fine di evitare che lo script venga eseguito prima del caricamento dell'[[HTML]], si possono adottare due strategie:
1. **mettere lo script in fondo alla pagina** (scrivendolo dentro un tag `<script>` o collegandolo a un file esterno), così che venga eseguito dopo il caricamento di tutti gli elementi HTML;
2. **associare una funzione che inizializza tutte le callback ai vari elementi del DOM a `window.onload`**.

La funzione `window.onload`, infatti, viene eseguita _solo dopo che tutti gli elementi della pagina sono stati caricati_.

## Base
Le cose importanti su JavaScript da sapere sono:
- _i dati sono tipati ma le variabili no_
	- `var`, `let` e `const` sono le parole chiave per dichiarare variabili
- _tra gli operatori_
	- si distingue \=\= da \=\=\=, il primo fa casting, il secondo no
	- il `+` è sia per la concatenazione di stringhe (con casting automatico) che per la somma di numeri
- _esiste l'operatore ternario_
	- `let x = (condizione) ? valore1 : valore2`
- _si distingue il `for` dal `for in`_
	- `for` è quello standard
	- `for in` è per iterare sugli indici di un array o di un oggetto
- _le funzioni non sono tipate_
- _gli unici oggetti sono quelli JavaScript_, ossia [[JSON]]
	- ci si può accedere con `.` o `[]`
- _gli array sono oggetti con proprietà e metodi utili_
	- `array.length` per la lunghezza
	- `array.push()` per aggiungere un elemento
	- `array.pop()` per rimuovere l'ultimo elemento
	- `array.shift()` per rimuovere il primo elemento
	- `array.unshift()` per aggiungere un elemento all'inizio
	- `array.slice(a, b)` per restituire un sottoarray da `a` a `b`
	- `array.splice(pos, rimuovi, inserisci)` per rimuovere e inserire elementi in posizione `pos`
	- `array.join(sep)` per concatenare gli elementi con un separatore `sep`
- _ci sono oggetti messi a disposizione_
	- `Math` per le funzioni matematiche
		- `Math.PI`
		- `Math.round()`
		- `Math.floor()`
		- `Math.ceil()`
		- `Math.random()`
		- `Math.sin()`
		- `Math.cos()`
	- `Date` per le date
		- `new Date()` per creare un oggetto data con la data corrente
		- `new Date(year, month, day, hours, minutes, seconds, milliseconds)` per creare un oggetto data con i parametri specificati
		- `date.getFullYear()`
		- `date.getMonth()`
		- `date.getDate()`
		- `date.getDay()`
		- `date.getHours()`
		- `date.getMinutes()`
		- `date.getSeconds()`
		- `date.getMilliseconds()`
	- `RegExp` per le [[Espressione regolare|espressioni regolari]] (dichiarata con `/pattern/`)
		- `new RegExp(pattern, flags)` per creare un oggetto RegExp
		- `regexp.test(string)` per verificare se una stringa corrisponde al pattern
		- `regexp.exec(string)` per trovare la prima corrispondenza
		- `string.match(regexp)` per trovare tutte le corrispondenze
	- `String` per le stringhe
		- `string.toUpperCase()`
		- `string.toLowerCase()`
		- `string.charAt(pos)`
		- `string.indexOf(substring)` per trovare la posizione di una sottostringa
		- `string.lastIndexOf(substring)`
		- `string.substring(start, end)`
		- `string.substr(start, length)`
		- `string.split(separator)` per dividere la stringa in un array utilizzando il separatore
	- `Array` per gli array
	- `Object` per gli oggetti
	- `JSON` per il parsing di stringhe JSON
		- `JSON.parse(string)` per convertire una stringa JSON in un oggetto JavaScript
		- `JSON.stringify(object)` per convertire un oggetto JavaScript in una stringa JSON

## Avanzato
Le cose avanzate su JavaScript da sapere sono:
- _truthy e falsy_
	- _falsy_ --> qualunque valore che in caso di casting a booleano diventa false
		- `0`, `null`, `undefined`, `""`, `NaN`
	- _truthy_ --> qualunque valore che in caso di casting a booleano diventa true
	    - `"any non empty string"`, `3.14`, `Infinity`, `{}`, `[]`, `"0"`, `"undefined"`, `"null"`
	    - da questo si ha che `{} == []` restituisce `true`
	- si possono sfruttare, e si usano tantissimo (per risparimare in `if`)
		- es. `port = port || 80`
			- restituisce `port` se è _truthy_ (per la [[Short-circuit evaluation|short-circuit evaluation]])
			- restituisce `80` se `port` è _falsy_
- _le funzioni in JavaScript sono oggetti_[^1] (si dice che sono un'entità di 1° classe)
	- le variabili possono contenere funzioni
	- in JavaScript non c'è differenza tra attributo e metodo, perché ogni metodo è in realtà un attributo (in quanto oggetto) --> _un oggetto JavaScript è solo composto da attributi, che possono essere funzioni e quindi usati come metodi_
	- si possono avere _funzioni che restituiscono funzioni_
	    - in [[Angular]] e [[React]] e in altri framework queste sono usatissime
	    - sono molto comode per implementare i _pattern di ingegneria del software_ (per esempio la [[Factory|factory]])
- _si possono dichiarare funzioni anonime_
- _esistono tantissime funzioni filtro sugli array_
	- `array.sort(f)` per ordinare l'array con una funzione `f`, che restituisce -1, 0, 1 confrontando gli elementi dell'array; è elegante e veloce perché già compilata
	- `array.filter(f)` per filtrare l'array con una funzione `f`, che restituisce `true` o `false` per ogni elemento;
	- `array.some(f)` per verificare se almeno un elemento dell'array soddisfa la funzione `f`;
	- `array.every(f)` per verificare se tutti gli elementi dell'array soddisfano la funzione `f`;
	- `array.find(f)` per trovare il primo elemento dell'array che soddisfa la funzione `f`;
	- `array.forEach(f)` per eseguire la funzione `f` su ogni elemento dell'array;
	- `array.map(f)` per creare un nuovo array con gli elementi trasformati dalla funzione `f`;
	- `array.reduce(f)` per ridurre l'array a un singolo valore con la funzione `f`;
- _si possono dichiarare funzioni "freccia"_
	- sono funzioni anonime, ma con una sintassi più compatta
	- possono contenere una sola espressione, che viene restituita con `return` (anche implicito)
- _si possono definire stringhe multi-linea usando backtick \`_
	- in queste stringhe è anche possibile usare gli interpolatori `${varName}`[^2]
- _è possibile usare un operatore di optional chaining_
	- `?.` per accedere a un attributo di un oggetto, se questo è definito
	- questo consente di evitare una serie di `if` nidificati
- _esiste l'operatore spread `...`_
	- spalma gli elementi di un elemento strutturato
	- è molto comodo per passare un array come argomenti di una funzione, per concatenare array o per clonarli
	- ad esempio `f(...array)` è equivalente a `f(array[0], array[1], ...)`

### Prototipo
JavaScript è _[[Linguaggio di programmazione orientato a oggetti|object-oriented]] ma prototype-based_ (non class-based come [[Java]], per esempio). Questo significa che:
- _posso aggiungere/modificare proprietà e metodi condivisi di molti oggetti istanziati da un prototipo_
- _queste modifiche sono immediatamente visibili e accessibili da tutti gli oggetti, dalle istanze già create_
- _sono modifiche che valgono per tutti, ma poi queste proprietà ereditate dalle istanze sono "private"_ (non statiche per intenderci)
- _ogni istanza ha un puntatore a un suo prototipo_

I prototipi sono comodi ma anche pericolosi. Per esempio, per verificare come finisce una stringa si può fare comodamente con un metodo del prototipo dell'oggetto `String` predefinito di JavaScript:
```javascript
String.prototype.endsWith = function(value) {
	return this.substr(-1*value.length) == value;
}
```
Quindi stiamo aggiungendo a tutte le stringhe un metodo `endsWith`. Questo metodo è molto comodo perché non si ha _namespace pollution_. Infatti il metodo creato è globale ma vale solo per le stringhe: non si è occupato lo spazio dei nomi globale.

Ma è corretto modificare il prototipo di una classe esistente? Questo è un dibattito che dura da 15 anni. C'è infatti il _rischio di modificare dei metodi definiti dalle librerie_. Quindi:
- o sono sicuro che non ci siano collisioni di nomi
- o lo faccio apposta per sovrascrivere i metodi già definiti
- o uso un prefisso apposito per distinguere quelli definiti da me

#### Classi
In realtà, **le classi in JavaScript sono zucchero sintattico per i prototipi**. Il `new` crea un oggetto vuoto e ad esso assegna il `this` del costruttore, ossia il riferimento all'oggetto corrente.

Con `bind()` si può bindare il `this` esplicitamente su un oggetto.

### Scope delle variabili
JavaScript prevede diverse modalità di definizione delle variabili:
- _variabili globali_ - `var a = 5; let b = 7; c = 9;` sono tutte dichiarazioni di variabili globali se sono fuori da ogni blocco
- _variabili di modulo_ - con keyword `export` e `import`, si ha che le variabili sono visibili solo all'interno del modulo se non viene esplicitato l'export
- _variabili locali_ (di funzione) - il loro scope sovrascrive quello delle variabili globali
- _variabili di blocco_ - definite con `let` e `const`, sono visibili solo all'interno del blocco in cui sono definite (non vale per `var`)

#### Closure
E' un meccanismo che consente di creare variabili private in oggetti e funzioni. Si tratta di una funzione che "incapsula" delle variabili, che non sono visibili all'esterno.

Consideriamo una funzione che ritorna un'altra funzione:
```javascript
Counter = function() {
  var counter = 0;
  return {
	  increment: () => {counter++;},
	  decrement: () => {counter--;}
  }
}
```
In questo caso, `counter` è una variabile privata, che non è accessibile dall'esterno. Infatti, se istanziamo un nuovo `Counter`
```javascript
let c = new Counter();
c.increment();
console.log(c.increment()); // 1
c.counter = 10;             // è lecito ma non fa niente
console.log(c.increment()); // 2
```
si può vedere che `counter` di `c` è protetto dalla _closure_ e quindi è accessibile solo tramite i metodi `increment` e `decrement`.

#### IIFE
L'IIFE (Immediately Invoked Function Expression) è una _funzione anonima creata ed immediatamente invocata_. Viene usata per creare _singleton_ dotati di _closure_. E' usata moltissimo nelle librerie JavaScript.
```javascript
var people = (function() {
	var persone = [];
	return {
		add: function(p) {persone.push(p)},
		lista: function() {return persone.join(', ')}
	}
}) ();
```
In questo caso, si dichiara e si invoca immediatamente una funzione anonima (quella tra parentesi), che ritorna un oggetto che usa la _closure_ per l'array `persone`.

## Oggetti predefiniti del browser
Il browser mette a disposizione degli oggetti predefiniti accessibili da JavaScript:
- `window`: rappresenta la finestra principale su cui si svolge la navigazione; ogni pagina web vive isolata da tutte le altre, non c'è comunicazione tra tab né finestre aperte del browser
	- `frame`: divide l'area della finestra in sottoaree dipendenti con elementi HTML indipendenti (inutilizzati per gli stessi problemi di sicurezza della window)
	- `document`: rappresenta il contenuto del documento attualmente visualizzato all'interno della finestra
		- si accede con `window.document` ma anche direttamente con `document` (perché `document` è una variabile globale, figlia di `window`)
	- `location`: l'URL del documento corrente, che se modificato fa accedere a un nuovo URL (equivalente a un _redirect_)
	- `history`: array degli URL acceduti durante la navigazione, consente di creare applicazioni dinamiche che navigano la cronologia
	    - non è affetto da operazioni AJAX, quindi per simulare navigazioni viene modificata a mano lo stack di history, questo si chiama _routing client-side_
- `navigator`: oggetto che fornisce informazioni sul client e sul browser

Il `window.document` rappresenta il [[DOM]].

## Referenze
[^1]: vengono chiamate _funzioni lambda_
[^2]: come le _f-string_ di [[Python]]