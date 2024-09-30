---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 25-09-2024 21:49:28
links:
  - "[[Lecture 17092024110611]]"
---
# Realizzazione di una macchina astratta
---
## Introduzione
Per realizzare una [[Macchina astratta|macchina astratta]] $M_{A}$ su di una macchina ospite $M_{O}$ esistono 3 modi:
1. _realizzazione in hardware_
2. _emulazione o simulazione via firmware_
3. _interpretazione o simulazione via software_

Il 1° modo è teoricamente sempre possibile e ovviamente garantisce una massima velocità di traduzione, ma nella pratica si fa solo per macchine astratte di basso livello perché c'è poca flessibilità.

Il 2° modo si fa realizzando strutture dati e algoritmi della macchina astratta mediante [[Microprogrammazione|microprogrammazione]], che risiedono in una [[ROM]], e nonostante l'alta velocità è una flessibilità più ampia rispetto al 1° modo richiede che la macchina ospite (fisica) sia microprogrammabile.

Il 3° modo si realizza **scrivendo strutture dati e algoritmi della macchina astratta mediante programmi scritti nel linguaggio "offerto" dalla macchina ospite**. Questo ovviamente diminuisce la velocità di traduzione, ma garantisce massima portabilità e flessibilità!

### Realtà
Nella realtà si realizza $M_{A}$ su $M_{O}$ usando una combinazione delle 3 tecniche: questo grazie a una _trasparenza_ dei livelli _software_, _firmware_ e _hardware_. Per esempio dal software posso accedere a componenti del firmware.

### Vantaggi
Con il 3° metodo si costruiscono macchine astratte cui linguaggio è più sofisticato di quello della macchina ospite, per cui iterando la costruzione di macchine astratte, una sopra l'altra, _si arriva ad ottenere una macchina astratta con un linguaggio di altissimo livello_.

## Realizzazione
Assumendo di scartare, quindi, la soluzione hardware e di assimilare quella software e firmware, si ha che:
> Implementare un linguaggio $L$ significa realizzare la macchina astratta $M_{L}$ che si poggia sulla macchina ospite (di livello inferiore) ${M_{O}}_{L_{O}}$, ossia quella a cui è associato il linguaggio $L_{O}$.

In poche parole, si deve implementare $L$ su ${M_{O}}_{L_{O}}$, ossia scrivere un programma in $L_{O}$ che traduca le istruzioni da $L$ a $L_{O}$.

Se indichiamo ${P_{r}}^{L}$ come un programma scritto in $L$, allora questo è associato a una [[Funzione parziale|funzione parziale]] $P^{L}$ sull'insieme dei dati $D$, che rappresenta la **semantica** di ${P_{r}}^{L}$: $$P^{L}: D \to D$$
(ossia $P^{L}(\text{input}) = \text{output}$)

<u>Nota bene</u>: il programma ${P_{r}}^{L}$ dice come trasforma un input in un output; la funzione parziale $P^{L}$ associa solo un input a un output.

### Implementazione
Si hanno 2 vie per realizzare ciò:
- _implementazione interpretativa pura_ - realizzando un [[Interprete|interprete]];
- _implementazione compilativa pura_ - realizzando un [[Compilatore|compilatore]].

#### Interpretativa pura
Si scrive un interprete per $L$ su ${M_{O}}_{L_{O}}$, ossia un programma scritto in $L_{O}$ (ed eseguito da $M_{O}$) che realizza una funzione parziale
$$I_{L}^{L_{O}} : (P_{r}^{L} \times D) \to D \ \ : \ \ I_{L}^{L_{O}}(P_{r}^{L}, \text{input}) = P^{L}(\text{input})$$

ovvero l'_interprete deve calcolare la semantica corretta del programma_!
![[traduzione-interprete.png]]

Pros:
- flessibilità
- facilità di realizzazione
- poca occupazione di memoria

Cons:
- scarsa efficienza di $M_{L}$

Questo perché l'interprete decodifica ogni istruzione prima di eseguirla, per cui **al tempo di esecuzione va aggiunto quello di decodifica ogni qualvolta si incontri un'istruzione**: il _body di un ciclo viene decodificato tante volte quanto viene eseguito_!

#### Compilativa pura
In questo caso, invece, i programma in $L$ sono tradotti in programmi equivalenti in $L_{O}$ da un compilatore ${C_{L, L_{O}}}^{L_{A}}$, un programma scritto in $L_{A}$ (linguaggio di una terza macchina astratta $M_{A}$), che realizza una funzione
$$C_{L,L_{O}}: {P_{r}}^{L} \to {P_{r}}^{L_{O}} \ \ | \ \ \forall {P_{r}}^{L}. \ \ C_{L,L_{O}}({P_{r}}^{L})={{P_{r}}c}^{L_{O}} \implies \forall \text{input}. \ \ P^{L}(\text{input}) = Pc^{L_{O}}(\text{input})$$

ovvero il compilatore (come anche l'interprete) deve fare in modo che _la semantica del programma in input sia la stessa del programma in output_.
![[traduzione-compilatore.png]]

Pros:
- alta efficienza

Cons:
- difficoltà d'implementazione (per lontananza da $L$ a $L_{O}$)
- scarsa flessibilità
- perdita di informazione sulla struttura del programma

Difatti, di un errore a run-time di un programma compilato è poco facile identificare la causa: anche se la semantica è la stessa, si è completamente perso il riferimento al programma scritto in $L$.

### Caso reale
Nella realtà dei fatti i due metodi coesistono: di solito **si compila e poi si interpreta il risultato**[^1].
![[compilatore-e-interprete.png]]

<u>Nota bene</u>: di solito l'interprete della macchina intermedia $M_{L_{i}}$ non è direttamente scritto su $M_{O}$ (appuno perché su macchina intermedia). Questo perché a volte, l'interprete, ha bisogno di meccanismi che lo supportano nella comunicazione con $M_{O}$. Questi meccanismi, chiamati **supporto a run-time** ([[SRT]]), e la macchina ospite, formano la macchine intermedia $M_{L_{i}}$ su cui viene eseguito l'interprete.

Inoltre, nel caso stretto della compilazione, oltre alla [[AOT]] (_Ahead-Of-Time_) Compilation, esiste la [[JIT]] (_Just-In-Time_) Compilation, ossia una compilazione run-time: ovviamente non riga per riga, per esempio le funzioni vengono compilate tutte in una volta, ma solo nel momento in cui sono invocate!

## Referenze
[^1]: per esempio [[Java]] fa proprio questo