---
title: 'ACSD-59967: JavaScript-fel förhindrar att  [!DNL Google Maps] återges korrekt'
description: Använd korrigeringsfilen ACSD-59967 för att åtgärda Adobe Commerce-problemet där JavaScript-felet förhindrar att  [!DNL Google Maps]  återges korrekt.
feature: Admin Workspace, Page Builder, CMS
role: Admin, Developer
exl-id: 2982857a-7adb-4163-be18-4d2caf0d645c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-59967: JavaScript-fel förhindrar att [!DNL Google Maps] återges korrekt

Korrigeringen ACSD-59967 åtgärdar ett problem där JavaScript-felet förhindrar att [!DNL Google Maps] återges korrekt. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.51 är installerad. Korrigerings-ID är ACSD-59967. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.4-p3

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

JavaScript-fel förhindrar att [!DNL Google Maps] återges korrekt.

<u>Steg som ska återskapas</u>:

1. Generera en giltig [!DNL Google Maps]-nyckel.
1. Konfigurera API-nyckeln [!DNL Google Maps] under **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Content Management]**.
1. Lägg till [!DNL Google API Key] i fältet **[!UICONTROL Google Maps API Key]** och spara konfigurationen.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]** > **[!UICONTROL Create New Page]**.
1. Lägg till ett **[!UICONTROL Row]**-element och ett **[!UICONTROL Maps]**-element.

<u>Förväntade resultat</u>:

Det finns inga JavaScript-fel i konsolen och kartan återges korrekt på *Storefront* och *Admin*.

<u>Faktiska resultat</u>:

JavaScript-fel visas i konsolen och kartan återges inte korrekt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
