---
tags:
  - category/note
  - status/finished
  - topic/logica-per-informatica
date: 04-10-2023 15:48:44
links:
  - "[[Lecture 20092023125825]]"
  - "[[Lecture 28092023090721]]"
---
# Insieme
---
## Definizione
> L'insieme è l'entità di base della [[Teoria degli insiemi]]. In un insieme non conta né l'ordine né la numerosità dei suoi elementi. Un insieme si indica così
> $$\{1, 2\}$$

## Intuizione "a scatola"
Per comprendere il modo in cui funzionano gli insiemi dobbiamo completamente dimenticare la rappresentazione fornitaci da sempre con il [[Diagramma di Venn|diagramma di Venn]]. Infatti, questi possono essere fuorvianti:
- come rappresento $\{\{1, 2\}, 3\}$ per non confonderlo con $\{1, 2, 3\}$?
- come rappresento un insieme che contiene se stesso?
- gli insiemi non hanno un'area

Pensiamo piuttosto agli **insiemi come scatole**, che una volta aperte possiamo vedere che contengono elementi al loro interno. Prendiamo allora i predicati di _appartenenza_ ed _essere sottoinsieme_ per aiutarci a comprendere questa nuova rappresentazione degli insiemi.

<u>Nota bene</u>: all'interno degli insiemi, le _ripetizioni_ e l'_ordine_ non contano ($\{1, 2, 3\}=\{2, 3, 1, 1, 2\}$).

### Appartenenza
L'**appartenenza** mette a confronto un _elemento_ con un _insieme_, andando a verificare se l'elemento di sinistra _appartenga_ all'elemento di destra. Non importa se a sinistra abbiamo un elemento o un insieme (anzi, ricordiamoci che _tutto è un insieme_...), l'importante è verificare che esso sia o meno contenuto nell'insieme confrontato.

Per cui
$$
\begin{align}
1 \in \{1, 2, 3\} \\
\{1, 2\} \notin \{1, 2, 3\} \\
\{1, 2\} \in \{\{1, 2\}, 3\} \\
\varnothing \notin \{1, 2, 3\}
\end{align}
$$

### Essere sottoinsieme
L'**essere sottoinsieme** mette a confronto un _insieme_ con un altro _insieme_, andando a verificare se il <u>contenuto</u> dell'insieme di sinistra ci sia _tutto_ nell'insieme di destra. Qualunque cosa ci sia a sinistra, che sia un elemento o un insieme (sempre ricordando che in realtà _tutto è un insieme_), si aprirà la scatola per verificare che il suo contenuto sia o meno un sottoinsieme dell'insieme confrontato.

Per cui
$$
\begin{align}
\{1, 3\} \subseteq \{1, 2, 3\} \\
\{1, 3\} \nsubseteq \{\{1, 3\}, 2\} \\
1 \nsubseteq \{1, 2, 3\} \\
\{1\} \subseteq \{1, 2, 3\} \\
\{1\} \nsubseteq 1 \\
1 \subseteq 1
\end{align}
$$

## Distinzioni
- [[Insieme finito]]
- [[Insieme infinito]]

## Referenze
- [[Insiemi numerici]]