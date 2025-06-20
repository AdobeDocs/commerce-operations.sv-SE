---
title: 'ACSD-61103: Felantalet återställs inte till noll efter lyckad kundinloggning via API'
description: Använd patchen ACSD-61103 för att åtgärda Adobe Commerce-problemet där antalet fel i tabellen"customer_entity" inte återställs till noll efter att en kund loggat in via API-slutpunkter.
feature: GraphQL, REST, Customers
role: Admin, Developer
exl-id: 9f5aac1f-c8a3-4255-8ebc-2268283b3384
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACSD-61103: Felantalet återställs inte till noll efter lyckad kundinloggning via API

Korrigeringen ACSD-61103 löser problemet där antalet fel i tabellen `customer_entity` inte återställs till noll när en kund har loggat in via API-slutpunkter. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 har installerats. Korrigerings-ID är ACSD-61103. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Antalet fel i tabellen `customer_entity` återställs inte till noll även efter att en kund har loggat in via API-slutpunkter.

<u>Steg som ska återskapas</u>:

1. Skapa ett kundkonto.
1. Generera en kundtoken via API, med felaktig information.
1. Kontrollera kolumnen `failures_num` i DB-tabellen `customer_entity` för kunden ovan.
1. Generera en kundtoken via API, med rätt information.
1. Kontrollera kolumnen `failures_num` i DB-tabellen `customer_entity` för kunden ovan.

<u>Förväntade resultat</u>:

Kolumnen `failures_num` bör återställas till 0 efter att du har använt rätt autentiseringsuppgifter för att generera en kundtoken via API.

<u>Faktiska resultat</u>:

Kolumnen `failures_num` återställs inte till 0 efter att du har använt rätt autentiseringsuppgifter för att generera en kundtoken via API.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
