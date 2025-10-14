---
title: 'ACSD-47937: Meddelanden om prisfall skickas inte på grund av cachelagring på programnivå'
description: Använd patchen ACSD-47937 för att åtgärda Adobe Commerce-problemet där meddelanden om prisfall inte alltid skickas på grund av cachelagring på applikationsnivå.
feature: Admin Workspace, Cache, Orders
role: Admin
exl-id: 91d8e677-c2bb-4230-bbe3-a2c5f9b82e16
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '413'
ht-degree: 0%

---

# ACSD-47937: Meddelanden om prisfall skickas inte på grund av cachelagring på programnivå

Korrigeringen ACSD-47937 åtgärdar ett problem där meddelanden om prisfall inte alltid skickas på grund av cachelagring på applikationsnivå. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.26 har installerats. Korrigerings-ID är ACSD-47937. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 och 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4, 2.4.5 och 2.4.5-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kunderna får inte e-post om att produktpriserna sjunker för efterföljande produktprisändringar.

<u>Steg som ska återskapas</u>:

1. Aktivera **[!UICONTROL Product Alert]** för både *[!UICONTROL Price Changes]* och *[!UICONTROL Back in Stock]* i **[!UICONTROL Store]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product Alert]**.
1. Aktivera **[!UICONTROL Display Out of Stock Products]**.
1. Skapa en enkel produkt (ABC) med kvantitet = 0.
1. Skapa en kund i butiken och prenumerera på produkten ovan för att få produktmeddelanden om prisfall.
1. Starta produktvarningen för kunder.

   ```PHP
   bin/magento queue:consumers:start product_alert
   ```

1. Sänk priset för ABC-produkten.
1. Utlös produktvarningen cron.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

1. Sänk priset på ABC-produkten igen.
1. Utlös produktvarningen cron.

   ```PHP
   php n98-magerun2.phar sys:cron:run catalog_product_alert
   ```

>[!NOTE]
>
>Om du inte är bekant med verktyget [!DNL n98] kan du köra `bin/magento cron:run command` som vanligt och övervaka tabellen `cron_schedule` för att se till att `catalog_product_alert`-jobbet får status som lyckat.

<u>Förväntade resultat</u>:

Den andra prissänkningen skickas.

<u>Faktiska resultat</u>:

Den andra prissänkningen skickas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool]
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i guiden för Commerce om molninfrastruktur

## Relaterad läsning

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool]
* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
