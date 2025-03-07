---
title: 'ACSD-46815: statisk innehållsdistribution misslyckas med kompakt strategi'
description: Använd patchen ACSD-46815 för att åtgärda Adobe Commerce-problemet där statisk innehållsdistribution misslyckas när kompakt strategi används.
feature: Deploy, Page Content, SCD
role: Admin
exl-id: 66941a83-daf8-4bb2-a575-b615e1c5dc7c
source-git-commit: 94fba368c799f4584e27331e852c0f8abeeabbd6
workflow-type: tm+mt
source-wordcount: '309'
ht-degree: 0%

---

# ACSD-46815: statisk innehållsdistribution misslyckas när kompakt strategi används

Korrigeringen ACSD-46815 åtgärdar ett problem där distributionen av statiskt innehåll misslyckas när den kompakta strategin används. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://support.magento.com/hc/en-us/articles/360047139492) 1.1.20 har installerats. Korrigerings-ID är ACSD-46815. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Statisk innehållsdistribution misslyckas vid distribution med en kompakt strategi.

<u>Steg som ska återskapas</u>:

1. Distribuera statiskt innehåll med en kompakt strategi genom att köra följande kommando:

```bash
bin/magento setup:static-content:deploy -f -s compact
```

<u>Förväntade resultat</u>:

Distributionen av statiskt innehåll slutförs utan fel.

<u>Faktiska resultat</u>:

Statisk innehållsdistribution misslyckas med en kompakt strategi. Följande fel inträffar under distributionsprocessen: *Innehållet från /app/pub/static/adminhtml/Magento/base/default/./node_modules/@spectrum-css/vars/dist/spectrum-global.css går inte att läsa filen.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce i molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i vår utvecklardokumentation.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
