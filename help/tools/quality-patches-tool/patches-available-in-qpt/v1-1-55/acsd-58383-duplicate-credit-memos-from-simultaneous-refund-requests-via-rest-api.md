---
title: 'ACSD-58383: Dubblerade kreditnotor från samtidiga återbetalningsbegäranden via  [!DNL REST API]'
description: Använd korrigeringsfilen ACSD-58383 för att korrigera Adobe Commerce-problemet där två identiska begäranden som körs samtidigt och som återbetalas via  [!DNL REST API]  skapar dubblettkreditnotor.
feature: REST, Payments, Returns
role: Admin, Developer
exl-id: 962970d5-22e7-4bdc-afa0-70e1fa21ecec
source-git-commit: 28390659fe180180c9b2c8d16239008a1f8a510b
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# ACSD-58383 Adobe Commerce-korrigering: Duplicera kreditnotor från samtidiga återbetalningsbegäranden via [!DNL REST API]

Korrigeringen ACSD-58383 åtgärdar problemet där utfärdande av en återbetalning via [!DNL REST API] med två identiska begäranden som utförs samtidigt resulterar i dubbla kreditnotor.

Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 är installerad. Korrigerings-ID är ACSD-58383. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3


>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Dubblettkreditnotor är resultatet av två återbetalningar som skapats samtidigt.

<u>Steg som ska återskapas</u>:

1. Konfigurera [!DNL Paypal Express] i Commerce [!UICONTROL Admin].
1. Ange betalningsåtgärden till *Försäljning*.
1. Konfigurera IPN [!DNL PayPal] (Instant Payment Notification) på webbplatsen [!DNL PayPal] Sandbox.
1. Utfärda återbetalning på webbplatsen [!DNL PayPal] Sandbox.
1. Emulera ett IPN-meddelande från [!DNL PayPal] med hjälp av utvecklarverktygen. IPN måste skapa en kreditnota.
1. Skapa en andra kreditnota med ett [!DNL API]-samtal.

<u>Förväntade resultat</u>:

Endast en kreditnota skapas för samma artikel.


<u>Faktiska resultat</u>:

Två kreditnotor skapas för samma artikel.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
