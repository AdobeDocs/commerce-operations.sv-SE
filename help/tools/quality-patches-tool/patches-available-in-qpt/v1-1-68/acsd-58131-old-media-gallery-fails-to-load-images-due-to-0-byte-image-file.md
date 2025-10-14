---
title: 'ACSD-58131: Det gamla mediegalleriet kan inte läsa in bilder på grund av en bildfil på 0 byte'
description: Använd korrigeringen ACSD-58131 för att åtgärda Adobe Commerce-problemet där det gamla mediegalleriet inte kan återge bilder när det finns en bild på 0 byte i katalogen.
feature: Media
role: Admin, Developer
type: Troubleshooting
source-git-commit: b09749a1e56ab6a7b613135ca252fd69757669d0
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---


# ACSD-58131: Det gamla mediegalleriet kan inte läsa in bilder på grund av en bildfil på 0 byte

Korrigeringen ACSD-58131 åtgärdar ett problem där det gamla mediegalleriet inte kan återge bilder när det finns en bild på 0 byte i katalogen. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 har installerats. Korrigerings-ID är ACSD-58131. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.5.0.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När en bild på 0 byte placeras i mediegalleriet kan det gamla mediegalleriet inte återge några bilder. Det uppdaterade systemet hoppar nu över ogiltiga 0-byte-filer, visar giltiga bilder som förväntat och loggar en varning för varje ogiltig fil.

```
[2024-05-02T14:00:39.616459+00:00] report.WARNING: The image empty2.jpg is invalid and cannot be displayed in the gallery. [] []
```

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Advanced]** > **[!UICONTROL System]** > **[!UICONTROL Media Gallery]**.
1. Ange **[!UICONTROL Enable Old Media Gallery]** som *Ja*.
1. Placera några bilder i katalogen `pub/media/wysiwyg`.
1. Skapa en bild på 0 byte i samma katalog med `touch pub/media/wysiwyg/empty_image.png`.
1. Lägg till en bild från katalogen `wysiwyg` via Page Builder under valfritt innehåll (t.ex. ett CMS-block):
   1. Skapa ett nytt block. Gå till **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Blocks]** och klicka på **[!UICONTROL Add New Block]**.
   1. Redigera innehållsavsnittet med Page Builder.
   1. Under **[!UICONTROL Layout]** drar du en ny **[!UICONTROL Row]** till scenen.
   1. Expandera **[!UICONTROL Media]** och dra en **[!UICONTROL Image]** platshållare till raden.
   1. Klicka på **[!UICONTROL Select from Gallery]**.
   1. Markera katalogen `wysiwyg` om den inte är markerad som standard.

<u>Förväntade resultat</u>:

Mediegalleriet fungerar även om det finns en bild på 0 byte (eller någon annan fil).

<u>Faktiska resultat</u>:

Mediegalleriet kan inte läsa in några bilder från katalogen `wysiwyg` på grund av ett kritiskt fel som loggats in `var/log/system.log`:

```
[2024-03-22T05:00:55.100934+00:00] report.CRITICAL: Exception: Notice: getimagesizefromstring(): Error reading from ! in /app/project/vendor/magento/module-cms/Model/Wysiwyg/Images/Storage.php on line 426 in /app/project/vendor/magento/framework/App/ErrorHandler.php:62
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
