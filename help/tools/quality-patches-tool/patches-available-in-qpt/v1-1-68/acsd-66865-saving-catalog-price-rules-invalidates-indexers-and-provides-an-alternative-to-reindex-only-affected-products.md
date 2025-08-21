---
title: 'ACSD-66865: Om du sparar en [!UICONTROL Catalog Price Rule] blir indexerare ogiltiga och det finns ett alternativ till att indexera om endast berörda produkter'
description: Använd korrigeringsfilen ACSD-66865 för att åtgärda Adobe Commerce-problemet där  när du sparar [!UICONTROL Catalog Price Rules] blir indexerare ogiltiga och ett alternativ till att indexera om bara berörda produkter.
feature: Price Rules, Price Indexer
role: Admin, Developer
type: Troubleshooting
source-git-commit: fe36522b99ec3fe7189d164cfca6127c9119e06e
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 0%

---


# ACSD-66865: Om du sparar en **[!UICONTROL Catalog Price Rule]** blir indexerare ogiltiga och det finns ett alternativ till att indexera om endast berörda produkter

Korrigeringen ACSD-66865 åtgärdar ett problem där ett **[!UICONTROL Catalog Price Rule]** gör indexerare ogiltiga och erbjuder ett alternativ till att indexera om endast berörda produkter. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 har installerats. Korrigerings-ID är ACSD-66865. Observera att detta problem har åtgärdats i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om du sparar en **[!UICONTROL Catalog Price Rule]** blir alla indexerare ogiltiga, vilket utlöser fullständiga omindexeringar i stället för att bara omindexera de produkter som påverkas.

<u>Steg som ska återskapas</u>:

1. Kontrollera att cron inte körs och att alla indexerare är inställda på att uppdateras enligt schemat (förutom `customer_grid` som kan uppdateras när programmet sparas).
2. Kör en fullständig manuell omindexering med kommandot: `php bin/magento indexer:reindex`.
3. Verifiera att alla index visar status *[!UICONTROL Ready]* med *0* objekt i eftersläpningen.
4. Gå till **[!UICONTROL Marketing]** > *[!UICONTROL Promotions]* > **[!UICONTROL Catalog Price Rule]** på sidlisten Admin. Skapa en aktiv katalogprisregel för en enskild produkt (till exempel med ett *SKU* -villkor).
5. Kör kommandot `php bin/magento indexer:status` för att kontrollera indexerarstatus.
6. Observera att flera index har markerats som **[!UICONTROL Reindex Required]** även om bara en produkt påverkas.

<u>Förväntade resultat</u>:

Endast den berörda produktinformationen identifieras och en partiell omindexering aktiveras i stället för en fullständig omindexering för alla indexerare.

<u>Faktiska resultat</u>:

En fullständig omindexering utlöses för alla indexerare, även när endast en produkt påverkas av **[!UICONTROL Catalog Price Rule]**.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
