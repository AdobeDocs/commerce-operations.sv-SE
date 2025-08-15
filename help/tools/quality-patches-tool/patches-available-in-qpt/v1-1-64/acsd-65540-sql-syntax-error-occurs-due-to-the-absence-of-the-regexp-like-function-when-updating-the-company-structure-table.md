---
title: 'ACSD-65540: SQL-fel inträffar på grund av att funktionen REGEXP_LIKE saknas i uppdatering av company_structure'
description: Använd patchen ACSD-65540 för att åtgärda Adobe Commerce-problemet där SQL-fel inträffar på grund av att funktionen REGEXP_LIKE saknas i uppdateringen company_structure.
feature: B2B
role: Admin, Developer
type: Troubleshooting
exl-id: a3e60742-60d4-41e3-93c3-506cc5a1c4a3
source-git-commit: b1912bbc5aabd36067563326ee5c6bb84e14441d
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# ACSD-65540: SQL-fel inträffar på grund av att funktionen `REGEXP_LIKE` saknas i `company_structure`-uppdateringar

Korrigeringen ACSD-65540 åtgärdar ett problem där SQL-fel inträffar på grund av att funktionen `REGEXP_LIKE` saknas i `company_structure`-uppdateringar. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.64 har installerats. Korrigerings-ID är ACSD-65540.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce B2B (alla distributionsmetoder) 1.5.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce B2B (alla distributionsmetoder) 1.5.2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

SQL-syntaxfel inträffar på grund av att funktionen `REGEXP_LIKE` saknas i `company_structure`-uppdateringar.

<u>Steg som ska återskapas</u>:

1. Uppdatera [!DNL B2B] till version 1.5.2.
1. Kör följande kommando:

```
bin/magento setup:upgrade
```

<u>Förväntade resultat</u>:

Uppgraderingen har slutförts.

<u>Faktiska resultat</u>:

```
Unable to apply data patch Magento\Company\Setup\Patch\Data\SetCompanyForStructure for module Magento_Company. Original exception message: SQLSTATE[42000]: Syntax error or access violation: 1305 FUNCTION REGEXP_LIKE does not exist, query was: UPDATE `company_structure` SET `company_id` = ? WHERE (REGEXP_LIKE(path, '^331(/.+)?$'))
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
