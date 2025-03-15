---
tags:
  - category/note
  - status/finished
  - topic/tecnologie-web
  - topic/reti-di-calcolatori
date: 25-11-2024 13:19:58
links:
  - "[[Lecture 18022025152022]]"
  - "[[Lecture 24022025111633]]"
---
# Autenticazione
---
## Introduzione
> L'**autenticazione** è il processo tramite il quale un sistema verifica l'identità di un utente. Nell'ambito della [[Sicurezza di rete|sicurezza di rete]], si tratta di verificare piu' a basso livello l'identita' di un interlocutore all'interno di una [[Rete|rete]].

<u>Attenzione</u>: l'_autenticazione non è da confondere con l'[[Autorizzazione|autorizzazione]]_, che è _il processo tramite il quale un sistema verifica i permessi di un utente_.

## Web
Nel contesto del [[Web|web]], l'_autenticazione può avvenire tramite [[Cookie|cookie]]_. In particolare, questi possono essere utilizzati per _memorizzare le informazioni di login dell'utente_, per evitare di doverle reinserire ad ogni accesso.

Gli approcci più comuni per l'autenticazione web sono:
- _[[Autenticazione session-based|session-based]]_ - il server mantiene un ID di sessione, e informazioni sull'utente verificate ad ogni richiesta;
- _[[Autenticazione token-based|token-based]]_ - il client mantiene un token rilasciato dal server, che spedisce ad ogni richiesta per la verifica.

## Sicurezza
Nell'ambito della sicurezza, gia' abbiamo accennato al fatto che possiamo sfruttuare le potenzialita' dell'[[RSA]] per verificare l'autenticita' di un interlocutore. Per evitare attacchi di tipo replay, possiamo unire questa tecnica con l'utilizzo del [[Nonce|nonce]] ed ottenere uno scambio apparentemente sicuro:
![[autenticazione-rsa-nonce-naive.png]]

Per quanto questo scambio sembri funzionare, c'e' sempre la possibilita' che si palesi un [[Man-in-the-middle|man-in-the-middle]]: non possiamo essere certi del fatto che sia il nonce $R$ firmato con $K_{A}^{-}$ e $K_{A}^{+}$ in realta' non appartengano a un mal-intenzionato Trudy che si e' posto in mezzo nella comunicazione tra Alice e Bob.
![[autenticazioone-rsa-nonce-mitm.png]]

Di fatto, per eliminare la possibilità del _man-in-the-middle_ bisogna essere certi del fatto che **la chiave pubblica inviata dal mittente sia effettivamente del mittente**! In altri termini, **e' necessario creare un'associazione garantita e certificata tra la chiave pubblica del mittente e la sua identita' digitale**: questo viene implementato dalle [[Certification Authorities|CA]].

## Referenze