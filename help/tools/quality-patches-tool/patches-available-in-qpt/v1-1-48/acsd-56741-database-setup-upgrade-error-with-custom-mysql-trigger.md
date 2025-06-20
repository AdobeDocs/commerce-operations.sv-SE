---
title: 'ACSD-56741: Felsöka databaskonfigurationsfel med anpassade MySQL-utlösare'
description: Använd patchen ACSD-56741 för att åtgärda Adobe Commerce-problemet där ett felmeddelande *Ett försök att få åtkomst till matrisförskjutning av värdet null* visas under "setup:upgrade" på grund av en anpassad MySQL-utlösare i databasen som inte är relaterad till indexering och [!DNL MView].
feature: Install
role: Admin, Developer
exl-id: 93a1c75f-8a45-49df-9fa4-6ba1234c822d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-56741: Felsöka databaskonfigurationsfel med anpassade MySQL-utlösare

Korrigeringen ACSD-56741 åtgärdar ett problem där ett felmeddelande *Ett försök att få åtkomst till matrisförskjutning för ett värde av typen null* visas under `setup:upgrade` på grund av en anpassad MySQL-utlösare i databasen som inte hör till indexering och [!DNL MView]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.48 har installerats. Korrigerings-ID är ACSD-56741. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.5.0

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett felmeddelande *Ett försök att få åtkomst till matrisförskjutning för värdet av typen null* visas under `setup:upgrade` på grund av en anpassad MySQL-utlösare i databasen som inte hör till indexering och [!DNL MView].

<u>Steg som ska återskapas</u>:

1. Kör `php bin/magento indexer:set-mode schedule`.

   ```
   DELIMITER //
   CREATE TRIGGER trg_catalog_category_entity_before_delete_umis BEFORE DELETE ON catalog_category_entity FOR EACH ROW
       -> BEGIN
       -> UPDATE ewave_navigation_menu_item_info as nit INNER JOIN ewave_navigation_menu_category_type as ncmi ON nit.id = ncmi.menu_item_id AND ncmi.category_id = OLD.entity_id SET nit.status = 0;
       -> END //
   ```

1. Kör `php bin/magento c:f`.
1. Kör `php bin/magento setup:upgrade`.

<u>Förväntade resultat</u>:

Installationsuppgraderingen avslutas utan fel.

<u>Faktiska resultat</u>:

Installationsuppgraderingen avslutas med ett felmeddelande:

*Varning! Försöker komma åt matrisförskjutning för värdet av typen null*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
