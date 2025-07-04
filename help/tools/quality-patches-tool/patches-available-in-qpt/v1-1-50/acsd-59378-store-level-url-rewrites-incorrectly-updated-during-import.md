---
title: 'ACSD-59378: Store-level [!DNL URL] återskriver felaktigt uppdaterade under import'
description: Använd korrigeringsfilen ACSD-59378 för att åtgärda Adobe Commerce-problemet där  [!DNL URL] återskrivningar på butiksnivå inte uppdateras korrekt under importen.
feature: Data Import/Export
role: Admin, Developer
exl-id: dc54d810-dcc6-42c6-a877-d00d3cf4f9a5
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-59378: Lagringsnivå [!DNL URL] skriver om felaktigt uppdaterat under import

ACSD-59378-korrigeringen åtgärdar ett problem där [!DNL URL]-omskrivningar på butiksnivå felaktigt uppdateras under importen. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 är installerad. Korrigerings-ID är ACSD-59378. Observera att detta problem har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.5-p5

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.5x (alla versioner av 2.4.5)

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!DNL URL]-omskrivningar på Store-nivå uppdateras felaktigt under importen.

<u>Steg som ska återskapas</u>:

1. Skapa en produkt med `url_key = key_default` i scopet **Alla butiksvyer**.
1. Ange `url_key = key_store` i omfattningen **Standardbutiksvy**.
1. Exportera produkten.
1. Importera en [!DNL CSV]-fil för den här produkten med följande data:
   * Kolumnen `store_view_code` är inställd på *empty* så att den gäller för omfattningen **All Store Views** .
   * `url_key` är inställd på standardnyckeln *`key_default`*.

<u>Förväntade resultat</u>:

[!DNL URL] omskrivningar genereras bara om för butiksvyer där det inte finns någon åsidosatt `url_key` (där standardvärdet `url_key` gäller).

<u>Faktiska resultat</u>:

`key_store` [!DNL URL] omskrivningar tas bort, men [!DNL URL] omskrivningen på nivån **Standardbutiksvy** för produkten är fortfarande inställd på *`key_store`*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
