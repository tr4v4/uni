---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 06-04-2025 17:54:39
links:
  - "[[Lecture 31032025111817]]"
  - "[[Lecture 07042025111854]]"
---
# Rete wireless
---
## Introduzione
Per capire come funzionano le [[Rete|reti]] wireless bisogna prima di tutto studiare le caratteristiche delle [[Onda radio|onde radio]]. Inoltre e' necessario conoscere i concetti di [[VSWR]], [[Intentional radiator|intentional radiator]] ed [[EIRP]]. Infine, bisogna avere un po' di domestichezza con l'unita' di misura dei deciBel (dB), deciBel-milliWatt (dBm) e con le loro scale di conversione con i milliWatt, che sono (in quanto logaritmiche):
![[mW-dB-conversion-table.png]]

![[db-mw-conversion.png]]

Per calcolare la differenza tra due rilevazioni (RX e TX) in mW si usa la formula seguente, che da' il risultato in dB:
$$\text{PowerDifference} = 10 \cdot \log\left(\frac{\text{RX}}{\text{TX}}\right)$$

Per convertire invece mW in dBm:
$$P_{dBm} = 10 \cdot \log(P_{mW})$$

<u>Attenzione</u>: la scala dei dBm parte come riferimento da 1mW=0dBm.

### dBi
Il dB-isotropic e' la misura del guadagno passivo di un'antenna (in quanto non isotropica). Si dice quindi che un'antenna reale ha un guadagno passivo in una certa direzione di $x$ dBi. Valgono le stesse scale di conversione del dB (quindi +3dBi significa un raddoppio dell'energia ottenuta dall'intentional radiator nella direzione dell'antenna).

<u>Nota bene</u>: guardando il guadagno in dBi nella direzione preferenziale di un'antenna reale si può sapere qual è il suo EIRP e capire se è in regola con i limiti.

### dBd
Il dB-dipole e' l'opposto del dBi: e' il guadagno passivo normalizzato da un'antenna non isotropica. Vale che
$$x \text{ dBd} = y \text{ dBi} - 2.14$$

## Power monitoring
La sensibilita' nei dispositivi moderni sta nel range $[-90, \cdots, +10]$ dBm. A seconda della potenza in questo range si ha:
- _signal detection_ (se riesco a capire ciò che ricevo)
- _signal detection power_ (con quale tecnica trasmetto)
- _channel status detection_ (capire se il canale è occupato o meno, e quindi se posso trasmettere o no)

### RSSI
RSSI sta per Received Signal Strength Indicator, e si concretizza nelle tacchette del wifi su ogni dispositivo.

La scala di RSSI non e' standard, cambia da device a device! Quindi se per esempio hai due dispositivi con diversa scala di RSSI, alla stessa distanza da una sorgente di segnale con una certa potenza in dBm, allora non puoi stabilire quale dispositivo e' migliore sulla base dei loro RSSI.

## Referenze