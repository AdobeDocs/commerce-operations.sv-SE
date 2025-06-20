---
title: 'ACSD-55004: Valideraren kraschar när en importfil som är större än värdet överförs'
description: Använd patchen ACSD-55004 för att åtgärda Adobe Commerce-problemet där en validerare kraschar när en importfil som är större än det värde som konfigurerats i "php.ini" överförs.
feature: Data Import/Export
role: Admin, Developer
exl-id: c889f645-a3ae-4330-8ca9-45f8b6616ac8
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-55004: Valideraren kraschar när en importfil som är större än värdet överförs

ACSD-55004-korrigeringen åtgärdar ett problem där en validerare kraschar när en importfil som är större än det värde som konfigurerats i `php.ini` överförs. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.40 har installerats. Korrigerings-ID är ACSD-55004. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Valideraren kraschar när en importfil som är större än det värde som konfigurerats i `php.ini` överförs.

<u>Steg som ska återskapas</u>:

Försök överföra en importfil som är större än vad som konfigurerats i `php.ini`.

<u>Förväntade resultat</u>:

Filstorleken valideras utan fel.

<u>Faktiska resultat</u>:

Valideraren kraschar.

`var/log/exception.log` innehåller:

```
[2023-10-06T21:36:30.470618+00:00] report.CRITICAL: Error: Class "Zend_Validate_File_Upload" not found in ../module-import-export/Model/Source/Upload.php:81
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
