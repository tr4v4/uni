---
tags:
  - category/note
  - status/finished
  - topic/linguaggi-di-programmazione
date: 06-10-2024 16:39:14
links:
  - "[[Lecture 01102024110253]]"
---
# Discipline di valutazione
---
## Introduzione
> Una **disciplina di valutazione** è una _regola di valutazione di una [[Relazione|relazione]] di transizione_ all'interno di un [[Sistema di transizione|sistema di transizione]]. In particolare _vincola l'ordine di valutazione di ogni produzione di una categoria sintattica descritta da [[Grammatiche libere|grammatica libera]]_.

In particolare, esistono 6 discipline:
- **IS** (_Interna Sinistra_) - è quella standard, usata da tutti i [[Compilatore|compilatori]] per le espressioni aritmetiche, e consiste nel valutare prima l'espressione sinistra e poi quella destra;
- **ID** (_Interna Destra_) - controparte della IS;
- **IP** (_Interna Parallela_) - consiste nel valutare entrambe le espressioni, ma senza un ordine preciso;
- **ES** (_Esterna Sinistra_) - usata nelle espressioni booleane, consiste nel valutare prima l'espressione sinistra, e poi se necessario anche quella destra ([[Short-circuit evaluation|short-circuit evaluation]]);
- **ED** (_Esterna Destra_) - controparte della ES;
- **EP** (_Esterna Parallela_) - consiste nel valutare una delle due espressioni (senza ordine), e se necessario anche l'altra;

<u>Nota bene</u>: per natura, **le discipline esterne sono tendenzialmente più generali, ossia definite per più stati**. Di conseguenza _la [[Funzione parziale|funzione parziale]] $\text{eval}$ che le realizza ha un dominio definito (con [[Immagine di funzione|immagine]]) più ampio rispetto alle discipline interne_.

## Referenze