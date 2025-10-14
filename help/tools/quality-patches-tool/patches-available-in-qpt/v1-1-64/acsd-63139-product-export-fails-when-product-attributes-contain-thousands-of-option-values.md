---
title: 'ACSD-63139: Produktexport misslyckas när produktattribut innehåller tusentals alternativvärden'
description: Använd patchen ACSD-63139 för att åtgärda Adobe Commerce-problemet där produktexporten misslyckas när produktattributen innehåller tusentals alternativvärden.
feature: Data Import/Export
role: Admin, Developer
exl-id: 785907dc-aa3f-49e2-bd52-c3afe4393456
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63139: Produktexport misslyckas när produktattribut innehåller tusentals alternativvärden

Korrigeringen ACSD-63139 åtgärdar ett problem där produktexporten misslyckas när produktattributen innehåller tusentals alternativvärden. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 har installerats. Korrigerings-ID är ACSD-63139. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p10

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktexporten misslyckas när produktattributen innehåller tusentals alternativvärden.

<u>Steg som ska återskapas</u>:

1. Installera Adobe Commerce med B2B-modulen.
1. Importera en stor databassdump med:
   &#x200B;- ~7 000 produkter
   &#x200B;- ~450 produktattribut
   &#x200B;- Vissa attribut har fler än 100 alternativ
1. Kör följande kommando för att installera cron (om det inte redan är installerat):

   ```
   bin/magento cron:install
   ```

1. Konfigurera [!DNL RabbitMQ] genom att följa instruktionerna i [[!DNL RabbitMQ] Krav](https://experienceleague.adobe.com/sv/docs/commerce-operations/installation-guide/prerequisites/rabbitmq).
1. Öppna filen `php.ini`, ange minnesgränsen till 4G och starta om PHP-tjänsten.
1. Gå till **[!UICONTROL System]** > *[!UICONTROL Data Transfer]* > **[!UICONTROL Export]** på Admin-panelen.
1. I avsnittet *[!UICONTROL Export Settings]* ställer du in **[!UICONTROL Entity Type]** på *Produkter*, rullar längst ned och klickar på **[!UICONTROL Continue]**.
1. Kör följande kommando för att starta exportprocessorn:

   ```
   bin/magento queue:consumers:start exportProcessor --max-messages=1
   ```

<u>Förväntade resultat</u>:

Produktexporten bör slutföras.

<u>Faktiska resultat</u>:

Produktexportprocessen misslyckas och följande allvarliga fel returneras:

```
Fatal error: Allowed memory size of 4294967296 bytes exhausted (tried to allocate 12288 bytes) in /var/www/html/app/code/Magento/Catalog/Model/ResourceModel/Product/Collection.php on line 597
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
