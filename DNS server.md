---
tags:
  - škola/VŠ/VUT/ISA
aliases:
---
# Primární server (master)
- obsahuje úplné ==autoritativní== záznamy o doménách
- pro každou doménu existuje **jeden primární** server (je vždy v [[Zónový soubor#SOA|SOA]] záznamech)
# Sekundární server (slave)
- uchovává ==autoritativní== kopie záznamů od primárního
- žádá o [[DNS protokol#Přenos zón|přenos zón]]

> [!NOTE] Poznámka
> Z pohledu [[Zónový soubor#NS|NS záznamů]] jsou autoritativní jak sekundární, tak i primární server, rozlišit je lze pouze přes [[Zónový soubor#SOA|SOA záznamy]] 
# Záložní server (caching-only)
- přijímané dotazy předává dalším serverům
- ukládá odpovědi do cache
- poskytuje úplně neautoritativní odpovědi

