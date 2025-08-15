---
title: 'ACP2E-3838: [!DNL Page Builder] CORS-fel förhindrar att ändringar sparas i administrationspanelen i produktionsläge'
description: Använd korrigeringsfilen ACP2E-3838 för att åtgärda Adobe Commerce-problemet där  [!DNL Page Builder] CORS-fel förhindrar att ändringar sparas i administrationspanelen i produktionsläge.
feature: Page Builder, Page Content, Admin Workspace
role: Admin, Developer
exl-id: 0d590c0e-e21c-4553-a0a3-9332e22796f3
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---

# ACP2E-3838: [!DNL Page Builder] CORS-fel förhindrar att ändringar sparas i administrationspanelen i produktionsläge

Korrigeringen för ACP2E-3838 åtgärdar ett problem där [!DNL Page Builder] CORS-fel förhindrar att ändringar sparas i administrationspanelen i produktionsläge. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 har installerats. Korrigerings-ID är ACP2E-3838. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p9 - 2.4.4-p12, 2.4.5-p8 - 2.4.5-p11, 2.4.6-p6 - 2.4.6-p9, 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!DNL Page Builder] CORS-fel förhindrar att ändringar sparas i administrationspanelen i produktionsläge.

<u>Steg som ska återskapas</u>:

1. Logga in på adminpanelen.
1. Gå till **[!UICONTROL Content]** > **[!UICONTROL Pages]**.
1. Klicka på **[!UICONTROL Add New Page]** eller markera en befintlig CMS-sida och klicka på **[!UICONTROL Edit]**.
1. Klicka på **[!UICONTROL Edit with Page Builder]** om du vill lägga till ett nytt innehållsblock eller redigera ett befintligt block.
1. Gör ändringar i innehållet, till exempel lägga till text, bilder eller andra element.
1. Klicka på knappen **[!UICONTROL Save]**.

<u>Förväntade resultat</u>:

Sidinnehållet bör sparas utan fel.

<u>Faktiska resultat</u>:

1. [!DNL Page Builder]-ändringarna kan inte sparas.
1. Webbläsarkonsolen loggar CORS-relaterade fel.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
