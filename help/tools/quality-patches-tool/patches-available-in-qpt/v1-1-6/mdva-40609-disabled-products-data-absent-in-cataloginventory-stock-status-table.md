---
title: 'MDVA-40609: Inaktiverade produktdata saknas i registret catalog_stock_status'
description: Korrigeringen MDVA-40609 löser problemet där data om inaktiverade produkter inte visas i indextabellen "cataloglager_stock_status", vilket leder till att felaktiga produktkvantiteter visas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 är installerat. Korrigerings-ID är MDVA-40609. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.
feature: Catalog Management, Inventory, Orders, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '418'
ht-degree: 0%

---

# MDVA-40609: Inaktiverade produktdata saknas i registret catalog_stock_status

MDVA-40609-korrigeringen löser problemet där data om inaktiverade produkter inte visas i indextabellen `cataloginventory_stock_status`, vilket leder till att felaktiga produktkvantiteter visas. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.6 har installerats. Korrigerings-ID är MDVA-40609. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Inaktiverade produktdata visas inte i indextabellen `cataloginventory_stock_status` vilket leder till att felaktiga produktkvantiteter visas.

<u>Förutsättningar</u>:

Lagermodulen är installerad.

<u>Steg som ska återskapas</u>:

1. Konfigurera två webbplatser med butiker och butiksvyer.
1. Skapa ytterligare en källa och ett lager.
1. Lägg till en enkel produkt:
   * Ange Aktivera produkt till *Nej*.
   * Tilldela två källor med Source Item Status = Instock och Antal större än noll.
1. Spara produkten.
1. Kontrollera fliken **Produkt, säljbart antal**.

<u>Förväntade resultat</u>:

Båda lagren har angett värden som är större än noll.

<u>Faktiska resultat</u>:

En aktie har noll värde.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i avsnittet [Patchar i QPT](https://support.magento.com/hc/en-us/sections/360010506631-Patches-available-in-MQP-tool-).
