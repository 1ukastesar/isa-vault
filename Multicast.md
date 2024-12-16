---
tags:
  - škola/VŠ/VUT/ISA
aliases:
  - multicast
  - multicastu
  - multicastem
  - multicastů
---
# Používané protokoly:
- [[IGMP]] - lokální přepojování pro [[IP adresa#IPv4|IPv4]]
- [[MLD]] pro lokální připojování pro [[IP adresa#IPv6|IPv6]]
- PIM - globální směřování

# Mapování [[MAC adresa|MAC adres]]
## Pro [[IP adresa#IPv4|IPv4]]
- [[Mac adresa]] (dst) má prefix ==01 00 5e== 
- Z [[IP adresa#IPv4|IPv4]] adresy se použije posledních 23 bitů na vytvoření 48 bitové adresy

> [!Warning] Přijímající zařízení nikdy nepoužívají mapovanou MAC adresu jako zdrojovou
### Příklad:
224.==0.0.1== se mapuje na 01:00:5e:==00:01:01==
Nicméně zde může dojít k tzv **imperfect filtering**, kde třeba adresa 225.0.0.1 by měla stejnou [[MAC adresa|MAC adresu]] výše.

### Rezervované adresy
Některé rezervuje [[IANA]], [[IP adresa#Třídy IP Adres|jedná se o třídu D]]

V praxi 224.0.0.1 a ff02::1 má každé připojené zařízení v sítí, obdoba takového broadcastu

![[Multicast-2024-12-16--19-45-09-B7E9C9E7EA18C3F151584F355E19C56B.png]]
## Pro [[IP adresa#IPv6|IPv6]]
- Používá se nižších 32bitů [[IP adresa#IPv6|IPv6]] adresy (tzn 10 bytů ze začátku se ignoruje)
![[Multicast-2024-12-16--19-45-09-8A9E3F3CA5351052B44F8BA261DD3411.png|550]]
- prefix se používá ==33 33==
### Příklad:
ff02::1:==ff3b:bd1c== se mapuje na 33:33==:ff:3b:bd:1c==

