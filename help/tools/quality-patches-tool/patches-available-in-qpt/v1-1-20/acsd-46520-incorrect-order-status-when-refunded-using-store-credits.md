---
title: 'ACSD-46520: Felaktig orderstatus vid återbetalning med butikskrediter'
description: I den här artikeln finns en lösning på problemet där användarna får en felaktig orderstatus när de återbetalas med butikskrediter.
feature: Orders, Returns
role: Admin
exl-id: 67740003-a71e-41bf-afda-ca3e32290115
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# ACSD-46520: Felaktig orderstatus vid återbetalning med butikskrediter

ACSD-46520-korrigeringen löser problemet där användarna får en felaktig orderstatus när de återbetalas med butikskrediter. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.20 har installerats. Korrigerings-ID är ACSD-46520. Observera att problemet har åtgärdats i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 och 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användarna får en felaktig orderstatus när de återbetalas med butikskrediter.

<u>Steg som ska återskapas</u>:

1. Skapa ett kundkonto i butiken och logga in.
1. Tilldela butikskrediter till kunden från administratören. Butikskrediterna ska omfatta hela ordern.
1. Gör en beställning med hjälp av butikskrediterna.
1. Fakturera ordern.
1. Skapa en kreditnota för att återbetala hela orderbeloppet.
Markera kryssrutan **[!UICONTROL Refund to store credit]**.
1. Kontrollera orderstatus.

<u>Förväntade resultat</u>:

Orderstatusen är *Stängd*.

<u>Faktiska resultat</u>:

Orderstatusen är *Fullständig*, vilket inte har rätt status.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Adobe Commerce eller [!DNL Magento Open Source] lokalt: [Verktyg för kvalitetspatchar > Användning](/help/tools/quality-patches-tool/usage.md) i guiden för kvalitetspatchar.
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
