---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 19-11-2024 19:23:59
links:
  - "[[Lecture 23102024132952]]"
  - "[[Lecture 14112024173206]]"
---
# IP
---
## Introduzione
> L'**IP** (**Internet Protocol**) è il [[Protocollo di rete|protocollo di rete]] principale del [[Livello rete|livello rete]]. Introduce un _nuovo indirizzamento globale e gerarchico_[^1], che permette di instradare i pacchetti in modo efficiente. E' di tipo _connectionless_ e _best-effort_.

## Compiti
Il protocollo IP si occupa di:
- _indirizzamento_ -> ogni dispositivo connesso alla rete ha un [[Indirizzo IP|indirizzo IP]] univoco, un indirizzo logico;
- _frammentazione_ -> i segmenti (di [[Livello trasporto|livello trasporto]]) vengono suddivisi in pacchetti;
- _[[Instradamento|instradamento]]_ -> i pacchetti vengono inviati verso la destinazione attraverso i [[Router|router]];

## Pacchetto
Un pacchetto IP contiene gli _indirizzi IP del mittente e del destinatario_.

## Versioni
L'IP è stato sviluppato in due versioni:
- **[[IPv4]]**: la versione storica che prevede 4 byte per indirizzo, per un totale di $2^{32}$ indirizzi (esauriti nel 2017);
- **[[IPv6]]**: la versione futura che prevede 16 byte per indirizzo, per un totale di $2^{128}$ indirizzi.

## Referenze
[^1]: nuovo rispetto all'[[Indirizzo MAC|indirizzo MAC]]