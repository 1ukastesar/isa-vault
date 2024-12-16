---
tags:
  - škola/VŠ/VUT/ISA
aliases:
---
= signal initialization protocol

# Povinnosti protokolu
- registruje uživatele a zařízení do sítě
- uskutečňuje hovory a ukončuje je
- vytváření spojení mezi účastníky prostřednictvím serveru nebo metodou peer-to-peer
- **Stará se pouze o správu před vytvořením hovoru, po vytvoření již nemá za hovor správu!**

# Zprávy (metody) protokolu

- REGISTER
- INVITE společně s [[SDP]]
- OK společně s [[SDP]]
- ACK
- CANCEL
- BYE
# Process spojení při registraci
![[SIP-2024-12-16--19-45-10-EDB62DEBE8549437D285F7CF564C7CF7.png]]
# Proces spojení při volání

```mermaid
sequenceDiagram

actor A as Volající

participant SA as SIP server A

participant SB as SIP server B

actor B as Volaný

  

A->>SA: INVITE

SA->>SB: INVITE

SB->>B: INVITE

  

SB-->>SA: 100 Trying

SA-->>A: 100 Trying

  

B-->>SB: 180 Ringing

SB-->>SA: 180 Ringing

SA-->>A: 180 Ringing

  

B-->>SB: 200 OK

SB-->>SA: 200 OK

SA-->>A: 200 OK

  

A->B: RTP

  

B->>SB: BYE

SB->>SA: BYE

SA->>A: BYE
```

