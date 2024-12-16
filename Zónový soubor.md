---
tags:
  - TBD
aliases:
  - Zonový soubor
---
# Typ záznamu
![[Zónový soubor-2024-12-16--19-45-15-177CEECD6EDCA024A395D46F894141E1.png]]
# Zóna
## Doména

### Záznamy pro primární server
```
zone "moje-domena.cz" {
	type master;
	file "moje-domena.cz";
};
```

#### Reverzní záznam pro doménu
```
zone "16.172.in-addr.apra" {
	type master;
	file "172.16";
};
```

### Záznamy pro sekundární server

```
zone "moje-domena.cz" {
	type slave;
	file "moje-domena.cz";
};
```

#### Reverzní záznam
```
zone "16.172.in-addr.apra" {
	type slave;
	file "172.16";
};
```

## Hint soubor
```
zone "." {
	type hint;
	file "named.root";
};
```

# Záznamy v zónách

> [!warning] Je nutné používat FDQN, aby nedošlo k doplnění na doménu specifikovanou v zoně


## SOA
- každá zóna má právě jeden SOA záznam
- obsahuje ==název primárního serveru== a ==email správce== (zavináč se dává jako první tečka v emailu, protože zavináč znamená nahrazení za FDQN v souboru)
- pro reverzní soubory platí stejná "hlavička" SOA záznamu, jen dále jsou záznamy s ip adresami na levé straně
### Parametry
- **Serial** - při každé změně by se mělo měnit
- **Refresh** - interval na obnovu záznamů na [[DNS server#Sekundární server (slave)|sekundárním serveru]]
- **Retry** - doba čekání na další pokud, pokud se první nepodaří
- **expire** - maximální doba expirace záznamu po kterém musí sekundární server  [[DNS protokol#Přenos zón|stáhnout záznamy z primárního]]
- **minimum** - implicitní doba pro jednotlivé záznamy pokud nemají specifikováno
```
$TTL 3600
 @ 	IN	 	SOA ns.moje-domena.cz. root.pc1.moje-domena.cz.(
				20050311	;Serial
				3600 		;Refresh
				900 		;Retry
				3600000		;Expire
				3600) 		;Minimum
 
	IN NS 	ns.moje domena.cz.
ns 	IN A 	192.168.5.35

```

## NS
- určuje [[DNS server|autoritativní servery]] pro danou doménu
- Slouží k budování hiearchické struktury DNS

> [!info] Odlišit sekundární od primárního lze přes dotazem na SOA záznam

## A
- mapování doménového jména na [[IP adresa#IPv4|IPv4 adresu]]
```
fit.vutbr.cz.  3600  IN  A  147.12.53.125
```
## AAAA
- mapování doménového jména na [[IP adresa|IPv6]] adresu
```
www.cesnet.cz.  3600  IN  A  2001:fc03:f3::2953
```
## NAPTR
- slouží pro [[DNS#Prostor reverzního mapování|reverzní záznamy]]  z [[IP adresa|IP adresy]] na doménové jméno
1. Pro [[IP adresa|IP adresu]]: 147.23.229.13:
```
13.229.23.147.in-addr.apra.  3600  IN  NAPTR  fit.vutbr.cz.
```
## CNAME
 - aka Canonical name
 - mapuje alias na kononické jméno počítače
 - jedná se o symbolická jména pro WWW, DNS a Name servery

> [!warning] U CNAME nesmí alias nikdy být na pravé straně záznamu

```
www.vutbr.cz.  3600  IN  CNAME  vutbr.cz.
vutbr.cz.  3600  IN  A  47.215.150.2
```
## MX
- lokalizace mailových serverů pro danou doménu

> [!warning] Nižší číslo znamená vyšší prioritu

```
stud.fit.vutbr.cz.  3600  IN  MX  10  eva.fit.vutbr.cz.
stud.fit.vutbr.cz.  3600  IN  MX  20  merlin.fit.vutbr.cz.
```

## SRV
- lokalizace služeb např [[SIP]]
- formát:
\_Service.\_Proto.name. TTL Class SRV PRIORITY WEIGHT PORT TARGET

- priority - jako u MX záznamů tj. nižší hodnota je vyšší priorita
- weight - podle poměru rozdělí zátěž
```
_sip._udp.cesnet.cz.  3600  IN  SRV  20  3  8080  cyrus.cesnet.cz.
```
## TXT
- uchovává textová data