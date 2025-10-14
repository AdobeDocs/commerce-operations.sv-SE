---
title: 'ACSD-63974: Korrigerar långsam [!UICONTROL Requisition List] inläsningstid med sidnumrering'
description: Använd ACSD-63974-korrigeringen för att åtgärda problemet där sidan [!UICONTROL Requisition List] tar lång tid att läsa in när det finns för många objekt.
feature: B2B
role: Admin, Developer
exl-id: 1798baa3-da2f-44eb-8312-1f1b3f75b24d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-63974: Korrigerar långsam [!UICONTROL Requisition List] inläsningstid med sidnumrering

Korrigeringen ACSD-63974 åtgärdar ett problem där sidan **[!UICONTROL Requisition List]** tar lång tid att läsa in när det finns för många objekt. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 har installerats. Korrigerings-ID är ACSD-63974. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det tar lång tid att läsa in sidan **[!UICONTROL Requisition List]** när det finns många objekt (2 000+). Detta beror på att sidnumrering saknas, vilket gör att alla objekt läses in samtidigt.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > *[!UICONTROL General]* > **[!UICONTROL B2B features]**.
1. Ange **[!UICONTROL Enable Requisition List]** som *Ja*.
1. Generera 2000+ produkter genom att redigera noden `simple_products` i `setup/performance-toolkit/profiles/ce/small.xml`.
1. Kör kommandot:

   ```bash
   bin/magento setup:perf:generate-fixtures ./setup/performance-toolkit/profiles/ce/small.xml
   ```

1. Skapa en kund och logga in.
1. Lägg till alla produkter i **[!UICONTROL Requisition List]**.
1. Visa **[!UICONTROL Requisition List]** på Storefront.


<u>Förväntade resultat</u>:

Sidan ska läsas in inom rimlig tid.


<u>Faktiska resultat</u>:

Inläsningstiden för sidan ökar med antalet objekt eftersom alla objekt läses in samtidigt på grund av att sidnumreringen saknas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: Uppgraderingar och korrigeringar > Tillämpa korrigeringar i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
