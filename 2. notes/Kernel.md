---
tags:
  - category/note
  - status/finished
  - topic/sistemi-operativi
date: 15-03-2025 17:45:15
links:
  - "[[Lecture 27022025151550]]"
  - "[[Lecture 28022025091715]]"
  - "[[Lecture 06032025151956]]"
---
# Kernel
---
## Tipologie
Esistono diverse tipologie di kernel:
- [[Kernel monolitico|monolitici]]
- [[Microkernel|microkernel]]
- [[Kernel ibrido|ibridi]]
- [[ExoKernel]] - si partizionano le risorse del sistema per scopi diversi; non fornisce system call, fornisce solo supporto ad altri sistemi operativi
- [[AnyKernel]] - i driver possono essere caricati in user space --> estremamente comodo per sviluppare device driver; il concetto può essere esteso a file system e stack di rete

## Schema
![[kernel-schema.png]]

## Referenze