---
tags:
  - škola/VŠ/VUT/ISA
aliases:
  - zajištění kvality služeb
  - Quality of Service
  - qos
---
> [!question]- Čím se zajišťuje kvalita přenosu?
> Na přepínačích pomocí front

- Řeší se na úrovni [[OSI model#Internetová vrstva (L3)|L3]]

> [!info] Existují metody na vyšší úrovni
> - pro [[OSI model#Transportní vrstva (L4)]] je u [[TCP]] sliding window
> - na vyšší vrstvách si v protokolu vymění rychlost spojení a podle toho posílají data


- dívá se na hlavičky, zejména na Type of service, ale i příchozí adresa, odchozí, apod

> [!info] Na ToS se dívá u [[DiffServ]]

# Definice požadavků
- pomocí SLA (Service level agreement)
## Co obsahuje SLA
- latence
- rychlost
- ztrátovost
- jitter
# Prostředky pro regulaci provozu

## Podle modelace provozu
- [[Traffic policing]]
- [[Traffic shaping]]

## Podle řízení rychlost
- [[Leaky Bucket]]
- [[Token bucket]]

> [!Question]- Je některá z uvedených metod lepší?
> **Záleží na použití:**
> - například u [[VoIP]] při použití fronty by se pakety mohly zbytečně zpožďovat, proto je lepší je zahazovat
> - u nekritických provozů naopak stojí za to, nechat burst data ve frontě a zpracovat je stanovenou rychlostí
# Prioritizace provozu
- [[DiffServ]]
- [[IntServ]]
- [[RSVP]]
- Preventivní uvolňování front ještě před zahlcením:
	- [[RED]]
	- [[WRED]]
# Řešení v praxi

## Mezi ISP
![[QoS-2024-12-16--19-45-14-C4E4B60F342D696639BA1AF2F7957D22.png]]

## Na hardwarových prvcích
- hardware má pouze jednu frontu, kde neumí řešit prioritu
- V praxi se priorita ==řeší vždy pomocí softwaru== a to takovým způsobem, že se implicitně používá hardwarová fronta dokud se nezaplní a poté se začne řešit priorita softwarem
- jakmile se naplní všechny fronty, nové příchozí pakety se začnou zahazovat

![[QoS-2024-12-16--19-45-14-9BA280A6AB150D22B7E2159C1C5CDEDD.png]]

## Na prioritizaci provozu
- pomocí [[FIFO]]
> [!NOTE] Implicitní způsob zpracování je pomocí jednoduché FIFO fronty

### Druhy
#### Prioritní fronta
- jedna prioritní fronta a potom další běžná neprioritní

> [!Warning]- Neprioritní fronta je závislá na prioritní, což způsobí:
> - nevíme rychlost obsluhy (neprioritní) fronty
> - maximální doba zpoždění může být nekonečná a **hrozí riziko vyhladovění**
#### Round-Robin fronty
- stejný objem přenesených dat
- cyklicky se vybírá určitý počet paketů z každé fronty
- toky se dynamicky mění - fronty se vytváří pro různá spojení
- výpočet rychlost a zpoždění jako u fronty, ale jen se dělí počtem front

#### Váhové fronty
- podle poměru se odebírá různý počet paketů z každé fronty