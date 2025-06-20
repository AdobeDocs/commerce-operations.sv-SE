---
title: 'ACSD-61622: [!DNL FedEx] kontospecifika frekvenser saknas i REST API-svar'
description: Använd korrigeringsfilen ACSD-61622 för att åtgärda Adobe Commerce-problemet där  [!DNL FedEx] kontospecifika frekvenser saknas i REST API-svaret.
feature: Shipping/Delivery
role: Admin, Developer
exl-id: 59e33dc4-3f9b-4590-95b6-e98c77e750ee
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '381'
ht-degree: 0%

---

# ACSD-61622: [!DNL FedEx] kontospecifika frekvenser saknas i REST API-svar

Korrigeringen ACSD-61622 löser problemet där kontospecifika värden för [!DNL FedEx's] saknas i REST API-svaret. Den lägger till typen för `ACCOUNT`-tariffbegäran i REST API-begäran som skickas från Adobe Commerce till [!DNL FedEx], som returnerar ett svar som liknar SOAP API-svaret. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 är installerad. Korrigerings-ID är ACSD-61622. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p1 - 2.4.6-p8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!DNL FedEx's] kontospecifika frekvenser saknas i REST API-svaret.

<u>Steg som ska återskapas</u>:

1. Installera en ren Adobe Commerce-instans.
1. Skapa en enkel produkt med en vikt på 5 lbs.
1. Konfigurera [!DNL FedEx] för REST API.
1. Aktivera leveransmetoden [!DNL FedEx] och rensa cachen.
1. Börja observera loggfilen: `var/log/shipping.log`
1. Lägg en enkel produkt i kundvagnen och gå till fraktsidan vid kassan. Exempel på kunddata:

   * Postnummer: 58601
   * Namn: John Doe
   * Adress: 196 Eulalia Burg
   * Land: USA
   * Delstat: North Dakota
   * Telefonnummer: 187-563-3627

<u>Förväntade resultat</u>:

`PAYOR_ACCOUNT_PACKAGE`-frekvenser är tillgängliga i REST API-svaret, ungefär som SOAP API-svar.

<u>Faktiska resultat</u>:

Endast `PAYOR_LIST_PACKAGE` priser är tillgängliga i svaret, vilket betyder att det inte finns några förhandlade (konto) priser från [!DNL FedEx].

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
