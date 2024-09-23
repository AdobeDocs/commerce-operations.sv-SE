---
title: "ACSD-46618: produktlistwidgeten visar felaktiga cachelagrade priser för inloggad kund"
description: Använd en patch för att åtgärda problemet med Adobe Commerce där produktlistwidgeten visar felaktiga cachelagrade priser för en inloggad kund.
feature: Cache, Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-46618: Widgeten Produktlista visar felaktiga cachelagrade priser för en inloggad kund

Korrigeringen ACSD-46618 löser problemet där produktlistwidgeten visar felaktiga cachelagrade priser för en inloggad kund. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.html) 1.1.21 har installerats. Korrigerings-ID är ACSD-46618. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**
* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**
* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Korrigeringen ACSD-46618 löser problemet där produktlistwidgeten visar felaktiga cachelagrade priser för en inloggad kund.

<u>Steg som ska återskapas</u>:

1. I Adobe Commerce Admin väljer du **[!UICONTROL Stores]**, sedan **[!UICONTROL Configuration]**, expanderar **[!UICONTROL Sales]** och väljer **[!UICONTROL Tax]**. Uppdatera skatteinställningarna för att visa priser inklusive och exklusive moms.
1. Ange **[!UICONTROL Enable Cross Border Trade]** = _Ja_.
1. Skapa en momsregel som bara gäller för USA.
1. Lägg till en widget på startsidan, inklusive mer än en produkt.
1. Skapa två kunder med en adress i USA och en adress som inte är i USA.
1. Logga in med den amerikanska kunden från butiken. Kontrollera att sidan är cachelagrad.
1. Observera priset som visas i startsideswidgeten.
1. Logga ut och logga in med en kund som inte är i USA.

<u>Förväntade resultat</u>:

Priset som visas i startsidans widget motsvarar kundens adress.

<u>Faktiska resultat</u>:

På startsidans widget visas priser med moms för kunder utanför USA.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
