---
title: 'ACSD-66889: Fel vid omindexering av lager i CLI'
description: Använd korrigeringsfilen ACSD-66889 för att åtgärda Adobe Commerce-problemet som utlöser ett fel när lagerindexeraren körs.
feature: Inventory
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9631e0864b2ad8fc09734aedd476e96852cd70fb
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---


# ACSD-66889: Fel vid omindexering av lager i CLI

Korrigeringen ACSD-66889 åtgärdar det fel som inträffar när lagerindexeraren körs. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 har installerats. Korrigerings-ID är ACSD-66889.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5-p13

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När lagerindexeraren körs genererar processen en varning om borttagning och kan inte slutföras på grund av inaktuell strängsyntax.

<u>Steg som ska återskapas</u>:

1. Kör omindexering av lager med CLI-kommandot:

   ```
   php bin/magento indexer:reindex inventory
   ```

<u>Förväntade resultat</u>:

CLI:n återskapar lagerindexeraren.

<u>Faktiska resultat</u>:

CLI genererar ett funktionalitetsfel som inte längre används och lagerindex behålls i tillståndet *Omindexering krävs*:

```
Deprecated Functionality: Using ${var} in strings is deprecated, use {$var} instead in /home/vendor/magento/module-elasticsearch-catalog-permissions/Model/Adapter/FieldMapper/Product/FieldProvider/FieldName/Resolver/CategoryPermission.php on line 24
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
