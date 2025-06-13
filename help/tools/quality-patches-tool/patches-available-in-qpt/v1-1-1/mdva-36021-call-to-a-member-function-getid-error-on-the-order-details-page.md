---
title: 'MDVA-36021: Användarna får felmeddelanden när de öppnar orderinformationen'
description: Korrigeringen MDVA-36021 löser problemet där användare får *Anrop till medlemsfunktionen getId()* när de försöker öppna orderinformation. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1 är installerat. Korrigerings-ID är MDVA-36021. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.
feature: Orders
role: Admin
exl-id: 737479fe-f363-4974-9c58-7ed9cd113fdb
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# MDVA-36021: Användarna får felmeddelanden när de öppnar orderinformationen

Korrigeringen MDVA-36021 löser problemet där användare får felmeddelandet getId()*för* anropet till en medlemsfunktion när de försöker öppna orderinformationen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.1 har installerats. Korrigerings-ID är MDVA-36021. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.4.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce om molninfrastruktur 2.4.1, 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.2-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När användare försöker öppna orderinformation visas följande felmeddelande på sidan med orderinformation i Admin: *report.CRITICAL: Error: Call to an member function getId() on array in /magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml:62*.

<u>Förutsättningar</u>:

Systemet bör ha skatteinställningar och beställningar med specifika skattesatser.

<u>Steg som ska återskapas</u>:

1. Logga in på Commerce Admin.
1. Gå till **Försäljning** > **Beställningar** > **Öppna order**.

<u>Förväntade resultat</u>:

Ordern öppnas utan fel.

<u>Faktiska resultat</u>:

Du får ett felmeddelande som liknar följande: *report.CRITICAL: Error: Call to an member function getId() on array in /magento2ce/app/code/Magento/Sales/view/adminhtml/templates/order/totals/tax.phtml:62*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
