---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 18-08-2025 19:02:09
links:
  - "[[Lecture 22102024110521]]"
  - "[[Lecture 24102024120228]]"
---
# Linguaggio libero deterministico
---
## Introduzione
> Un [[Linguaggio formale|linguaggio]] si dice **libero deterministico** se è [[Linguaggio accettato|accettato]] _per stato finale_ da un [[DPDA]].

## Teoremi
### Rapporto con liberi
> La classe dei linguaggi liberi deterministici è _inclusa propriamente_ nella classe dei [[Linguaggio libero|linguaggi liberi]].

Ovvero ci sono linguaggi liberi che non possono essere deterministici.

#### Esempio
Si prenda il linguaggio
$$L = \{ww^{R} | w \in \{a, b\}^{*}\}$$
Questo sappiamo essere libero. Infatti abbiamo creato l'[[NPDA]] che lo accettava. Ma si può dimostrare che non esiste un DPDA che lo riconosce!

Invece il linguaggio
$$L = \{wcw^{R}|w \in \{a, b\}^{*}\}$$
è libero deterministico. Il DPDA che lo riconosce per stato finale è:
![[dpda-1.png]]

### Rapporto con regolari
> Se $L$ è [[Linguaggio regolare|regolare]] allora esiste un DPDA $N$ tale che $L = L[N]$ (sempre per stato finale).

Ovvio, ci basta creare un DPDA che si comporta come il [[DFA]] che riconosce $L$ senza mai manipolare lo stack.

### Accettazione per pila vuota
> Un linguaggio libero deterministico $L$ è riconosciuto da un DPDA _per pila vuota_ $\iff$ $L$ gode della **prefix property**:
> $$\nexists x, y \in L : x \text{ prefisso di } y$$

Allora per contronominale, se $L$ è libero deterministico ma non gode della prefix property, allora _non può essere riconosciuto da un DPDA per pila vuota_.

Possiamo però con uno stratagemma passare sempre da un linguaggio che non gode della prefix property ad uno praticamente equivalente che invece ne gode: **aggiungendo un simbolo speciale $ alla fine di ogni sua stringa**!
Infatti se $L$ è libero deterministico, allora $L\$ = \{w\$ | w \in L\}$ gode della prefix property, e quindi può essere riconosciuto da un DPDA per pila vuota.

#### Esempio
##### 1
Prendiamo il linguaggio
$$L = \{a^{n}b^{n}|n\geq 0\}$$
Sappiamo che è libero e anche deterministico (sotto il DPDA che lo riconosce per stato finale):
![[dpda-2.png]]

Tuttavia non gode della prefix property: la stringa $a^{0}b^{0} = \epsilon$ è il prefisso di $a^{1}b^{1} = ab$,

Il linguaggio $L\$$, invece, ne gode. Infatti il DPDA che lo riconosce per pila vuota è il seguente:
![[dpda-3.png]]

##### 2
Prendiamo ora quest'altro linguaggio
$$L = a^{*} \cup \{a^{n}b^{n} | n \geq 1\}$$
che è libero deterministico, ma non gode della prefix property.
Il DPDA che lo riconosce per stato finale è il seguente:
![[dpda-4.png]]

Quello che invece riconosce $L\$$ per pila vuota è:
![[dpda-5.png]]

### Grammatica non ambigua
> Se $L$ è libero deterministico, allora $L$ è [[Linguaggio generato|generabile]] da una grammatica libera [[Grammatica ambigua|non ambigua]], e di conseguenza i linguaggi liberi deterministici non sono [[Linguaggio ambiguo|ambigui]].

### Proprietà
I linguaggi liberi deterministici **sono solo chiusi per complementazione**, e invece:
- _non sono chiusi per intersezione_;
- _non sono chiusi per unione_;

Il fatto che siano chiusi per complementazione ci dice quindi che se esiste un DPDA che riconosce un linguaggio, allora esiste anche un altro DPDA che riconosce il suo complementare.
L'idea della prova è la seguente: basta rendere totale la funzione di transizione $\delta$ (aggiungendo degli stati non finali), e a quel punto scambiando gli stati finali con quelli non finali[^1] ottieni il DPDA che riconosce il linguaggio complementare.

Non sono chiusi per intersezione, basta prendere i due linguaggi
$$L_{1} = \{a^{n}b^{n}c^{m} | n, m \geq 0\} \ \ \ \ \ \ L_{2} = \{a^{m}b^{n}c^{n} | n,m \geq 0\}$$
e notare che
$$L_{1} \cap L_{2} = \{a^{n}b^{n}c^{n} | n \geq 0\}$$
non è proprio libero (e quindi neanche libero deterministico)!

Non sono chiusi per unione, quindi, come diretta conseguenza dei precedenti risultati e di [[Leggi di De Morgan|De Morgan]].

## Referenze

[^1]: stessa tecnica usata per dimostrare la chiusura per complementazione dei linguaggi regolari!
