---
tags: 
aliases:
  - PSTN
---
# Architektura PSTN
![[Hlasové služby-2024-12-16--19-45-08-0CDB1868931F4DF5FEA15436523A86AA.png]]

## Koncové zařízení
Analogové nebo digitální telefony, jedná se o zařízení se sluchátkem k uskutečňování hovorů tak aby osoba mohla přes něj jak mluvit, tak i poslouchat. Takové zařízení umožňuje provádět signalizaci.

## Smyčky
Jedná se o sadu drátů, které se používají na propojení ústředen mezi sebou a i různých poskytovatelů, dělí se dále jako:
- lokální smyčky (local loops) - ty spojují zákazníka do lokální sítě od jeho ústředny
- páteřní (trunks) - tyto smyčky propojují páteřní ústředny (CO) a nebo dvě centrální ústředny dvou poskytovatelů (interoffice trunks)

## Přepínače, ústředny (switches)
Jedná se o zařízení, které ukončují smyčku (smyčka je několik drátů, které vzájemně propojují [[Switch|switche]]). Vytváří signalizaci a vytváří / ukončují hovory a v případě, že se koncové zařízení, kam se chce volat nachází mimo, zajišťují i směřování. Pokud je hovor mimo síť, poskytují přepínaným spojením hovor do klasické telefonní PTSN sítě.

### Ústředny se dělí na dva druhy:
- PBX (= private branch exchange), které se nacházejí u zákazníků a propojují koncová zařízení se zbytkem sítě
- CO (Central Office)

# Signalizace
Jsou tři druhy:
## 1. Kontrolní
zvednuto --> vyzvánění --> zavěšeno
## 2. Adresová
tónová volba
## 3. Informační
oznamovací tón, obsazovací tón, neznámé číslo


# Srovnání PSTN a [[VoIP]]
- Klasická telefonie garantuje šířku pásma na hovor, pokud hovor započte, je jistota, že mi šířka zůstane po celou dobu telefonního hovoru
- Koncové zařízení můžou být napájené z ústředny
- dobrá kvalita, spolehlivost, standardizace
- garance možnosti použít tísňového volání