---
title: "ACSD-60538: Attribut visas inte korrekt om produkten är inaktiverad i [!UICONTROL All Store Views]"
description: Använd patchen ACSD-60538 för att åtgärda Adobe Commerce-problemet där produktattributen inte visas korrekt i GraphQL-svaret om en produkt inaktiveras i *Alla butiksvyer* och endast aktiveras i specifika butiksvyområden, vilket gör att produkten inte visas korrekt.
feature: Attributes, GraphQL
role: Admin, Developer
source-git-commit: c394e003797d8095c17a0f6047024231e26a8321
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# ACSD-60538: Attribut visas inte korrekt om produkten är inaktiverad i *[!UICONTROL All Store Views]*

Korrigeringen ACSD-60538 åtgärdar ett problem där produktattributen inte visas korrekt i GraphQL-svaret om en produkt är inaktiverad i *[!UICONTROL All Store Views]* och endast aktiveras i specifika butiksvyområden, vilket gör att produkten inte visas korrekt. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51 är installerad. Korrigerings-ID är ACSD-60538. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.7-p1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om en produkt är inaktiverad i *[!UICONTROL All Store Views]* och endast är aktiverad i specifika butiksvyområden visas inte produktattributen korrekt i GraphQL-svaret, vilket leder till att produkten inte visas korrekt.

<u>Förutsättningar</u>:

Lagermodulen är installerad.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt med attributet *color* och tre underordnade produkter (*blue*, *black* och *brown*).
1. Inaktivera två associerade underordnade produkter (*blue* och *black*) i omfattningen *[!UICONTROL All Store Views]*.
1. Gå till scopet **[!UICONTROL Store View]**.
1. Aktivera underordnade produkter (*blue* och *black*) i omfattningen *[!UICONTROL Store View]*.
1. Kör nedanstående GraphQL-förfrågan:

   ```GraphQL
   {
     products(filter: { sku: { eq: "SKU" } }) {
       items {
           ... on ConfigurableProduct {
             configurable_options {
               attribute_id,
               attribute_code,
            values {
             value_index
             label
           }
       }
       variants {
         product {
           sku
         }
         attributes {
           label
           code
           value_index
          }
         }
        }
       }
      }
     }  
   ```

<u>Förväntade resultat</u>:

GraphQL-svar innehåller attributvärden för den underordnade associerade produkten som är inaktiverade på *[!UICONTROL All Store Views]* och aktiverade på omfånget *[!UICONTROL Store View]*.

<u>Faktiska resultat</u>:

GraphQL-svar har tomma attributvärden för den underordnade associerade produkten när produkten är inaktiverad på *[!UICONTROL All Store Views]* och aktiverad i *[!UICONTROL Store View]*-omfånget.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.