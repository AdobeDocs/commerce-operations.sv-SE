---
title: 'ACSD-64113: Fel i administratör vid överföring av bild med mindre bredd än höjd via  [!DNL Media Gallery]'
description: Använd korrigeringsfilen ACSD-64113 för att åtgärda Adobe Commerce-problemet när fel uppstår i administratören när bilder med en relativt liten bredd överförs jämfört med höjden (eller tvärtom) via  [!DNL Media Gallery].
feature: Page Content, Media, Admin Workspace
role: Admin, Developer
exl-id: aba9d875-1d5d-49c2-8071-ba0ce679d7cd
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-64113: Fel i administratör vid överföring av bild med mindre bredd än höjd via [!DNL Media Gallery]

Korrigeringen ACSD-64113 åtgärdar ett problem där fel uppstår i administratören vid överföring av bilder med en relativt liten bredd jämfört med deras höjd (eller tvärtom) via [!DNL Media Gallery]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 har installerats. Korrigerings-ID är ACSD-64113. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Fel inträffar i administratören när bilder med en relativt liten bredd överförs jämfört med deras höjd (eller tvärtom) via [!DNL Media Gallery].

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Content]** > **[!UICONTROL Media]** > **[!UICONTROL Media Gallery]** och välj katalogen **[!UICONTROL wysiwyg]**.
1. Överför bilden med en relativt liten bredd jämfört med dess höjd (eller tvärtom).

<u>Förväntade resultat</u>:

Bilden överförs utan fel.

<u>Faktiska resultat</u>:

1. Följande felmeddelande visas:

   *Ett tekniskt problem med servern skapade ett fel. Försök igen för att fortsätta med det du gjorde. Försök igen senare om problemet kvarstår.*
1. `var/log/exception.log` innehåller:

   ```
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($width) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

   eller

   ```
   report.CRITICAL: ValueError: imagecreatetruecolor(): Argument #1 ($height) must be greater than 0 in /home/lib/internal/Magento/Framework/Image/Adapter/Gd2.php:427
   ```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
