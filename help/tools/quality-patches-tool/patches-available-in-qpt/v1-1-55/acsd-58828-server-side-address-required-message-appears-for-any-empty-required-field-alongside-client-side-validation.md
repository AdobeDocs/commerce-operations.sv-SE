---
title: 'ACSD-58828: Serversidesadressen *måste anges* för alla tomma obligatoriska fält, tillsammans med validering på klientsidan'
description: Använd patchen ACSD-58828 för att åtgärda Adobe Commerce-problemet där valideringsmeddelandet *address krävs* på serversidan visas om något obligatoriskt fält lämnas tomt, tillsammans med valideringsmeddelandet på klientsidan.
feature: Shipping/Delivery, Checkout
role: Admin, Developer
exl-id: 6c19773d-cb75-409f-bbd7-78d285a0252a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '358'
ht-degree: 0%

---

# ACSD-58828: Meddelandet *adress krävs* på serversidan visas för alla tomma obligatoriska fält, tillsammans med validering på klientsidan

ACSD-58828-korrigeringen åtgärdar ett problem där serversidans valideringsmeddelande *address krävs* om något obligatoriskt fält lämnas tomt, tillsammans med valideringsmeddelandet på klientsidan. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 är installerad. Korrigerings-ID är ACSD-58828. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**
* Adobe Commerce (alla distributionsmetoder) 2.4.6-p2

**Kompatibel med Adobe Commerce-versioner:**
* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Verifieringsmeddelandet *address krävs* på serversidan om ett obligatoriskt fält lämnas tomt, tillsammans med valideringsmeddelandet på klientsidan.

Steg som ska återskapas:

1. Logga in som kund.
1. Lägg en produkt i kundvagnen.
1. Gå till kassan.
1. Lämna leveransadressen som den är.
1. Markera **[!UICONTROL Flat rate]** och välj **[!UICONTROL Next]**.
1. Avmarkera **[!UICONTROL My billing and shipping address are the same]**.
1. Lägg till en ny adress i listrutan.
1. Lämna alla obligatoriska fält tomma och välj **[!UICONTROL Update]**.

Förväntade resultat:

Felmeddelandet beskriver saknad eller felaktig information som krävs för utcheckning.

Faktiska resultat:

Feladressen *krävs. Ange och försök igen.* visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
