---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 13-07-2025 17:20:16
links:
  - "[[Lecture 06052025152121]]"
  - "[[Lecture 29042025152102]]"
---
# RTS-CTS
---
## Introduzione
> Il **protocollo RTS-CTS** (**Request to Send** - **Clear to Send**) viene utilizzato per evitare collisioni in reti wireless, specialmente in scenari con molti dispositivi che condividono lo stesso canale di comunicazione. Questo protocollo è particolarmente utile in ambienti dove il [[Problema del terminale nascosto|problema del terminale nascosto]] può causare problemi di trasmissione.

## Protocollo
Se $A$ vuole trasmettere a $C$, e $C$ si trova anche nell'area di copertura di $B$ ma $A$ e $B$ sono _nascosti_, allora:
1. $A$ invia un pacchetto RTS a $C$;
2. $C$ risponde con un pacchetto CTS ad $A$ (cambiando i [[Indirizzo MAC|MAC address]]), ma questo arriva anche a $B$;
3. $B$ sa che non può trasmettere, quindi non interferisce con la comunicazione tra $A$ e $C$.

![[rts-cts.png]]

<u>Nota bene</u>: nell'_RTS posso mettere anche la dimensione dei dati da trasmettere_, allora in questo caso $C$ trasmetterà nel CTS questa dimensione, e $B$ _saprà quanto tempo dovrà aspettare prima di trasmettere_ a $C$.

Quindi:
- _se senti solo l'RTS_ --> puoi comunicare anche con chi l'ha inviato, disturberesti solo lui e non il ricevente perche' non hai sentito il suo CTS;
- _se senti solo il CTS_ --> devi aspettare di poter parlare.

Si tratta di fatto di un **meccanismo di prenotazione dello spazio**, in particolare di quello attorno al ricevente: zittisce tutti i trasmittenti vicini, tranne colui che ha inviato l'RTS. Questo, [[Probabilita'|probabilisticamente]] parlando, e' equivalente al meccanismo di **collision detection** implementato da [[Ethernet]], ma implementa in realta' la **collision avoidance**.

<u>Nota bene</u>: viene cambiato il paradigma, perche' e' il ricevente ad invitare il trasmittente a comunicare, e non viceversa. Questo paradigma si chiama _transmissin by invitation_.

## Svantaggi
E' facilmente attaccabile: e' sufficiente inviare in continuazione CTS per creare un _CTS flooding_ e impedire le comunicazioni.

Inoltre introduce maggiore overhead!

## Referenze