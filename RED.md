---
tags:
  - škola/VŠ/VUT/ISA
aliases:
---
Metoda prevence zahlcení
# Chování bez prevence zahlcení
![[RED-2024-12-16--19-45-14-FFD93DC159BBB505925F3B393B9EC3E7.png]]


> [!warning]- Hrozí vyhladovění TCP
> Při maximálním vytížení se Window hodnota v [[TCP]] paketu začne snižovat a toky TCP se zpomalí
> Zatímco TCP se přizpůsobuje na základě dropnutých paketů, [[UDP]] takové mechanismy nemá a hrozí, že stávající a nové [[UDP]] pakety zahltí linku

# Princip fungování
- RED na základně vytížení linky má stanovený threshold, při kterém ==začne náhodně zahazovat== jak UDP tak i TCP pakety ze vstupní fronty.
- Pokud dojde k maximálnímu vytížení, dropuje se vše v příchozí frontě
![[RED-2024-12-16--19-45-14-CFB89565F348B7E16077B5FE8C03B591.png]]

# Efekt aplikace
- Dochází k vyhlazení TCP
- prevence proti vyhladovění TCP
![[RED-2024-12-16--19-45-14-42BC519266719035DC779DB676150430.png]]