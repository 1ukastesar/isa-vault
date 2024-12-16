---
tags:
  - škola/VŠ/VUT/ISA
aliases:
  - metoda zásobníku žetonů
---
> [!Question]- Omezení toku na základě objemu. Je tok 6000B/min omezený víc než 100B/s?
> u 6000B/min je méně omezený, protože dokáže v špičce přenést tisíce bajtů za sekundu za předpokladu, že ve zbytku přenášet data nebude. 
> Čím delší je teda časové okno, tím je větší možnost mít větší špičky

- žeton reprezentuje povolení na prostup daného paketu bránou
- žetony se generují, dokud se nenaplní fronta na žetony

> [!Info] Jedná se o model s pamětí (pamětí jsou žetony)

![[Token bucket-2024-12-16--19-45-14-96831149A1EAC63BCEE45F8490D66AA4.png]]

# Jednotky
CBS - Committed burst rate (velikost)
CIR - Commited information rate: (rychlost)
PIR - Peak information rate - závisí ne velikosti zásobníku
	PIR = CBS / T + CIR