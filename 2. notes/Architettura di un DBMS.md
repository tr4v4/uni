---
tags:
  - category/note
  - status/ongoing
  - topic/basi-di-dati
date: 18-10-2025 15:35:57
links:
  - "[[Lecture 16102025151651]]"
---
# Architettura di un DBMS
---
## Introduzione
L'architettura di un [[DBMS]], [[Modello relazionale dei dati|relazionale]] almeno, si presenta nel seguente modo:
![[architettura-dbms-relazionale.png]]

## Componenti
### Query processor
> Il **query processor** è il componente che più condiziona le performance del DBMS.

Si compone a sua volta di:
- _query compiler_
- _execution engine_

#### Query compiler
Questo traduce ogni query in un "piano" di query, facendo:
- _[[Parser|parsing]]_, in modo particolare producendo l'[[Albero sintattico|alberi sintattico]];
- _preprocessing_, che controlla la semantica;
- _optimization_, che trasforma la query originale nella miglior sequenza di operazioni, seguento le [[Equivalenze nell'algebra relazionale|equivalenze nell'algebra relazionale]];

Per esempio, trasforma la query [[SQL]]:
```sql
SELECT A, B
FROM R1, R2
WHERE C = D AND C = 'c'
```
diventa prima
$$\pi_{A, B}(\sigma_{C=D}(\sigma_{C='c'}(R1) \Join R2))$$
e poi la sequenza
$$\sigma_{C='c'}(R1), \ \ \ \Join R2, \ \ \ \sigma_{C=D}, \ \ \ \pi_{A, B}$$

#### Execution engine
Questo invece esegue tutti gli step dell'espressione in [[Algebra relazionale|algebra relazionale]] presa dal query compiler, _interfacciandosi con il manager delle risorse per recuperare le informazioni_.

### Manager delle risorse
Si deve capire che i dati, in un database, sono _sempre su una memoria secondaria_. Il manager delle risorse sa precisamente dove sono questi dati e come ottenerli velocemente. Include:
- _index/file/record manager_ che conosce lo schema del [[Database|database]];
- _buffer manager_ che partiziona la memoria principale in buffer dentro i quali possiamo trasferire dei blocchi di disco (fa da [[Cache|cache]]);
- _storage manager_ che tiene traccia delle locazioni dei file sul disco, e ottiene i blocchi.

Quindi si interfaccia direttamente con la memoria secondaria.

### Manager delle transazioni
Sappiamo che in un database acceduto contemporaneamente da più utenti è necessario introdurre il meccanismo delle [[Transazione|transazioni]]. Ognuna di queste è isolata dalle altre, e secondo la legge di **durabilità di un DBMS**, _il lavoro di una transazione non sarà mai perso_.

Il manager delle transazioni, allora, gestisce:
- _logging and recovery_
- _concurrency control_

#### Logging and recovery
Si compone di:
- _manager dei log_ --> segna su un file separato tutte le operazioni svolte dal database (e quindi le transazioni); inizialmente le scrive sul buffer, e poi negozia con il buffer manager per assicurarsi che tali log siano scritti anche sul disco;
- _manager del recovery_ --> esamina i log changes e in caso di system failure ripristinano il database a uno stato consistente.

#### Concurrency control
Anche se le transazioni appunto sono eseguite in "isolamento", _nella realtà non sono eseguite in sequenza_! Si cerca di parallelizzare il più possibile tali transazioni, ma per farlo nella maniera più corretta sono necessari dei meccanismi di controllo delle concorrenze.

In particolare, si vuole assicurere che:
> L'**ordine di esecuzione delle transazioni sia scelto in modo tale che l'effetto sia lo stesso del caso di esecuzione sequenziale** (una alla volta).

Questa proprietà si può ottenere usando un meccanismo di **lock**: _quando due query accedono alla stessa tabella, viene creato un lucchetto che fa passare una transizione alla volta_. Tuttavia, questo può portare addirittura a casi di [[Deadlock|deadlock]]!

## Referenze