---
title: 'ACSD-66149: IPN-hanteraren returnerar *500* för typer som inte stöds'
description: Använd patchen ACSD-66149 för att åtgärda Adobe Commerce-problemet där IPN-hanteraren inte ignorerar IPN-typer som inte stöds eller är okända, vilket gör att problemet inte loggas, avbryter processen och returnerar även 500-fel.
feature: Payments
role: Admin, Developer
type: Troubleshooting
exl-id: d4794e24-1b6b-4bb5-b54c-9a248fa5f3bd
source-git-commit: cf0f5992c7b2a51b270a4a1a81fd50305a92759c
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-66149: IPN-hanteraren returnerar *500* för typer som inte stöds

Korrigeringsfilen ACSD-66149 åtgärdar ett problem där IPN-hanteraren (Instant Payment Notification) returnerar ett 500-fel för IPN-typer som inte stöds eller är okända. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 har installerats. Korrigerings-ID är ACSD-66149. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Problemet är att IPN-hanteraren returnerar ett *500*-fel för IPN-typer som inte stöds eller är okända. Det inträffar när PayPal skickar IPN med fält som saknas.

<u>Steg som ska återskapas</u>:

1. Skapa en anpassad modul som emulerar alla typer av okända IPN-typer från PayPal.
1. Skapa minst en produkt.
1. Konfigurera PayPal Express med dina egna autentiseringsuppgifter.
1. Beställ hos Paypal Express.
1. Kör PayPal-emulatorn.

<u>Förväntade resultat</u>:

I programmets IPN-hanterare ignoreras felaktiga IPN-typer och *500*-fel genereras inte:

```Order 000000001: Status processing — HTTP 500```

<u>Faktiska resultat</u>:

Programmet genererar många *500*-fel under bearbetning av felaktiga IPN:er och bearbetar ibland inte vissa order om de förväntade fälten saknas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool]
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden för Commerce om molninfrastruktur

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken
