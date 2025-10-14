---
title: 'ACSD-66441: Navigering i lager visar felaktiga attributalternativ i flerbutiksinställningar'
description: Använd patchen ACSD-66441 för att åtgärda Adobe Commerce-problemet där navigering i lager visar attribut från andra butiker felaktigt i en konfiguration för flera butiker.
feature: Catalog Management, Search
role: Admin, Developer
type: Troubleshooting
exl-id: d61c6b9e-bbcf-4285-b97b-b1fee67048e5
source-git-commit: 515e6d1f00c910455a2ffddf70c4a450184e7e81
workflow-type: tm+mt
source-wordcount: '388'
ht-degree: 0%

---

# ACSD-66441: Navigering i lager visar felaktiga attributalternativ i flerbutiksinställningar

Korrigeringen ACSD-66441 åtgärdar ett problem där navigering i lager visar attribut från andra butiker felaktigt i en konfiguration för flera butiker. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 har installerats. Korrigerings-ID är ACSD-66441. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.7-p6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Navigering i lager i butiken innehåller attributvärden från andra butiker, även när dessa produkter inte är tillgängliga i den aktuella butiksvyn.

<u>Steg som ska återskapas</u>:

1. Skapa en sekundär webbplats-, butiks- och butiksvy.
1. Skapa en konfigurerbar produkt med ett anpassat attribut (till exempel storlek).
1. Tilldela den konfigurerbara produkten till huvudwebbplatsen och en kategori.
1. Indexera om alla data.
1. Navigera till den tilldelade kategorin i butiken. Alla storleksalternativ visas korrekt i Navigering i lager.
1. Ta bort tilldelningen av två enkla produkter från huvudwebbplatsen och tilldela dem till den sekundära webbplatsen, eller ta bort dem från huvudwebbplatsen.
1. Indexera om alla data.
1. Gå tillbaka till kategorisidan för butiken och kontrollera navigeringen i lager.

<u>Förväntade resultat</u>:

Navigering i lager visar endast attributalternativ från produkter som är tilldelade den aktuella butiken eller webbplatsen.

<u>Faktiska resultat</u>:

Navigering i lager visar attributalternativ (storlekar) för produkter som har tilldelats andra butiker eller webbplatser.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
