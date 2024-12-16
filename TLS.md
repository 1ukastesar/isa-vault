---
tags:
  - škola/VŠ/VUT/ISA
aliases:
  - tls
---
= Transport layer security

- Pracuje nad [[OSI model#Transportní vrstva (L4)|L4]] vrstvou
- zabezpečuje vrstvy nad sebou, zejména aplikační a jejich protokoly
- Při vytváření spojení si strany vyměňují klíče asynchronní kryptografií pomocí DH nebo RSA
- po výměně symetrického klíče dochází ke komunikaci symetrickou kryptografií
# Handshake
```mermaid
sequenceDiagram

actor C as Client

participant S as Server

  

C->>S: Client Hello<br/>TLS version, supported cipher algorithms

S->>C: Server Hello<br/>choosen TLS version and cipher algo

S->>C: Server certificate with PK (public key)

Note left of C: Client verifies certificate<br/> with CA

Note over S,C:Both sides creates based on method<br/>its public and private keys<br/><br/>DF (Diffie) with eliptic curver or<br/>RSA key exchange or<br/>AES, etc...

S->>C: Server key exchange<br/>with digital signiture (previous msg)

S->>C: Server Hello done

C->>S: Client key exchange

C->>S: Change cipher spec<br/>from now msg have encypt

C->>S: Finished<br/>encrypted summary of previous mesages

S->>C: Change cipher spec

S->>C: Finished<br/>with encrypted summary of conversation
```