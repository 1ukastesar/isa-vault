---
tags:
  - škola/VŠ/VUT/ISA
aliases:
---
# Popis
- Implementace pomocí rezervace zdrojů pro jednotlivé toky mezi zařízeními (nikoliv pro jednotlivé pakety, ale skupinu paketů v rámci jednoho toku)
- na rezervaci používá protokol [[RSVP]]
- poskytují společnou (vzájemně integrovanou) službu množině provozních požadavků
# Podporované třídy
- garantované služby - striktní omezení ve frontách podle [[Token bucket]]
- kontrolovaná zátěž  - provoz aby se zatížení chovalo, že jsem tam já sám (blížící se nezatíženému)
- největší úsilí - žádná rezervace

Dané zařízení když dostane požadavek odpoví, jestli to může splnit, potom si interně připraví fronty a mechanismy. Pokud není schopno zajistit (je zatížené) vrací negativní odpověď a žadatel musí poslat nižší nároky


> [!Info] V praxi je využití malé vzhledem k nutné kooperaci všech prvků na cestě

