---
tags:
  - škola/VŠ/VUT/ISA
aliases:
  - NATem
  - NATu
---
= Network address translation

Jedná se o překlad [[IP adresa|IP adres]] z jedné skupiny na jinou

NAT se rozděluje na mapování:
- 1:1 - kde jedna adresa se mapuje na jinou adresu
- 1:N - kde N adres z LAN se mapuje na jednu vnější (veřejnou adresu) - nazývané také jako PAT (port address translation) nebo NAPT (network port address translation)

![[NAT-2024-12-16--19-45-09-D145D31037BB6B245454EEA3BFA3CB43.png]]

V Praxi se často PAT zaměňuje právě s NAT, protože NAT jako takový dělá M:N překlad adres, zatímco PAT z definice je 1:N mapování