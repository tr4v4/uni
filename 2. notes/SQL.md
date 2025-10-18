---
tags:
  - category/note
  - status/finished
  - topic/basi-di-dati
date: 13-10-2025 14:37:35
links:
  - "[[Lecture 09102025151427]]"
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

## DML

## Referenze