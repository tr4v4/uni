---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 12-07-2025 14:46:52
links:
  - "[[Lecture 28042025111320]]"
---
# OFDM
---
## Introduzione
> L'**Orthogonal Frequency Division Multiplexing (OFDM)** è una tecnica di [[Multiplexing wireless|multiplexing wireless]] che consiste nella divisione di un segnale in più portanti ortogonali, permettendo una trasmissione efficiente e robusta in ambienti con interferenze e multipath.

OFDM è ampiamente utilizzato in tecnologie moderne come Wi-Fi, LTE e DVB-T.

## Funzionamento
A differenza del _frequency multiplexing_, in cui ogni canale ha una banda di frequenza (portante) distinta, OFDM utilizza molte sotto-portanti, dette **sub-carriers**, ortogonali che si sovrappongono su uno stesso canale:
![[fdm.png]]
![[ofdm.png]]

Questo consente di migliorare l'efficienza spettrale (_non c'e' bisogno di spazi di guardia!_) e _aumenta il symbol rate_.

Per esempio, IEEE 802.16 (WiMAX), utilizza OFDM in cui ogni singolo canale e' suddiviso da 128 a 2048 sub-carriers, ognuno con una larghezza di banda pari a 9.76 KHz. La [[Modulazione|modulazione]] adottata puo' essere [[BPSK]], [[QPSK]], [[QAM|16-QAM]] o [[64-QAM]], a seconda della robustezza richiesta. In generale, quindi, [[PSK]] e' la modulazione standard per OFDM!
![[WiMAX.png]]

### Ortogonalita'
Qual e' il ruolo dell'ortogonalita'? Fondamentalmente i sub-carriers sono scelti in modo tale che le lor frequenze siano [[Ortogonalità|ortogonali]] tra loro, ossia matematicamente della forma
$$\sin{x}, \ \ \ \sin{kx}$$
o anche
$$\cos{x}, \ \ \ \cos{kx}$$

Infatti, **se due funzioni sono ortogonali, il loro prodotto [[Integrale|integrato]] su un intervallo di periodo e' 0**:
$$\int_{0}^{T} \sin{x} \cdot \sin{kx} \ dx = 0$$

Questo si traduce in una _totale assenza di interferenze tra i sub-carriers_, permettendo di usarli per **inviare piu' dati contemporaneamente**!
![[risultante-subcarriers.png|500]]

### Esempio
Immaginiamo un OFDM con 4 carriers, 1 simbolo per secondo e modulazione BPSK. I bit da inviare sono (rimpiazzando `0` con `-1`):
`1 1 -1 -1 1 1 1 -1 1 -1 -1 1`.

Questa sequenza di bit la dividiamo quindi in 4 sottosequenze, ognuna rappresentata da un sub-carrier:
- _CH1_ (1 Hz) --> `1 1 1`
- _CH2_ (2 Hz) --> `1 1 -1`
- _CH3_ (3 Hz) --> `-1 1 -1`
- _CH4_ (4 Hz) --> `-1 -1 1`

<u>Nota bene</u>: le frequenze dei canali sono ortogonali tra di loro.

Quindi, il segnale inviato sara' la somma dei segnali di ogni canale.

### Codifica e decodifica
Nella fattispecie, il trasmettitore utilizza [[IFFT]] (Inverse Fast Fourier Transform) per combinare i sub-carriers in un unico segnale, che viene poi trasmesso. A partire **dal dominio delle frequenze delle sottoportanti**, l'IFFT genera un **segnale nel dominio del tempo che rappresenta la somma di tutti i sub-carriers**.

Lato ricevente, invece, il segnale ricevuto viene decodificato utilizzando la [[FFT]] (Fast Fourier Transform) per separare i sub-carriers e recuperare i dati originali. Piu' specificamente, a partire **dal dominio del tempo del segnale ricevuto**, la FFT genera un **dominio di frequenze che rappresenta i sub-carriers**.

![[fft-ifft.jpg]]

## Prestazioni
![[ofdm-prestazioni.png]]

Sappiamo che OFDM ha un symbol rate pari a
$$250.000 \text{ sym/s}$$
Questo significa che, anche senza conoscere la tabella, se sappiamo il numero di sub-carriers, il numero di bit per simbolo e la convoluzione usata, possiamo calcolare il throughput:
$$\text{Throughput} = \text{Symbol Rate} \cdot \text{Sub-carriers} \cdot \text{Bits per Symbol} \cdot \text{Convolution}$$

<u>Nota bene</u>: la convoluzione e' la frazione dei sub-carriers che sono effettivamente utilizzati per la trasmissione dei dati, rispetto al totale (gli altri sono usati per la sincronizzazione e il controllo degli errori).

## Svantaggi
Un noto problema di OFDM e' l'**effetto Doppler sui sub-carriers quando il canale e' in movimento** (ad alte velocita'). 

## Referenze