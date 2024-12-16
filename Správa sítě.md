---
tags:
  - škola/VŠ/VUT/ISA
aliases:
---
Jejím úkolem je především:
- monitorování zařízení a uživatelů, jejich správa a nastavení systémů
- autorizace přístupu k zařízením a službám
- sledování zatížení, řešení výpadků a chyb
- bezpečnostní monitoring: útoky, nedovolené chování
- Zálohování a obnova zdrojů


Standart [[FCAPS]]

# Monitorování sítí
## Pasivní
probíhá pouhé sledování toků na sítí a sbírají se z ní informace tvoří statistika (použití sondy na síti)
Příklady pasivních: [[Netflow]], [[SNMP]] traps

## Aktivní
U aktivního monitorování se nečeká pasivně na zprávy, ale probíhá aktivní dotazování koncových sledovaných zařízení na jejich stav, tzv pooling
Příklady: [[SNMP]], [[ICMP]], telnet