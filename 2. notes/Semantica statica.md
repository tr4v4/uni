---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 05-10-2024 19:23:57
links:
  - "[[Lecture 26092024120454]]"
---
# Semantica statica
---
## Introduzione
> Ci sono regole, nei [[Linguaggio di programmazione|linguaggi di programmazione]] che non possono essere catturati da [[Grammatiche libere|grammatiche libere]]. Vengono chiamate **vincoli sintattici contestuali**, e costituiscono la **semantica statica** (o **sintassi contestuale**).
> La caratteristica primaria della semantica statica è che _riguarda quell'insieme di controlli che possono essere fatti sul testo di un programma **senza eseguirlo**_.

Per esempio
- la verifica della [[Dichiarazione|dichiarazione]] di una [[Identificatore|variabile]] prima del suo utilizzo;
- la compatibilità tra tipo di variabile e valore dell'[[Assegnamento|assegnamento]] ([[Type checking|type checking]]);
- l'uguaglianza tra il numero/tipo di parametri attuali di una [[Invocazione di procedura|chiamata di procedura]] e il numero/tipo dei parametri formali della dichiarazione della [[Funzione informatica|funzione]];

sono _tutti vincoli contestuali_, perché esulano da ciò che una grammatica libera riesce a esprimere.

<u>Nota bene</u>: in realtà, _questi controlli dovrebbero appartenere alla sintassi, ma dato che solitamente si associa la sintassi alla grammatica libera, allora si fa riferimento alla sintassi contestuale come semantica statica_.

## Soluzioni
Esistono due tecniche alternative per la cattura di vincoli contestuali:
1. usare _[[Grammatiche dipendenti dal contesto|grammatiche dipendenti dal contesto]]_ --> si tratta di una soluzione poco pratica perché riconoscere una stringa $w$ appartenente a un [[Linguaggio generato|linguaggio generato]] da una [[Grammatiche|grammatica]] del genere diventa un problema di [[Complessità computazionale|complessità]] esponenziale ($w \in L(G)$?);
2. usare _controlli "ad hoc"_ --> i [[Compilatore|compilatori]] possiedono una fase di [[Analisi semantica|analisi semantica]] che fa questi controlli.

Ovviamente la seconda opzione è quella usata effettivamente. Di fatto **si lascia la descrizione della sintassi del linguaggio di programmazione alla grammatica libera** e **durante la fase di analisi semantica il compilatore verifica i vincoli sintattici contestuali** (semantica statica);

## Referenze
- [[Semantica dinamica]]