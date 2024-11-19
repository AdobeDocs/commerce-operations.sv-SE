---
title: "ACSD-61845: Ett fel uppstod för begäranden med text/html-huvudet accept"
description: Använd patchen ACSD-61845 för att åtgärda Adobe Commerce-problemet där en HTTP-begäran med endast en *text/html* accept header orsakar ett 500-fel, där B2B-moduler är installerade.
feature: B2B
role: Admin, Developer
source-git-commit: 8dbf91806097281fb4f7c74e182f10b09b18e925
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---

# ACSD-61845: Ett fel uppstod för begäranden med rubriken *text/html* accept

Korrigeringen ACSD-61845 åtgärdar ett problem där en HTTP-begäran med endast en *text/html* accept-rubrik orsakar ett 500-fel på grund av felmatchningar i medietypen i svarshanteringen. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 har installerats. Korrigerings-ID är ACSD-61845. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p1 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du skickar en HTTP-begäran med endast *text/html* i huvudet accept inträffar ett 500-fel på grund av en felmatchning i medietypskonfigurationen.

<u>Förutsättningar</u>:

B2B-moduler installeras och aktiveras.

<u>Steg som ska återskapas</u>:

1. Skicka en begäran med endast *text/html* i huvudet accept enligt följande:

   ```
   curl -I --header "Accept: text/html, text/plain" http://<hostname>/pub/
   ```

<u>Förväntade resultat</u>:

Sidan returneras med en *200-statuskod*.

<u>Faktiska resultat</u>:

Ett 500-fel returneras, med följande felmeddelande i `exception.log`:

```
Magento\Framework\Webapi\Exception: Server cannot match any of the given Accept HTTP header media type(s) from the request: "text/html" with media types from the config of response renderer. in vendor/magento/framework/Webapi/Rest/Response/RendererFactory.php:84
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

[[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
