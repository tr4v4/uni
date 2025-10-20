---
tags:
  - category/note
  - status/finished
  - topic/basi-di-dati
date: 13-10-2025 14:37:35
links:
  - "[[Lecture 09102025151427]]"
  - "[[Lecture 17102025151336]]"
---
# SQL
---
## Introduzione
> **SQL** (**Structured Query Language**) è un [[Linguaggio di programmazione dichiarativo|linguaggio dichiarativo]] per le query in un [[Database|database]].

Implementa sia [[DDL]] che [[DML]].

## DDL
- `CREATE DATABASE db_name`
- `CREATE SCHEMA schema_name`
- in entrambi i comandi sopra, sia il database che lo schema creati apparterranno all'utente che li ha creati
- infatti si può fare `CREATE SCHEMA schema_name AUTHORIZATION 'user_name'` per specificare l'autorizzazione a un certo utente
- `CREATE TABLE`
	- attributi
		- basic
			- Character-string
			- Numeric
			- DATE, TIME, INTERVAL
			- Boolean
			- BLOB/CLOB
		- custom
			- `CREATE DOMAIN`
			- esempio:
				- `CREATE DOMAIN Grade AS SMALLINT DEFAULT NULL CHECK ( value >= 18 AND value <= 30 )`
	- vincoli delle relazioni
		- `NOT NULL`
		- `UNIQUE` per definire delle chiavi
		- `PRIMARY KEY`
		- `CHECK`
		- `REFERENCES` e `FOREIGN KEY` sono per i vincoli di integrità referenziali
			- c'è una sintassi diversa a seconda che si usi un unico attributo, oppure su più
			- ci sono anche le azioni triggerabili da fare quando un'operazione è rifiutata (rompe i vincoli referenziali)
				- `ON <DELETE | UPDATE> <CASCADE | SET NULL | SET DEFAULT | NO ACTION>`
- statement per modificare gli schema
	- `ALTER DOMAIN`
	- `ALTER TABLE`
	- `DROP DOMAIN`
	- `DROP TABLE`

## DQL
- `SELECT` - corrisponde all'operatore di _proiezione_
- `FROM` - a partire da quale/i tabella/e devo fare l'interrogazione?
- `WHERE` - corrisponde all'operatore di _selezione_
- `AS` - sulle tabelle è un'alias per la query, invece sui campi diventa l'operatore di _rinominazione_
- `LIKE` - per fare un filtro su una sorta di [[Espressione regolare|regex]] (per esempio `LIKE 'J_m%'` significa che quel campo deve cominciare con `J` e che la terza lettera dev'essere `m`);
- `IS NULL` - condizione per vedere se un valore è nullo

Di base la sintassi e' quindi:
```SQL
SELECT <AttributeList>
FROM <TableList>
[ WHERE <Condition> ]
```
che ricorda molto il [[Calcolo relazionale su tuple con dichiarazioni del range|calcolo relazionale su tuple]]! Non per niente _SQL e' implementato proprio tramite questo calcolo_...

### `DISTINCT`
Di norma sappiamo che quando facciamo l'operatore di proiezione $\pi$ con l'[[Algebra relazionale|algebra relazionale]], **due tuple che risultano uguali questi collassano per via della stessa definizione insiemistica di relazione**. Questo in SQL non e' direttamente implementato! Vale a dire che una query del tipo
```SQL
SELECT Surname, Agency
FROM EMPLOYEE
```
sulla tabella

| Number | Surname | Agency | Age |
| ------ | ------- | ------ | --- |
| 7309   | Neri    | Naples | 55  |
| 5998   | Neri    | Milan  | 64  |
| 9553   | Rossi   | Rome   | 44  |
| 5698   | Rossi   | Rome   | 64  |

restituisce la tabella

| Surname | Agency |
| ------- | ------ |
| Neri    | Naples |
| Neri    | Milan  |
| Rossi   | Rome   |
| Rossi   | Rome   |

Per fare in modo che le tuple uguali collassino, bisogna segnalarlo con la keyword `DISTINCT` dopo la `SELECT`, ovvero fare la query:
```SQL
SELECT DISTINCT Surname, Agency
FROM EMPLOYEE
```

Questo viene fatto per motivi di efficienza.

### `JOIN`
Le _join_ in SQL possono essere:
- _impliciti_ - basta elencare le tabelle nella clausola `FROM` e poi in `WHERE` porre la condizione ($\theta$-[[Algebra relazionale#$ theta$-join|join]]); di base significa che la join produce il [[Prodotto cartesiano|prodotto cartesiano]], e poi specificando la condizione $\theta$ si ottiene la natural join (come nel caso della equi-join);
- _espliciti_ - andando proprio a specificare la congiunzione con l'operatore `JOIN`.

Il secondo caso si fa con la sintassi seguente:
```SQL
SELECT ...
FROM A JOIN B ON condition
```

Di norma, esplicitare la join e' meglio: ci sono degli algoritmi efficienti per la loro risoluzione.

### Espressioni
All'interno delle `SELECT` possiamo anche scrivere delle vere e proprie espressioni, come nell'esempio seguente:
```SQL
SELECT Income/2 as halvedIncome
FROM PEOPLE
WHERE Name = 'Louis'
```

Questo ci suggerisce una cosa importante: **SQL ha piu' [[Potere espressivo|potere espressivo]] dell'algebra relazionale** (ricordiamo infatti i [[Limiti del calcolo e dell'algebra relazionale|limiti dell'algebra e del calcolo relazionale]]).

## DML

## Referenze
- [[Indice]]