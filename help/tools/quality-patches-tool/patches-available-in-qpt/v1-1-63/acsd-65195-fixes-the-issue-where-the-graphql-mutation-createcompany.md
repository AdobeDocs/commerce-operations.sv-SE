---
title: 'ACSD-65195: GraphQL "createCompany"-mutationen returnerar ett fel för ett land utan en obligatorisk region'
description: Använd patchen ACSD-65195 för att åtgärda Adobe Commerce-problemet där mutationen GraphQL"createCompany" genererar ett fel för länder som inte behöver en region.
feature: B2B, Companies, GraphQL
role: Admin, Developer
exl-id: b9eed00c-26f2-47fe-b1a0-6b020527f0c1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-65195: GraphQL `createCompany`-mutationen returnerar ett fel för ett land utan en nödvändig region

ACSD-65195-korrigeringen åtgärdar ett problem där [!UICONTROL GraphQL] `createCompany`-mutationen orsakar ett fel för länder som inte behöver en region. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.63 har installerats. Korrigerings-ID är ACSD-65195. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p9, 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!UICONTROL GraphQL] `createCompany`-mutationen returnerar ett fel när en region har angetts för ett land som inte behöver någon.

<u>Steg som ska återskapas</u>:

1. Aktivera **[!UICONTROL B2B Companies]**.
1. Skicka mutationen `createCompany` [!UICONTROL GraphQL] med ett angivet regionfält för ett land som inte behöver ett. Exempel: [!UICONTROL country_id]: *AE* och [!UICONTROL region]: *Dubai*.
1. Se GraphQL svar.

<u>Förväntade resultat</u>:

Företaget bör skapas utan att ett fel returneras när en region anges för ett land som inte behöver det.

<u>Faktiska resultat</u>:

Företaget skapas inte och följande fel returneras:
`Error: Invalid value of "Dubai" provided for the region field.`

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: Uppgraderingar och korrigeringar > Tillämpa korrigeringar i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
