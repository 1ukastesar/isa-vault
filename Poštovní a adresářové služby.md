---
tags:
  - škola/VŠ/VUT/ISA
aliases:
  - maily
---
# Architektura
![[Poštovní a adresářové služby-2024-12-16--19-45-13-6365FFF2113848288D48153A1C60B7E4.png]]
- MUA - mail user agent - klientská aplikace
- MTA - mail transfer agent - přeposílá maily od MUA do schránky na vzdáleném serveru nebo do lokálního serveru
- Dále potom využívá [[DNS]]
# Formát pošty
- 7bitové ASCII u SMTP, na posílání jiného druhu obsahu slouží MIME, které zprávu rozdělí na části a kóduje je vlastním způsobem (quoted printable, base64)
## Formát zprávy
- Zpráva se skládá ze tří částí:
### Obálka
- vytváří a rozbaluje MTA
- obsahuje pole:
	- od koho (mail from)
	- komu (rcpt to)
### Hlavička
- vytváří MUA
- obsahuje pole jako
	- Recieved
	- From
	- To
	- Message ID
	- Date
# Tělo
- vytváří MUA
- kóduje se pomocí MIME do částí

# Srovnání IMAP a POP3

| Činnost              | IMAP                                                                              | POP3                                                                                               |
| -------------------- | --------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| Přístup ke schránkám | Několikanásobný přístup ke schránkám z různých klientů                            | Pouze jeden přístup, při práci se schránka zamkne proti úpravám                                    |
| Práce se schránkami  | libovolné                                                                         | pouze INBOX, lokálně lze více                                                                      |
| Práce s obsahem      | Průběžné aktualizace z klienta na server, lze stáhnout jen hlavičky při připojení | Celý obsah přenesený ke klientovi a změny se nahrávají až po ukončení sezení (riziko ztráty práce) |
| Další funkce         | atributy zprávk (seen, unread, draft)                                             | nic                                                                                                |
# Ochrana proti podvržení
## SPF = sender policy framework
- MTA po přijetí emailu z obálky vyčte odesílatele doménu
- Podle získané domény zkontaktuje [[DNS]] a zjistí ze záznamu [[Zónový soubor#TXT|TXT záznam]]
- Podle záznamu z DNS ověří IP adresu odesílatele dotazem na DNS k IP adrese a srovná příchozí email, jestli se shoduje
## DKIM = Domain key identified mail
- vlastník mailového serveru udělá soukromý a veřejný klíč
- veřejný klíč dá do [[DNS]] [[Zónový soubor#TXT|TXT záznamu]]
- soukromým klíčem bude podepisovat všechny maily, do hlavičky vloží DKIM sig
- Příjemce podle záznamu v DNS ověří veřejným klíčem pravost