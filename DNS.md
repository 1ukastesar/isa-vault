---
tags:
  - škola/VŠ/VUT/ISA
aliases:
---
= Domain Name system

# Architektura
- globální jmenný prostor doménových jmen a [[IP adresa|IP adres]]
- decentralizovaný systém
- Jako hierarchické rozložení, delegace zprávy
## Prostor doménových jmen
- Uspořádání záznamů do podoby invertovaného stromu

![[DNS-2024-12-16--19-45-08-1742186A0E6D0A4127FAC4B8F910BB81.png]]

Doména jako taková je libovolný podstrom, záznamy se zónových souborů, kterým se říká zóny. Doména nicméně jako taková nemusí být celá uložená v jedné zóně, může se skládat z několika zón

**==DOMÉNA NENÍ ZÓNA==**
## Prostor reverzního mapování
### Pro [[IP adresa#IPv4|IPv4]]
![[DNS-2024-12-16--19-45-08-1E1F6ED49055883022561BD395E69EF2.png]]

Pro adresu 147.229.8.12 je záznam v podobě:

12.8.229.147==.in-addr.apra== IN PTR example.com

### Pro [[IP adresa#IPv6|IPv6]]

Podobné jako nahoře, reverzní adresa je ==.ip6.arpa==

v záznamu se adresa píše od konce, mezi každým číslem se dělá tečka:

![[DNS-2024-12-16--19-45-08-6BD85B3E383AA62F5FD1C9A8D5359D4B.png]]

# Správa domén
- [[ICANN]] akredituje registráty pro TLD a generické
- seznam správci TLD (Top level domain) je na [[IANA]]
- ccTLD mají pak národní domény, u nás CZ.NIC, který poté eviduje domény cz a přidává DNS záznam na domény druhého typuj
## Druhy domén
- Domény prvního typu:
	- národní: .cz, .sk. .uk, .rus
	- generické: .edu, .tech, .com, .net
- Domény druhého typu: vutbr.cz, google.com, seznam.cz
- Domény třetího a dalšího:
	- fit.vutbr.cz
	- pc1.fit.vutbr.cz
	- ...

DNS používá [[DNS protokol]] při rezoluci domény. [[DNS server|DNS servery]] Mezi sebou komunikují při přenosu [[Zónový soubor|zón]]

Pro zajištění důvěryhodnosti lze použít [[DNSSEC]]

