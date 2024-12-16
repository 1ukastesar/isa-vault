---
tags:
  - škola/VŠ/VUT/ISA
aliases:
  - OSI modelu
  - OSI modelem
---
![[OSI model-2024-12-16--19-45-10-E3CB32BE4B8F92EBF1F3C081F0E0D021.png]]

![[OSI model-2024-12-16--19-45-10-474DCB3157E463908F667B49C4AE7CEA.png]]

> [!Info]- V praxi nejsou vždycky vrstvy oddělené dokonale podle modelu
> Například u [[Switch|switchů]] dochází k tzv [[IGMP#IGMP snooping]] kde [[switch]] již neoperuje na nejnižší vrstvě

# TCP/IP Model
- používá se v praxi více

## Vrstva síťového rozhraní (L1 - L2)
- implementace v síťové kartě (NIC - network interface card)
- zahrnuje přenosy signálu přes datový kabel, napěťové špičky a dekódování signálu na logické 1 a 0
- spojení konektorů a pinů
- Na této vrstvě dochází k přenosu pomocí rámců a adresování je uskutečněno pomocí [[MAC adresa|MAC adres]]
- **[[PDU]] jednotka je Bit a rámec**
- max délka rámce je 1500 B
- vytváří spojení mezi počítači (mezi procesy potom [[#Transportní vrstva (L4)]])
## Internetová vrstva (L3)
- implementace v síťových modulech operačních systémů
- směřuje datagram na vzdálený počítač, definuje způsob adresování, přenáší data mezi internetovou vrstvou a fyzickým rozhraním
- PDU je [[IP paket]]
- adresování je pomocí [[IP adresa]]
- zajišťuje doručení s největším úsilím (best effort delivery) - doručuje data nejvhodnější cestou, ale neodkáže zajistit jejich samotné doručení
- Vrstva používá protokoly [[ARP]], [[IGMP]] a [[ICMP]]

## Transportní vrstva (L4)
- nachází se zde [[UDP]] datagramy a [[TCP]] segmenty
- vytváří logické spojení mezi procesy (narozdíl od [[#Vrstva síťového rozhraní (L1 - L2)]])
- Adresace je pomocí [[Síťový port|portů]]

## Aplikační vrstva (L5-L7)
Tvoří jí aplikace a procesy, které mezi sebou komunikají




# Komunikace klienta a serveru:
![[OSI model-2024-12-16--19-45-10-4226D6BCDA258E01116979067C5389FE.png]]

Při programování komunikace se využívají [[Sockets]] (neboli schránky)

