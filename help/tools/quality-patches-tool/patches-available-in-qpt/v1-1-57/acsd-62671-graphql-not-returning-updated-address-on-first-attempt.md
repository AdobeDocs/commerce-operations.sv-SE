---
title: 'ACSD-62671: [!DNL GraphQL] returnerar inte uppdaterad adress vid första försöket'
description: Använd patchen ACSD-62671 för att åtgärda Adobe Commerce-problemet där en  [!DNL GraphQL] begäran inte returnerar aktuell adressinformation vid det första försöket.
feature: GraphQL
role: Admin, Developer
exl-id: afd75ad2-e801-4f8a-b68f-526ca5168413
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# ACSD-62671: [!DNL GraphQL] returnerar inte uppdaterad adress vid första försöket

Korrigeringen ACSD-62671 åtgärdar ett problem där en [!DNL GraphQL]-begäran inte returnerar aktuell adressinformation vid det första försöket. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html?lang=sv-SE) 1.1.57 är installerad. Korrigerings-ID är ACSD-62671. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du använder [!DNL GraphQL Application Server] returnerar kundadressbegäran inte de senaste data.

<u>Steg som ska återskapas</u>:

1. Installera och starta [!DNL GraphQL Application Server].
1. Kontrollera att cachetypen `graphQL_query_resolver_result` är aktiverad.
1. Använd [!DNL GraphQL] för att:

   * Skapa en kund.
   * Generera en token.
   * Använd token för att skapa flera adresser för ovanstående kund.

1. Skicka [!DNL GraphQL]-begäran för att hämta kundens adresser.
1. Lägg till en ny adress till kunden.
1. Upprepa begäran från steg 4 flera gånger samtidigt som det returnerade adressantalet i svaret övervakas.

<u>Förväntade resultat</u>:

[!DNL GraphQL]-svaret innehåller rätt antal kundadresser.

<u>Faktiska resultat</u>:

Ibland returneras fel antal adresser i svaret på [!DNL GraphQL].

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
