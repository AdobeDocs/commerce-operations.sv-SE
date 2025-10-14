---
title: 'ACSD-58446: Om du tar bort ett team med underordnade användare eller team via GraphQL visas ett felmeddelande utan information'
description: Använd ACSD-58446-korrigeringen för att åtgärda Adobe Commerce-problemet där ett team med underordnade användare eller team via GraphQL returnerar ett felmeddelande som inte är informativt och som inte stämmer överens med användargränssnittet.
feature: GraphQL
role: Admin, Developer
exl-id: 943ab281-cc41-4b96-8a7c-fff8c074267c
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '439'
ht-degree: 0%

---

# ACSD-58446: Om du tar bort ett team med underordnade användare eller team via GraphQL visas ett felmeddelande utan information

Korrigeringen ACSD-58446 åtgärdar ett Adobe Commerce-problem där ett team med underordnade användare eller team via GraphQL returnerar ett felmeddelande som inte är informativt och som inte stämmer överens med användargränssnittet. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49 är installerad. Korrigerings-ID är ACSD-58446. Observera att problemet är planerat att åtgärdas i Adobe Commerce B2B 1.5.1

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p7

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om du tar bort ett team med underordnade användare eller team via GraphQL visas ett felmeddelande som inte är informativt och som inte stämmer överens med användargränssnittet.

## Förutsättningar:

Adobe Commerce B2B-moduler är installerade.

<u>Steg som ska återskapas</u>:

1. Aktivera funktionen *[!UICONTROL Company]*.
1. Skapa ett nytt företag.
1. Logga in på **[!UICONTROL Admin]** och aktivera företagskontot.
1. Kontrollera e-postadressen och ange ett lösenord för det nya företagskontot.
1. Skapa ett nytt team för företaget.
1. Logga in som företagsanvändare på Storefront och lägg till en ny användare för det skapade teamet.
1. Logga in på **[!UICONTROL Admin]**, inaktivera företagsanvändaren och ange *[!UICONTROL Customer Active]* = *Nej*
1. Se till att du tar bort det skapade teamet via GraphQL.

   ```
   mutation {
     deleteCompanyTeam(
       id: "MQ=="
     ) {
       success
     }
   }
   ```

<u>Förväntade resultat</u>:

Ett informativt felmeddelande som är konsekvent med användargränssnittet returneras.

<u>Faktiska resultat</u>:

Ett allmänt internt serverfelmeddelande som inte stämmer överens med användargränssnittet returneras.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
