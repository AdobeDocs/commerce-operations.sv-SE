---
title: 'ACSD-61134: Betalningsmetoden [!UICONTROL Braintree Vault] avmarkeras automatiskt i arbetsflödet för utcheckning'
description: Använd korrigeringsfilen ACSD-61134 för att lösa Adobe Commerce-problemet där betalningsmetoden *[!UICONTROL Braintree Vault]* automatiskt avmarkeras i kassaarbetsflödet när en kund uppdaterar sin faktureringsadress genom att avmarkera kryssrutan *[!UICONTROL My billing and shipping address are the same]*.
feature: Checkout
role: Admin, Developer
exl-id: 8aad34e2-89ef-460c-8921-91098bd1645b
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '327'
ht-degree: 0%

---

# ACSD-61134: Betalningsmetoden *[!UICONTROL Braintree Vault]* avmarkeras automatiskt i arbetsflödet för utcheckning

Korrigeringen ACSD-61134 åtgärdar ett problem där betalningsmetoden *[!UICONTROL Braintree Vault]* automatiskt avmarkeras i arbetsflödet för utcheckning när en kund uppdaterar sin faktureringsadress genom att avmarkera kryssrutan *[!UICONTROL My billing and shipping address are the same]*. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.54 har installerats. Korrigerings-ID är ACSD-61134. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7-beta1.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.6-p7

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Betalningsmetoden *[!UICONTROL Braintree Vault]* avmarkeras automatiskt i arbetsflödet för utcheckning.

<u>Steg som ska återskapas</u>:

1. Konfigurera betalningsmetoden *[!DNL Braintree]* med *[!UICONTROL Vault]* aktiverat.
1. Checka ut och spara ett kort i *[!UICONTROL Vault]*.
1. Gå till en annan produkt.
1. Lägg till en ny leveransadress på sidan *[!UICONTROL Shipping]* så att du har två adresser att välja mellan.
1. Välj betalningsmetod på sidan *[!UICONTROL Payment]* och klicka på **[!UICONTROL My billing and shipping addresses are the same]**.

<u>Förväntade resultat</u>:

Den valda betalningsmetoden förblir markerad.

<u>Faktiska resultat</u>:

Den valda betalningsmetoden är avmarkerad.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
