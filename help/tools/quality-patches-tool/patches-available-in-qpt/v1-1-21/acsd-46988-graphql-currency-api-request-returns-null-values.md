---
title: 'ACSD-46988: API-begäran för GraphQL-valuta returnerar null-värden'
description: Korrigeringen för ACSD-46988 åtgärdar ett problem där API-begäran för GraphQL-valuta returnerar null-värden för en anpassad valuta. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21 är installerat. Korrigerings-ID är ACSD-46988. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
feature: REST, GraphQL
role: Admin
exl-id: 276d2c75-6e7f-4888-b4d2-ac96bea93fc1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '410'
ht-degree: 0%

---

# ACSD-46988: API-begäran för GraphQL-valuta returnerar null-värden

Korrigeringen för ACSD-46988 åtgärdar ett problem där API-begäran för GraphQL-valuta returnerar null-värden för en anpassad valuta. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.21 har installerats. Korrigerings-ID är ACSD-46988. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

API-begäran för GraphQL-valuta returnerar null-värden för en anpassad valuta.

<u>Steg som ska återskapas</u>:

1. Konfigurera anpassad valuta i administratören. Gå till **System** > **Konfiguration** > **Allmänt** > **Valutainställning**.
1. Skicka en GraphQL-begäran med följande nyttolast:

<pre>
<code class="language-graphql">
&lbrace;
    currency &lbrace;
        base_currency_code
        base_currency_symbol
        default_display_currency_code
        default_display_currency_symbol
        available_currency_codes
        exchange_rates &lbrace;
            currency_to
            rate
        &rbrace;
    &rbrace;
&rbrace;
</code>
</pre>

<u>Förväntade resultat</u>:

Begäran returnerar valutavärden i stället för null-värden.

<u>Faktiska resultat</u>:

Begäran returnerar flera null-värden.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal plats för Adobe Commerce eller Magento Open Source: [Verktyg för kvalitetskorrigeringar > Användning](/help/tools/quality-patches-tool/usage.md) i guiden för kvalitetskorrigeringsverktyget.
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Ytterligare steg krävs efter installationen av korrigeringsfilen

För lokala användare:

* Kör: `composer require symfony/intl:"~5.4.11"`

För molnanvändare:

* Kör: `composer require symfony/intl:"~5.4.11"`
* Skicka `composer.json`- och `composer.lock`-filer till Git-databasen tillsammans med korrigeringsfilen.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra korrigeringsfiler som är tillgängliga i QPT finns i [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i guiden för verktyget för kvalitetspatchar.
