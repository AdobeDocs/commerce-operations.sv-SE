---
title: 'ACSD-62355: Förbättrar prestanda för konfigurerbar redigering i Adobe Commerce'
description: Använd patchen ACSD-62355 för att åtgärda Adobe Commerce-problemet där sidan för redigering av konfigurerbara produkter laddas långsamt när produkten baseras på många attribut med många värden.
feature: Admin Workspace
role: Admin, Developer
source-git-commit: e8694744c8a2411a8e966148860f43fb56b48772
workflow-type: tm+mt
source-wordcount: '543'
ht-degree: 0%

---

# ACSD-62355: Förbättrar prestanda för konfigurerbar redigering i Adobe Commerce

Korrigeringen ACSD-62355 åtgärdar problemet med långsam laddningstid och hög minnesförbrukning på den konfigurerbara produktredigeringssidan när produkten har många attribut med många värden. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.56 har installerats. Korrigerings-ID är ACSD-62355. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det tar lång tid att läsa in den konfigurerbara produktredigeringssidan när den konfigurerbara produkten är baserad på flera attribut med många värden, vilket orsakar fördröjningar och potentiella timeout- eller minnesbegränsningsproblem.

<u>Steg som ska återskapas</u>:

1. Skapa 9 nya attribut i standardattributuppsättningen. Varje attribut är [!UICONTROL Filterable] och har [!UICONTROL Scope]: [!UICONTROL Global].
   * Attribut 1: 50 alternativ
   * Attribut 2: 20 alternativ
   * Attribut 3: 10 alternativ
   * Attribut 4: 5 alternativ
   * Attribut 5: 5 alternativ
   * Attribut 6: 5 alternativ
   * Attribut 7: 5 alternativ
   * Attribut 8: 3 alternativ
   * Attribut 9: 2 alternativ

1. Skapa 9 enkla produkter med kombinationer av alternativ från de nya attributen.
   * Produkt 1: Första alternativet från varje attribut
   * Produkt 2: Andra alternativet från varje attribut
   * Produkt 3: Tredje alternativet från varje attribut
   * Produkt 4: Fjärde alternativet från varje attribut
   * Om ett attribut har färre alternativ än antalet produkter tilldelar du de återstående produkterna till slumpmässiga alternativ i det attributet.

1. Skapa en konfigurerbar produkt som använder de nya attributen:
   * Lägg till en underordnad produkt med följande konfiguration:
      * Använd det sista alternativet från Attribut 1 och det första alternativet från Attribut 2 till 9.
      * Detta ger 1 konfigurerbar produkt och 1 underordnad produkt.
1. Gå till fliken **[!UICONTROL Configurations]** för den konfigurerbara produkten.
1. Klicka på **[!UICONTROL Add Products]** manuellt och börja lägga till de tidigare skapade enkla produkterna en i taget.
1. Spara ändringarna efter varje tillägg.
1. När du lägger till produkter bör du tänka på inläsningstiden för den redigerbara produktsidan.
1. När du har lagt till 7 produkter bör du märka en avsevärd ökning av RAM-förbrukningen och sidinläsningstiden

<u>Förväntade resultat</u>:

Produktredigeringsblanketten ska läsas in snabbt och effektivt utan alltför stor minnesförbrukning.

<u>Faktiska resultat</u>:

Det tar lång tid att läsa in den konfigurerbara produkten och det kan leda till minnesbegränsningar eller timeoutfel.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
