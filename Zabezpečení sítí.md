---
tags:
  - škola/VŠ/VUT/ISA
aliases:
---
# Požadavky na bezpečnost
## Důvěrnost
- aka šifrování, kdo data nemá vidět je neuvidí
## Integrita
- s datama nebylo po cestě manipulováno
## Autentizace
- je odesílající důvěryhodný?
## Neodmítnutelnost
- kdo se tam podepíše, ten to poslal
## Kontrola přístupu

# Symetrické šifrování

> [!fail] Problém
> distribuce klíčů

# Asymetrické šifrování

> [!fail] Problém
> Ověření pravosti veřejného klíče



# Podepisování

> [!Question]- Co je to podpis?
> Zašifrovaný hash dat soukromým klíčem


> [!Warning]- Podpis NENÍ soukromý klíč
> podpis vznikne aplikací podpisu na nějaké data. To znamená že podoba podpisu je pro každé data jiná
> **bez dat není podpis**

# Certifikáty
## CA
- důvěryhodná instance, která prokazuje pravost veřejného klíče vydavatele
- funguje na hiearchickém principu, ověření podpisu CA se používá vyšší instance (kořenová CA)
- Digitální certifikát
	- ověřuje platnost veřejného klíče a vlastnictví vydavatele veřejného klíče

# Zabezpečení na vrstvách [[OSI model#TCP/IP Model|TCP/IP modelu]]
![[Zabezpečení sítí-2024-12-16--19-45-15-4E8B295E4A04FA156462D412711F881E.png]]

