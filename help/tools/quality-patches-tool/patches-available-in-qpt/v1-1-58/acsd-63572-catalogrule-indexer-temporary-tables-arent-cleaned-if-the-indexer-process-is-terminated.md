---
title: 'ACSD-63572: Tillfälliga register för indexering av katalog rensas inte om indexeringsprocessen avslutas'
description: Använd korrigeringsfilen ACSD-63572 för att åtgärda Adobe Commerce-problemet där indexerartabellerna inte rensas när processen avslutades på grund av en systemuppgradering eller ett stopp i [!UICONTROL CLI].
feature: System
Role: Admin, Developers
exl-id: 1cab7058-ca20-4d43-bfca-9b0e3ad35f42
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-63572: `catalogrule` temporära indexerartabeller rensas inte om indexerarprocessen avslutas

Korrigeringen ACSD-63572 åtgärdar ett problem där temporära indexerartabeller inte rensas när processen avslutades på grund av en system/uppgradering eller stopp i [!UICONTROL CLI]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 har installerats. Korrigerings-ID är ACSD-63572. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Tillfälliga register för indexerare rensas inte när processen avslutades på grund av en systemuppgradering eller stopp i [!UICONTROL CLI].

<u>Steg som ska återskapas</u>:

1. Öppna [!UICONTROL CLI].
1. Kör kommando: `bin/magento indexer:reindex catalogrule_rule`.
1. Avbryt processen innan den är klar med: `^C`.
1. Återställ indexerare med: `bin/magento indexer:reset catalogrule_rule catalogrule_product`.
1. Upprepa föregående steg flera gånger.
1. Kontrollera följande tillfälliga tabeller som har skapats i databasen:

   ```
   catalogrule_product__temp*
   catalogrule_product_price__temp*
   ```

<u>Förväntade resultat</u>:

De gamla temporära tabellerna tas bort när de inte behövs.

<u>Faktiska resultat</u>:

De gamla temporära tabellerna tas inte bort.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
