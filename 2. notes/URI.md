---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
date: 24-09-2024 17:55:45
links:
  - "[[Lecture 19092024151357]]"
---
# URI
---
## Introduzione
Per capire a fondo che cos'è e perché è importanti l'URI, è necessario prima ricordare che questo è ciò su cui si basa il principio architetturale del [[Web|web]] dell'**identificazione**. In particolare quello che l'URI identifica è una **[[Risorsa|risorsa]]**.
Molti URI fanno riferimento a file memorizzati in un file-system gerarchico, perché si tratta di file all'interno del server, ma sappiamo che le risorse non sono per forza file: _un URI può identificare anche un servizio_.

Ad ogni modo è proprio grazie all'URI che il web ha un così ampio successo: con esso si può anche definire il tipo di protocollo dell'applicazione web, rendendolo molto versatile.

## Definizione
> Per **URI** (**Uniform Resource Identifier**) si intende, nella pratica, una [[Sintassi|sintassi]] usata nel WWW per _definire i nomi e gli indirizzi di risorse su internet_.


Gli URI comprendono a loro volta:
- [[URL]]
- [[URN]]

![[URL-URN.png]]

### Differenza
La differenza sostanziale tra URL e URN sta nel loro ruolo. Possiamo immagine l'URL come il numero di telefono di una persona, e l'URN come il suo nome e cognome (o codice fiscale).
- con il _numero di telefono_ (URL) puoi _contattare la persona_, ma solo fino a quando questo è valido e associato ad essa;
- con il _nome e cognome_ (URN) puoi _fare riferimento a quella persona_ in una conversazione, e varrà sempre, ma non puoi contattarla.

Di fatto, un _name_ (URN) solitamente deve essere _risolto_ in un _locator_ (URL), attraverso un meccanismo chiamato _lookup_ (nell'esempio equivale a cercare il numero in un elenco telefonico).

## Sintassi
La sintassi di un'URI si basa su dei criteri di design:
- _trascrivibili_ (ovvio)
- _fornire identificazione, non interazione_ - non servono per accedere alla risorsa, ma per nominarla, per riferirsi alla stessa risorsa
- _fornire spazi di nomi organizzati gerarchicamente_ - si utilizzano specifici caratteri come delimitatori per separare in modo gerarchico le varie parti in cui è composto l'URI

Detto questo, la sintassi di un URI è del tipo:
`URI = schema:[//authority]path[?query][#fragment]`

dove:
- `schema` (negli URL è il protocollo): è identificato da una stringa registrata presso [[IANA]] usata come prefisso
- `authority`: individua un'organizzazione gerarchica dello spazio dei nomi a cui sono delegati i nomi (a loro volta delegati, ecc...); a sua volta è suddivisa in `authority = [userinfo@]host[:port]`, dove:
	- `userinfo` è solo per l'identificazione personale[^1]
	- `host` è un nome di dominio o un indirizzo [[IP]]
	- `port` può essere omessa se ci si riferisce a una _well-known [[Porta|port]]_
- `path`: parte identificativa della risorsa all'interno dello spazio di nomi identificato dallo schema e (se esistente) dalla authority
- `query`: è un'ulteriore specificazione della risorsa
- `fragment`: individua una risorsa secondaria, solitamente dipendente da quella primaria

### Caratteri ammessi
L'URI prevede una divisione dei caratteri ammessi in 3 classi:
- _unreserved_: sono tutte i caratteri utilizzabili, e comprendono le maiuscole, le minuscole, le cifre e una ristretta punteggiatura (`-_!~*'()`)
- _reserved_: sono tutti i caratteri riservati allo scopo di specificare le parti dell'URI (`;/?:@&=+$,`)
- _escaped_: costituiscono il modo per usare i caratteri _reserved_ come _unreserved_, e seguono la _sintassi escaped_ `%XX` dove `XX` è il codice esadecimale del carattere (in una codifica stabilita)
	- esempio di utilizzo di `%2F` per scrivere `/` in modo che non faccia da separatore gerarchico ma faccia parte del nome della sottoparte gerarchica

## URI reference
> La **URI reference** (o **uriref**), è un meccanismo che consente di fare riferimento a solo una parte dell'URI completo, chiamato appunto _uriref_, tagliandolo da sinistra. Automaticamente, nella fase di _risoluzione_, la parte mancante, detta _base_, viene aggiunta per riottenere l'**URI assoluto** (ossia completo) nel momento della richiesta della risorsa.

Infatti un **uriref, senza base, è inutilizzabile**.

### Risoluzione e dereferenziazione
Il processo alla base della richiesta di una risorsa cui manca la base, quindi uriref, si sviluppa nei seguenti 2 passaggi:
1. _URI resolution_: quando ho solo l'uriref oppure un URI a cui manca la risorsa fisica (URI senza URL), serve a ottenere l'URL assoluto;
2. _URI dereferencing_: dato un URL si ottiene la risorsa richiesta.

#### Risoluzione

|                                                                                                                                                              | Dato l'URI base ==http://www.site.com/dir1/doc1.html==                                                                                                                |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Se inizia con "#", è un frammento interno allo stesso documento di base                                                                                      | `#anchor1` si risolve come http://www.site.com/dir1/doc1.html#anchor1                                                                                                 |
| Se inizia con uno schema, è un URI assoluto                                                                                                                  | http://www.site.com/dir2/doc2.html si risolve come http://www.site.com/dir2/doc2.html                                                                                 |
| Se inizia con "//", è un URI assoluto con lo stesso schema della base. Serve per creare riferimenti che funzionano sia con HTTP che con HTTPS                | //www.site2.com/dir5/doc7.html si risolve in http://www.site2.com/dir5/doc7.html N.B.: se la base fosse https://... diventerebbe https://www.site2.com/dir5/doc7.html |
| Se inizia con "/", allora è un path assoluto all'interno della stessa autorità della base, e ha la stessa authority.                                         | /dir3/doc3.html si risolve come http://www.site.com/dir3/doc3.html                                                                                                    |
| Altrimenti, si estrae il path assoluto dell'URI di base, meno l'ultimo elemento, e si aggiunge in fondo l'URI relativo. Si procede infine a semplificazioni: | doc4.html si risolve come http://www.site.com/dir1/doc4.html<br>dir5/doc5.html si risolve come http://www.site.com/dir1/dir5/doc5.html                                |
| "./" (stesso livello di gerarchia): viene cancellata                                                                                                         | ./doc6.html<br>si risolve come http://www.site.com/dir1/./doc6.html che è equivalente a http://www.site.com/dir1/doc6.html                                            |
| "../" (livello superiore di gerarchia): viene eliminato insieme all'elemento precedente.                                                                     | ../doc7.html si risolve come http://www.site.com/dir1/../doc7.html che è equivalente a http://www.site.com/doc7.html                                                  |

### Schema
Ci sono diversi tipi di `schema`. I principali sono:
- `http` o `https` con sintassi associata `http://host[:port]/path[?query][#fragment]`
- `file` con sintassi associata `file://host/path [#fragment]`
- `data` con sintassi associata `data:[<media type>][;base64],<data>`
- `ftp` con sintassi associata `ftp://[user[:password]@]host[:port]/path`

## Approfondimenti
- [[CDN]] (Content Delivery Network)
- URL permanenti
- URI rewriting
- URI shortener
- IRI
- IDN, con rischio di _spoofing_
- CURIE
- Linked Data e Linked Open Data

## Referenze
- [[URI route]]

[^1]: si pensi a [[SSH]]