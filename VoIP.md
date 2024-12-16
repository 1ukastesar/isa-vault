---
tags:
  - škola/VŠ/VUT/ISA
aliases:
  - voip
---
# Architektura

![[VoIP-2024-12-16--19-45-11-C1C026922646A6629F77FDD873FFAAD4.png]]

model klient - server architektura
- **SIP klient** - hardware/software telefon, který převádí hlas na IP datagramy, přes něj se iniciuje hovor a přijímá hovor
- **SIP server** - sw aplikace, eviduje registrované uživatele, vytváří a směřuje hovory

Na rezoluci adres se používá [[DNS protokol]]

Na získání [[IP adresa|IP adres]] jednotlivým zařízením zajišťuje [[DHCP]]

## Použité protokoly
- Signalizace během a při vytváření hovoru: [[SIP]]
- Přenos dat (video / zvuk): [[RTP]]
- Pro zvolení protokolu při uskutečňování: [[SDP]]
# Požadavky na VoIP
- Je nutné dostatečné přenosové pásma
- zajistit kvalitu přenosu i odezvu
- po právní stránce zajistit tísňové volání, případně napojení na [[Hlasové služby|PSTN]]
- spolehlivost a dostupnost jako PTSN (k lepší adopci zákazníků)
- bezpečnost (autentizace, důvěrnost, zneužití)

> [!Info] V případě přenosu hlasu je žádoucí, aby zpoždění bylo do 400ms u hlasových paketů

# Potenciální problémy
- napájení telefonů (lze řešit přes PoE)
- Mobilita a dostupnost sítě (přenosy jsou uskutečněné přes IP namísto vyhraněných vysílačů)

# Převádění hlasu
- zvuk přes ADC převodník, oseknutí frekvencí, které jsou typické pro lidský hlas (3,8 - 8 khz), data rate 64kbps, dále přes nějaký kodek na komprimaci

## Příklad:
![[VoIP-2024-12-16--19-45-11-9821962DB46FC1AD06F23EC3FB56BAAD.png]]

64kbps je data rate pro přenos (měl bych vědět)

58B režie za 20 ms => za 1s je to 2900B => převod na bity = 23200b režie za 1s
plus objem dat za sekundu +64 000b

= 84200b

# Zabezpečení VoIP

- hrozí bezpečnostní rizika, jako je odposlech, nebo neautorizované použití služby
- Lze oddělit provoz na VLAN nebo použít zabezpečení spojení pomocí: [[IPsec]], Secure RTP, SIP over [[TLS]]
# Jiné soukromé řešení
Whatsapp, Messenger, Discord, Viber
- stejně jako VoIP řeší registraci a přihlašování uživatelů do sítě, směřování hovorů, adresace hovorů, přenos hlasových a obrazových dat
- Ale mají vlastní technologii, která není kompatibilní se službami na venek, data jsou v rámci dané firmy a není garantované, že daná služba bude fungovat i za další roky