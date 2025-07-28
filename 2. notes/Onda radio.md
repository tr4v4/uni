---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 06-04-2025 18:00:07
links:
  - "[[Lecture 31032025111817]]"
  - "[[Lecture 01042025152454]]"
---
# Onda radio
---
## Introduzione
> Le **onde radio** sono _onde elettromagnetiche utilizzate per la trasmissione di segnali radio, televisivi e comunicazioni wireless_.

## Proprieta'
### Ampiezza
L'ampiezza di un'onda radio è l'altezza massima dell'onda rispetto alla sua posizione di riposo. Un'ampiezza maggiore indica un segnale più forte, e questa dipende da quanta energia viene usata per trasmetterla.

### Frequenza
La frequenza è il numero di cicli dell'onda che passano attraverso un punto in un secondo. La lunghezza d'onda è inversamente proporzionale alla frequenza, e può essere calcolata con la formula:
$$wavelength = \frac{c}{frequency}$$
dove $c$ è la velocità della luce.

Se un'antenna riceve piu' onde, il risultato che viene ricevuto è la loro somma vettoriale. Per scremare le onde a solo la frequenza che vogliamo è necessario usare i _filtri passa-banda_.

La dimensione dell'antenna è tarata in funzione della lunghezza d'onda da ricevere/trasmettere. In particolare, se facciamo combaciare le lunghezze abbiamo il massimo rendimento energetico ($1:1$), ma va bene anche proporzioni sulle potenze del 2 ($\frac{1}{2}, \frac{1}{4}$).

### Area di coperatura della propagazione
Il decadimento dell'ampiezza è quadratico inverso ($\frac{a}{d^{2}}$), e a volte le condizioni atmosferiche fanno ridurre la potenza di trasmissione in proporzione cubica alla distanza. Di fatto, quindi, la copertura è limitata da una **distanza limite**: oltre quella distanza si sente l'energia dell'onda, ma _non è sufficiente per captare il segnale_.

In particolare possiamo dividere l'area di copertura di un'onda in:
- _trasmissione_, l'area in cui il segnale viene trasmesso, con un basso tasso di errore;
- _detection_, l'area in cui e' ancora possibile ricevere il segnale, ma con un alto tasso di errore (comunicazione impossibile);
- _interferenza_, l'area in cui il segnale si confonde con il rumore di fondo, per cui non e' neanche possibile riceverlo.

In generale le regole sono:
- le _alte frequenze sono buone per distanze brevi ma più affette dagli ostacoli_;
- le _basse frequenze sono buone per lunghe distanze ma meno affette dagli ostacoli_;

### Fase
La fase è la posizione di un punto in un ciclo dell'onda. E' lo shift rispetto alla posizione iniziale di emissione dell'onda. La fase è importante perché può influenzare la qualità del segnale ricevuto. Infatti:
- aspetti positivi --> **fasi simili possono aumentare l'ampiezza delle onde catturate** (vengono ricevute come somme vettoriali);
- aspetti negativi --> **fenomeno di cancellazione se le fasi sono opposte**, o comunque se le frequenze sono diverse.

### Polarizzazione
La polarizzazione fa riferimento al campo elettrico dell'onda, e dato che questo e' parallelo all'antenna, corrisponde alla direzione di questa rispetto alla terra. Le due polarizzazioni principali sono:
- **verticale**, quella usata nelle WLAN;
- **orizzontale**.

Se un'_antenna trasmette un'onda polarizzata verticalmente, e un'altra antenna riceve un'onda polarizzata orizzontalmente, il segnale ricevuto sarà molto debole_.

Se si usa una polarizzazione diversa o addirittura opposta rispetto a quella dell'antenna, per poter ricevere o trasmettere il segnale, sara' **necessario aumentare l'ampiezza dell'onda, e quindi usare piu' energia**!

### Guadagno di segnale
Il guadagno di segnale è la _capacità di un'antenna di aumentare l'ampiezza del segnale ricevuto_. Esistono due tipi di guadagni:
- **guadagno attivo**, che richiede energia aggiuntiva per amplificare il segnale, mediante un _amplificatore_;
- **guadagno passivo**, che sfrutta il segnale proveniente dalla sorgente con una _parabola che fa convergere tutti i riflessi del segnale in un punto_ (fuoco), aumentando l'ampiezza senza usare energia aggiuntiva.

### Perdita di segnale
Durante la trasmissione di un'onda radio, parte dell'energia viene dispersa in calore o viene riflessa. Questo fenomeno è noto come _perdita di segnale_.

### Effetti della propagazione
La propagazione del segnale può essere influenzata da diversi fattori, tra cui:
- **fading**, effetto della mobilità delle reti wireless;
- **shadowing**, le onde sono assorbite dagli ostacoli;
- **reflection**, le onde sono riflesse dagli ostacoli;
- **refraction**, le onde sono deviate dagli ostacoli;
- **scattering**, le onde sono disperse dagli ostacoli;
- **diffraction**, le onde sono divise dagli ostacoli.

Inoltre, se si aggiunge il fatto che un singolo segnale puo' prendere percorsi differenti tra il trasmettitore e il ricevitore (**multipath propagation**), e quindi _arrivare in forme e latenze differenti a destinazione_, si capisce quanto sia complessa la trasmissione di segnali radio.

## Referenze