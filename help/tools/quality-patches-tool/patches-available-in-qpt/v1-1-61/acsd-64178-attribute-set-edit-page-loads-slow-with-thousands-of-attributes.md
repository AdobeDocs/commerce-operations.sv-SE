---
title: 'ACSD-64178: Sidan [!UICONTROL Edit Attribute Set] läses in långsamt med tusentals produktattribut'
description: Använd korrigeringsfilen ACSD-64178 för att åtgärda Adobe Commerce-problemet där sidan [!UICONTROL Edit Attribute Set] läses in långsamt om det finns tusentals produktattribut.
feature: Catalog Management
role: Admin, Developer
source-git-commit: 42585380737774a78800876e262e43a806e93b77
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# ACSD-64178: Sidan [!UICONTROL Edit Attribute Set] läses in långsamt med tusentals produktattribut

Korrigeringen ACSD-64178 åtgärdar ett problem där sidan **[!UICONTROL Edit Attribute Set]** läses in långsamt om det finns tusentals produktattribut. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 har installerats. Korrigerings-ID är ACSD-64178. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Sidan **[!UICONTROL Edit Attribute Set]** läses in långsamt om det finns tusentals produktattribut.

<u>Steg som ska återskapas</u>:

1. Skapa minst 4 200 attribut som inte har tilldelats någon av attributuppsättningarna.
1. Gå till **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Attribute Set]** på sidlisten Admin. Klicka på en attributuppsättning som du vill redigera.

<u>Förväntade resultat</u>:

Sidan läses in inom rimlig tid.

<u>Faktiska resultat</u>:

Det tar flera minuter att läsa in sidan.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
