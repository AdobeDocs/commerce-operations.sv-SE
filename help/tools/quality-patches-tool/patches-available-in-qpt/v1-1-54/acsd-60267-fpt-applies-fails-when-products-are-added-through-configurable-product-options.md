---
title: 'ACSD-60267: FPT gäller felaktigt när produkter läggs till via konfigurerbara produktalternativ'
description: Använd patchen ACSD-60267 för att åtgärda problemet med Adobe Commerce där den fasta produktskatten gäller korrekt när enkla produkter läggs till direkt i kundvagnen, men misslyckas när du väljer samma produkter med konfigurerbara produktalternativ.
feature: Taxes
role: Admin, Developer
source-git-commit: c18ff9dd75ec6002c6461fcd3abd98ac8b97a9f7
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-60267: FPT gäller felaktigt när produkter läggs till via konfigurerbara produktalternativ

Korrigeringen ACSD-60267 åtgärdar ett problem där den fasta produktskatten gäller korrekt när enkla produkter läggs till direkt i kundvagnen, men misslyckas när du väljer samma produkter med konfigurerbara produktalternativ. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.54 har installerats. Korrigerings-ID är ACSD-60267. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

FPT (Fixed Product Tax) fungerar korrekt när enkla produkter med FPT läggs till i kundvagnen, men FPT läggs inte till när produkter läggs till via ett konfigurerbart produktval.

<u>Steg som ska återskapas</u>:

1. Ange *[!UICONTROL Enable FPT]* till *Ja* genom att gå till *Admin* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Tax]** > **[!UICONTROL Fixed Product Taxes]**.
1. Skapa ett FPT-attribut och tilldela det till en *[!UICONTROL Attribute Set]*.
1. Öppna **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]**.
1. För *[!UICONTROL Default Label]* anger du en etikett som identifierar attributet.
1. Ange *[!UICONTROL Catalog Input for Store Owner]* till *[!UICONTROL Fixed Product Tax]*.
1. Skapa en ny skatt och zon och tilldela den till en ny *[!UICONTROL Tax Rule]*.
1. Skapa en konfigurerbar produkt med två enkla produkter.
1. Tilldela nu två olika FPT-värden till dessa enkla produkter.
1. Indexera om och kontrollera priserna i butiken.
1. Lägg produkterna i kundvagnen och kontrollera delsummorna.

<u>Förväntade resultat</u>:

* På sidan *[!UICONTROL Catalog]* visas priser inklusive FPT.
* Delsummor i kundvagnen inkluderar FPT.

<u>Faktiska resultat</u>:

* På sidan *[!UICONTROL Catalog]* visas inte priserna inklusive FPT-värdet.
* Delsummor och sammanfattning är ogiltiga.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.

