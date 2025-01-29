---
title: 'ACSD-46703: Dra och släpp för produktanpassning fungerar inte'
description: Den här artikeln innehåller en lösning på problemet där dra och släpp för de anpassningsbara alternativen inte fungerar som förväntat.
feature: Products
role: Developer
exl-id: 38b9490a-c9d4-4f8e-b90f-69bf50a6b571
source-git-commit: a1c5898626fb8419af017a29a009a0a2c069326e
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 0%

---

# ACSD-46703: Dra och släpp för produktanpassning fungerar inte

Korrigeringen ACSD-46703 åtgärdar ett problem där de anpassningsbara alternativen (dra och släpp) inte fungerar som förväntat. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 är installerat. Korrigerings-ID är ACSD-46703. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5

>[!NOTE]
>
>Korrigeringen kan komma att gälla för andra versioner med nya [kvalitetskorrigeringsverktyg]. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användarna kan inte dra och släppa de anpassningsbara alternativen från en sida till en annan.

<u>Steg som ska återskapas</u>:

1. Skapa en enkel produkt.
1. Lägg till anpassningsbara alternativ till den enkla produkten och se till att du lägger till över 20 alternativ, vilket resulterar i sidnumrering.
1. Försök att flytta ett anpassningsbart alternativ (dra och släpp) inom samma sida.
1. Nu kan du försöka flytta ett anpassningsbart alternativ från sida två till sida ett.

<u>Förväntade resultat</u>:

* Du kan dra och släppa de anpassningsbara alternativen från en sida till en annan.
* Du kan sortera värdena med dra och släpp-funktionen, även för flera sidor.

<u>Faktiska resultat</u>:

Du kan inte flytta något värde till en annan sida med dra och släpp-funktionen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokalt för Adobe Commerce eller Magento Open Source: [Verktyg för kvalitetspatchar > Användning](/help/tools/quality-patches-tool/usage.md) i guiden för kvalitetspatchar.
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].

Mer information om andra korrigeringsfiler som är tillgängliga i QPT finns i [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i guiden för verktyget för kvalitetspatchar.
