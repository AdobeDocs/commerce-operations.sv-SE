---
title: 'ACSD-60788: Anpassade skript för  [!DNL Google Tag Manager] kördes inte på grund av CSP-fel'
description: Använd ACSD-60788-korrigeringen för att åtgärda Adobe Commerce-problemet där anpassade skript för  [!DNL Google Tag Manager]  inte körs på grund av fel i Content Security Policy (CSP).
feature: Security
role: Admin, Developer
exl-id: 3392da76-86cb-4357-8658-c95d914a5829
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 0%

---

# ACSD-60788: Anpassade skript för [!DNL Google Tag Manager] körs inte på grund av fel i säkerhetsprincipen för innehåll

ACSD-60788-korrigeringen åtgärdar ett problem där anpassade skript för [!DNL Google Tag Manager] inte körs på grund av fel i säkerhetsprincipen för innehåll. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52 är installerad. Korrigerings-ID är ACSD-60788. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.7-p1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Anpassade skript för [!DNL Google Tag Manager] körs inte på grund av fel i Content Security Policy (CSP).

<u>Steg som ska återskapas</u>:

1. Konfigurera variabeln *[!DNL Google Tag Manager]*.
1. Konfigurera den anpassade HTML-taggen *[!DNL Google Tag Manager]*.
1. Placera följande JavaScript-kod i den första taggen:

   ```
   <script nonce="{{gtmNonce}}">
   console.log("Nonce from simple JS {{gtmNonce}}");
   </script>
   ```

1. Töm cacheminnen när du har konfigurerat *GTM*.
1. Öppna utvecklarkonsolen i webbläsaren.
1. Öppna hemsidan.

<u>Förväntade resultat</u>:

Webbläsarens dev-konsol visar *Nonce från enkel JS (slumpmässiga tecken)*.

<u>Faktiska resultat</u>:

Webbläsarens dev-konsol visar *Nonce från enkel JS undefined*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
