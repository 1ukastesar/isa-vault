---
tags:
  - škola/VŠ/VUT/ISA
aliases:
---
= Relatime transfer protocol

- Aplikační protokol na přenos hlasových nebo obrazových dat
- obsahuje typ dat, sekveční číslo (protože se posílá přes [[UDP]]), časovou značku
- každý směr komunikace má svůj vlastní kanál (aby komunikace nebyla přepínaná jako na vysílačce), tzn. dva při volání 1-1
- Pro monitorování kvality přenosu se používá [[RTCP]]