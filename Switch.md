---
tags:
  - škola/VŠ/VUT/ISA
aliases:
  - switche
  - switchu
  - switchů
  - swtichem
---
Síťový prvek pracující na [[OSI model#Vrstva síťového rozhraní (L1 - L2)| L1-L2 vrstvě]]
# [[IGMP]] / [[MLD]] snooping
Switch provádí analýzu vyšší vrstvy (L3+) a sleduje [[IP adresa|IP adresu]] zařízení a fyzický port, které zařízení má zájem o data a tomu portu to pak pošle.

Pokud zařízení snooping neumí, posílá vždy [[Multicast|multicast]] data do všech fyzických portů, protože cílová [[MAC adresa]] [[Multicast|multicastu]] nikdy ze zařízení nebude jako zdrojová