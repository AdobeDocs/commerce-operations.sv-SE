---
title: 'ACSD-61199: Fliken CMS page [!UICONTROL Hierarchy] visar inte rätt trädstruktur'
description: Använd korrigeringsfilen ACSD-61199 för att åtgärda Adobe Commerce-problemet där CMS sidas *[!UICONTROL Hierarchy]*-flik inte visar rätt trädstruktur när du redigerar en CMS-sida med en befintlig *[!UICONTROL Hierarchy]*.
feature: Page Content
role: Admin, Developer
exl-id: f541d001-9680-431a-9a62-816c2d10b6d5
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-61199: Fliken [!UICONTROL Hierarchy] på CMS-sidan visar inte rätt trädstruktur

Korrigeringen ACSD-61199 åtgärdar ett problem där CMS-sidans *[!UICONTROL Hierarchy]*-flik inte visar en korrekt trädstruktur när en CMS-sida redigeras med en befintlig *[!UICONTROL Hierarchy]*. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 har installerats. Korrigerings-ID är ACSD-61199. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Fliken *[!UICONTROL Hierarchy]* på CMS-sidan visar inte en korrekt trädstruktur när en CMS-sida med en befintlig *[!UICONTROL Hierarchy]* redigeras.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]**.
1. Skapa en ny **[!UICONTROL CMS page]**. Den läggs till i webbplatsens rot på *[!UICONTROL Hierarchy]*.
1. Spara sidan.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Hierarchy]**.
1. Lägg till eventuella andra befintliga sidor i *[!UICONTROL Hierarchy]*.
1. Spara *[!UICONTROL Hierarchy]*.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Pages]**.
1. Redigera någon av de befintliga sidorna och öppna *[!UICONTROL Hierarchy]*.

<u>Förväntade resultat</u>:

*[!UICONTROL Hierarchy]* läses in som förväntat.

<u>Faktiska resultat</u>:

*[!UICONTROL Hierarchy]* har inte lästs in på fliken.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

[[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
