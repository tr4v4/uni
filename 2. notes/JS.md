---
tags:
  - category/note
  - status/ongoing
  - topic/tecnologie-web
date: 16-11-2024 19:17:07
links:
  - "[[Lecture 24102024153025]]"
  - "[[Lecture 04112024161118]]"
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

## Referenze