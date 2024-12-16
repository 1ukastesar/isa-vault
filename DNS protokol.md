---
tags:
  - škola/VŠ/VUT/ISA
aliases:
---

# Popis protokolu
- Jedná se o aplikační protokol nad [[UDP]] ([[TCP]] v případě přenosu zón) na portu 53
## Zpráva obsahuje:
- Hlavičku
- Dotaz
- Odpověď
- Authority sekci
- Additional

![[DNS protokol-2024-12-16--19-45-12-1E288D120502A7DAEC128AD62A69F55A.png]]
# Rezoluce DNS
- Klient, který chce vykonat rezoluci domény má od DHCP přidělený server (a nebo ho má v systému natvrdo nastavený)
- dotáže se tedy lokálního DNS serveru, pokud již nemá v cache výsledek
- Lokální DNS server pokud také nemá v cache výsledek se začne postupně dotazovat root serverů na dotaz, k zjištění [[IP adresa|IP adresy]] root serveru má speciální zónový soubor named.root se zónou hint
```mermaid
sequenceDiagram

actor C as Client

participant lD as Local DNS

participant rS as Root server

participant tS as TLD CZ server

participant dS as Domain VUT server

  

C->>+lD: query A www.vubr.cz

  

Note over C,lD: Rekurzivní dotaz

Note over lD,dS: Iterativní dotaz

lD->>+rS: query A www.vutbr.cz

rS->>-lD: no A NS: d.nic.cz

  

lD->>+tS: query A www.vutbr.cz

tS->>-lD: no A NS: pitpit.vutbr.cz

lD->>+dS: query A www.vutbr.cz

dS->>-lD: response A 147.54.30.29

  

lD->>-C: response A 147.54.30.29
```

# Přenos zón
- probíhá **mezi sekundárním a primárním serverem**
- sekundární využívá metodu pooling a vyzývá primární server o nová data, podle refresh intervalu v SOA záznamu
- lze použít ==DNS notify== (z masteru na slave)
```mermaid
sequenceDiagram

participant S as Secondary name server

participant P as Primary name server

  

S->>+P: SOA query for zone

P->>-S: SOA query answer

S->>+P: IFXR/AFXR query to zone

Note over S,P: IFXR - incermental file exchange request<br/>AFXR - all file exchange request

P->>-S: IFXR/AFXR answer (zone transfer)
```