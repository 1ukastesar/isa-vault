---
tags:
  - škola/VŠ/VUT/ISA
aliases:
  - metoda tekoucího vědra
---
- analogie vědra s vodou s dírou na spodu
![[Leaky Bucket-2024-12-16--19-45-13-981209C634D6C6AB7253E987AD866920.svg]]
# Implementace
- používá se fronta [[FIFO]]
- čítač
- časovač
## Podmínky
1. Na vstup mi chodí data, o určité velikosti. Každý čas N inkrementuji proměnnou u časovače (podle stanoveného průtoku) a pustím tolik dat, které jsou menší nebo rovno čítači. 
2. Poslaná data odečtu z čítače a proces opakuji. 
3. Pokud žádná data nemůžu v daný okamžik poslat, čekám, dokud čítač nebude větší, abych data mohl poslat
4. Pokud je vědro prázdné, čítač se neinkrementuje a čeká se na příchozí data


> [!NOTE] Model popisuje způsob [[Traffic shaping]]
> V případě, že velikost vědra se sníží na minimum pro potřebnou rychlost, stane se z modelu [[Traffic policing]]
