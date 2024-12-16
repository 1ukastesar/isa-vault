---
tags:
  - škola/VŠ/VUT/ISA
aliases:
---
= Internet Control message protocol

Řidí tok a detekci nedosažitelných uzlů na [[IP adresa|IPv4]]. Pro [[IP adresa|IPv6]] je dostupný [[MLD]]

- paket nad [[OSI model#Internetová vrstva (L3)]] je-li zahozen, vygeneruje se ICMP paket který se pošle zpět:
	- toto platí jak pro [[TCP]]
	- tak i [[UDP]]


> [!warning] ICMP paket se v případě chyby generuje pouze u unicastu



Je součástí protokolu IP, protože **v hlavičce protocol má hodnotu 1**

![[ICMP-2024-12-16--19-45-09-0788A79C1AEC0B4EDD57E83A224454E9.png]]