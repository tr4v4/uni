---
tags:
  - category/note
  - status/finished
  - topic/programmazione
date: 28-10-2023 12:06:36
links:
  - "[[Lecture 25102023092611]]"
---
# Stringhe
---
## Introduzione
> Le **stringhe** in informatica si definiscono come _[[Array|array]] di caratteri_.

Di speciale, rispetto ai semplici array, hanno l'utilizzo di un _carattere speciale che determina il fine-stringa_: `NULL` (o `\0`[^1]). Se dichiariamo infatti una stringa di 10 caratteri, uno di essi verrà riservato al fine-stringa.

Il motivo che si cela dietro all'utilizzo del fine-stringa è di semplice comodità: se dichiariamo una stringa di 100 caratteri, ma l'utente ne inserisce solo 20, ponendo `\0` in 21° posizione _sappiamo determinare quando termina l'input dell'utente_.

## Inizializzazione
Una stringa si dichiara come un semplice array, ma si può inizializzare in vari modi:
- `char msg[20] = "Ciao. Come stai?;"`
	- `\0` viene _aggiunto automaticamente_
- `char msg[20] = {'C', 'i', 'a', 'o', '\0'};`
	- `\0` lo dobbiamo _aggiungere manualmente_

Per prendere in ingresso una stringa dall'utente si può utilizzare:
- `cin >> stringa;`
	- termina l'inserimento dopo il primo spazio che trova
- `cin.getline(stringa, lunghezza);`
	- termina l'inserimento dopo l'invio, massimo dopo il raggiungimento della lunghezza massima della stringa
	- <u>attenzione</u>: la lunghezza massima della stringa comprende `\0`

## Libreria
### `cstring`
Abbiamo a disposizione la libreria `cstring` che ci permette di utilizzare i seguenti metodi
- `strcpy`
	- copia una stringa da un array a un altro
	- _versione sicura_: `strncpy`, si limita a copiare fino a `n` caratteri, non aspetta di incontrare `\0` per terminare il ciclo
- `strcat`
	- concatena due stringhe
	- _versione sicura_: `strncat`, si limita a concatenare fino a `n` caratteri, non aspetta di incontrare `\0` per terminare il ciclo
- `strlen`
	- restituisce la lunghezza della stringa, non considerando `\0`
- `strcmp`, `strncmp`
	- compara due stringhe
		- restituisce `0` se le stringhe _sono uguali_
		- restituisce `1` se la prima stringa è _alfabeticamente maggiore della seconda_
		- restituisce `-1` se la prima stringa è _alfabeticamente minore della seconda_
	- _versione sicura_: `strcmp`, si limita a comparare fino a `n` caratteri, non aspetta di incontrare `\0` per terminare il ciclo

### `cstdlib`
La libreria `cstdlib`, contiene funzioni di conversione da stringhe ad altri [[Tipi di dati|tipi di dati]]:
- `atoi`: _str_ --> _int_
- `atol`: _str_ --> _long_
- `atof`: _str_ --> _float_

## Referenze
[^1]: fare riferimento alla tabella [[ASCII]]