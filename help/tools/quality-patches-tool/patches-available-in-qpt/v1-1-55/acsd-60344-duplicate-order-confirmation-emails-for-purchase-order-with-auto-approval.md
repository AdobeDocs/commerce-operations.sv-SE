---
title: 'ACSD-60344: Dubblerat orderbekräftelsemeddelande via e-post när [!UICONTROL Purchase Order] används med automatiskt godkännande'
description: Använd patchen ACSD-60344 för att åtgärda Adobe Commerce-problemet där e-postmeddelanden med dubblettorderbekräftelse skickas när du använder en [!UICONTROL Purchase Order] med automatiskt godkännande.
feature: Purchase Orders
role: Admin, Developer
exl-id: c4d415ee-b1ac-4094-9209-19b91f9a7666
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---

# ACSD-60344: Dubblerat orderbekräftelsemeddelande via e-post när *[!UICONTROL Purchase Order]* används med automatiskt godkännande

Korrigeringen ACSD-60344 åtgärdar ett problem där e-postmeddelanden med dubblettorderbekräftelse skickas när en *[!UICONTROL Purchase Order]* används med automatiskt godkännande. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 är installerad. Korrigerings-ID är ACSD-60344. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.6-p4

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Dubblerade orderbekräftelsemeddelanden skickas när en *[!UICONTROL Purchase Order]* används med automatiskt godkännande.

<u>Förutsättningar</u>

Aktivera B2B-moduler och *[!UICONTROL Purchase Order]*.

<u>Steg som ska återskapas</u>:

1. Skapa ett företagskonto och aktivera en *[!UICONTROL Purchase Order]* för det.
1. Skapa ett vanligt användarkonto och lägg till det i företagskontot som en företagsanvändare.
1. Gör en beställning med det här kontot.
1. Kör cron och kolla e-post.

<u>Förväntade resultat</u>:

Endast ett e-postmeddelande med orderbekräftelse tas emot per beställning.

<u>Faktiska resultat</u>:

Två e-postmeddelanden med orderbekräftelse har tagits emot.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
