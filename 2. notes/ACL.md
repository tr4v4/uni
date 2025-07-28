---
tags:
  - category/note
  - status/finished
  - topic/reti-di-calcolatori
date: 30-03-2025 22:04:30
links:
  - "[[Lecture 10032025112014]]"
---
# ACL
---
## Introduzione
> Un **ACL** (Access Control List) è un insieme di regole di firewalling per consentire o non consentire l'entrata di certi [[Pacchetto|pacchetti]] nella rete locale. Viene usata di solito all'interno dei [[Router|router]] come sorta di [[Firewall|firewall]].

Un esempio di regola di ACL potrebbe essere:

| action | source address       | dest address         | protocol | source port | dest port | flag bit |
| ------ | -------------------- | -------------------- | -------- | ----------- | --------- | -------- |
| allow  | 222.22/16            | outside of 222.22/16 | TCP      | > 1023      | 80        | any      |
| allow  | outside of 222.22/16 | 222.22/16            | TCP      | 80          | > 1023    | ACK      |
| allow  | 222.22/16            | outside of 222.22/16 | UDP      | > 1023      | 53        | ----     |
| allow  | outside of 222.22/16 | 222.22/16            | UDP      | 53          | > 1023    | ----     |
| deny   | all                  | all                  | all      | all         | all       | all      |

## Referenze