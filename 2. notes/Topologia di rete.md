---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 01-10-2024 19:51:02
links:
  - "[[Lecture 20092024132015]]"
  - "[[Lecture 25092024132223]]"
---
# Topologia di rete
---
## Introduzione
> Per **topologia di rete** si intende lo studio degli schemi di connessioni delle [[Infrastruttura di rete|infrastrutture di rete]].

## Tipologie
Le più importanti topologie sono:
- _anello_
- _stella_
- _bus_
- _albero_

### Anello
![[topologia-anello.png|200]]
Era **considerata la soluzione migliore per la connessione di dispositivi in rete locale**. Presto, però, fu superata dal modello a stella.

Vantaggi:
- _affidabilità_ --> se si rompeva un arco dell'anello si faceva rigirare il segnale nel verso opposto, garantendo sempre la comunicazione _broadcast_
- _facilità di broadcast_
- _meccanismo facile per evitare le collisioni_ --> con la tecnologia [[Token Ring]] solo chi possedeva il token era autorizzato a trasmettere, e il tempo di possesso del token era negoziabile dai dispositivi della rete, per mettere tutti d'accordo sul tempo di attesa per riaverlo (erano sincronizzati)

Svantaggi:
- _[[SPOF]]_ --> il protocollo Token Ring purtroppo non è facile da gestire, come nei casi di distruzione dell'arco che trasmette il token, con la sua conseguente perdita (nessuno parla più)
- _sincronizzazione sui tempi di utilizzo_ --> sempre il Token Ring richiede una sincronizzazione degli host connessi per scandire il tempo di utilizzo del token, ma la ricezione dei token non è istantanea, per esempio può passare del tempo proporzionale alla lunghezza dei cavi, ed è difficile tenere conto di questo fattore

### Stella
![[topologia-stella.png|200]]

La topologia a stella è quella che **oggigiorno domina completamente ogni infrastruttura di rete, sia fisica che logica**[^1].

Come elemento centrale è presente un [[Hub|hub]] oppure uno [[Switch|switch]].

Vantaggi:
- _numero minimo di archi_ --> il grafo ha uno schema di connessioni minimamente connesso, considerando anche l'host centrale
- _efficienza_
- _scalabilità_ --> per connettere un nodo in più basta connetterlo al nodo centrale
- _riduzione del costo_
- _latenza di rete minimale_ --> per via del [[Complessità computazionale|costo]] dell'attraversamento degli archi, che di fatto è costante, e _non lineare come nel caso della topologia ad anello_
- _facile gestione dei collegamenti punto a punto_
- [[Ethernet]] --> è il protocollo che gestisce la comunicazione, attuato principalmente dal nodo centrale per gestire le collisioni

Svantaggi:
- _SPOF_ --> il nodo centrale è a tutti gli effetti un collo di bottiglia, perché se si rompe lui non parla più nessuno

### Bus
![[topologia-bus.png|200]]
Tremendamente scomodo.

### Albero
![[topologia-albero.png|200]]
C'è una gerarchia tra host, a livello teorico e logico sarà utile per suddividere le reti in sottoreti[^2].

### Conclusioni
Per le [[LAN]] e le [[PAN]] la topologia solitamente è sempre a stella, mentre nelle reti più grandi e complesse esistono topologie ibride, dette _a maglia_. Questo perché _reti con connessioni multiple riducono il rischio di partizionamenti della rete_.

## Referenze
[^1]: si pensi all'[[Architettura client-server|architettura client-server]]
[^2]: _subnet mask_