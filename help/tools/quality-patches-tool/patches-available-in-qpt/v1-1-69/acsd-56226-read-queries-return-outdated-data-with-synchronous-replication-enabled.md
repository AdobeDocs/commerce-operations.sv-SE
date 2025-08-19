---
title: 'ACSD-56226: READ-frågor returnerar inaktuella data med "synchronous_replication" aktiverat'
description: Använd patchen ACSD-56226 för att åtgärda Adobe Commerce-problemet där READ-frågor returnerar inaktuella data när flaggan "synchronous_replication" är aktiverad för slavanslutning i molnet.
feature: System
role: Admin, Developer
type: Troubleshooting
source-git-commit: a45cef14b7b37f1112d2ef82adf29b09d63b8e2b
workflow-type: tm+mt
source-wordcount: '336'
ht-degree: 0%

---


# ACSD-56226: READ-frågor returnerar inaktuella data med `synchronous_replication` aktiverat

Korrigeringen ACSD-56226 åtgärdar ett problem där READ-frågor returnerar inaktuella data när flaggan `synchronous_replication` aktiveras för slavanslutning i molnet. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 har installerats. Korrigerings-ID är ACSD-56226. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p11

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

READ-frågor returnerar inaktuella data när flaggan `synchronous_replication` är aktiverad. Detta gör att slavanslutningen inaktiveras, vilket leder till databasöverlagring.

<u>Steg som ska återskapas</u>:

1. Ange `MYSQL_USE_SLAVE_CONNECTION` som *true* i miljövariablerna i Adobe Commerce i molninfrastrukturen.
1. Lägg till följande konfiguration i `.magento.env.yaml` för att ange `synchronous_replication` till *false*:

   ```
   DATABASE_CONFIGURATION:
     _merge: true
     slave_connection:
       default:
         synchronous_replication: false
   ```

1. Distribuera om och utför klientåtgärder som inloggning, lägg till i kundvagnen eller gör en beställning.

<u>Förväntade resultat</u>:

Slavanslutningen är fortfarande aktiverad när `synchronous_replication` är inställd på *false*.

<u>Faktiska resultat</u>:

Slavanslutningen är inaktiverad när `synchronous_replication` är inställd på *false*, vilket orsakar databasöverlagring.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
