---
title: 'ACSD-56616: Visa paketerade produkter i lager vid en enkel brist på stockinnehåll'
description: Använd patchen ACSD-56616 för att åtgärda Adobe Commerce-problemet där paketerade produkter oväntat visas i butiken när alla tillhörande enkla produkter inte finns i lager.
feature: Products
role: Admin, Developer
exl-id: 8b225d9d-1898-4c4d-81be-7b92cbf7d06f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# ACSD-56616: Visa butiker för paketerade produkter vid en enkel lagerbrist.

Korrigeringen ACSD-56616 åtgärdar ett problem där paketerade produkter oväntat visas i butiken när alla tillhörande enkla produkter inte finns i lager. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45 har installerats. Korrigerings-ID är ACSD-56616. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Felaktig butiksvisning av paketerade produkter vid en enkel lagerbrist.

<u>Steg som ska återskapas</u>:

1. Skapa en ny webbplats/butik/butik.
1. Skapa en ny källa.
1. Skapa ett nytt arkiv och tilldela det till den nyligen skapade webbplatsen.
1. Konfigurera indexerare att uppdatera enligt schema.
1. Generera två enkla produkter, S1 (kvantitet = 1) och S2 (kvantitet = 1), och tilldela dem till den nya Stock-webbplatsen och den nya webbplatsen.
1. Skapa *paketerad1*-produkt och associera den med en ny webbplats, placera den i kategorin *CAT*.
1. Definiera två obligatoriska listrutealternativ och länka den enkla produkten *S1* till alternativ1 och *S2* till alternativ2.
1. Spara produkterna.
1. Navigera till **[!UICONTROL System]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Web]** och aktivera *Lägg till butikskod i URL* = *Ja*.
1. Öppna butiken och köp den paketerade produkten.
1. Kör cron två gånger.
1. Gå tillbaka till kategorin *CAT*.

<u>Förväntade resultat</u>:

Produkten *bundle1* finns inte i lager.

<u>Faktiska resultat</u>:

Produkten *bundle1* visas med priset = *$0*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
