---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 09-03-2025 11:51:12
links:
  - "[[Lecture 17022025110943]]"
  - "[[Lecture 18022025152022]]"
  - "[[Lecture 10032025112014]]"
---
# Sicurezza di rete
---
## Principi
La sicurezza di [[Rete|rete]] si basa sui seguenti principi:
- **confidenzialita'** --> solamente il mittente e il destinatario sono capaci di interpretare il contenuto della loro comunicazione;
- **autenticazione** --> il mittente e il destinatario devono confermare le loro corrispettive identità, ognuno nei confronti dell'altro;
- **integrita' (del messaggio)** --> il contenuto della comunicazione non deve essere trasformato durante, o anche dopo, il transito di esso;
- **accesso e disponibilita'** --> i servizi devono essere accessibili e disponibili agli utenti;

## Comunicazione
Per poter rispettare i principi sopra citati, la comunicazione tra utenti delle reti deve avvenire in modo sicuro. In particolare, gli utenti comunicano del _plain text_, ma su [[Internet|internet]] viaggia del _chiper text_. La scienza che studia come implementare un meccanismo del genere si chiama [[Crittografia|crittografia]].

Per garantire l'[[Autenticazione|autenticazione]], invece, si utilizza un meccanismo (che si scoprira' essere connesso alla crittografia) chiamato [[Firma digitale|firma digitale]], in connubio con le [[Certification Authorities|CA]].

## Formula finale
Unendo i meccanismi di confidenzialita' con quelli di autenticazione e di integrita', otteniamo che se $B$ vuole comunicare con $A$, allora inviera'
$$K_{A}^{+}(m, K_{B}^{-}(h(m)))$$

Questa formula e' equivalente in termini di sicurezza con
$$K_{A}^{+}(m), K_{B}^{-}(h(m))$$
? La risposta e' teoricamente si' ma praticamente no: nel secondo caso ci sarebbe la possibilità che uno dall'[[Funzione hash|hash]] decifrato (si conosce la chiave pubblica di $B$) sia in grado di ricavare il messaggio; nella pratica pero' questo non ha comunque senso perché $h$ è una [[Funzione one-way|funzione one-way]].

Tuttavia, **Trudy potrebbe sempre intercettare la comunicazione e modificare qualche bit**, causando [[DoS]]. Non c'e' soluzione a questo problema.

## Referenze
- [[Attacchi informatici]]
- [[Posta elettronica sicura]]
- [[SSL]]
- [[IPsec]]
- [[Firewall]]
- [[ACL]]