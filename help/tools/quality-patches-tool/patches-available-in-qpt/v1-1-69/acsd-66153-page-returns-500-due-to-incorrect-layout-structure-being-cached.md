---
title: 'ACSD-66153: Sidan returnerar 500-fel på grund av cachelagrad felaktig layoutstruktur'
description: Använd korrigeringsfilen ACSD-66153 för att åtgärda Adobe Commerce-problemet där en sida returnerar felkoden 500 på grund av en cachelagrad felaktig layoutstruktur.
feature: Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: 70c7255e369ef366407d539488f0d815eb93f48a
workflow-type: tm+mt
source-wordcount: '342'
ht-degree: 0%

---


# ACSD-66153: Sidan returnerar 500-fel på grund av cachelagrad felaktig layoutstruktur

Korrigeringen ACSD-66153 åtgärdar ett problem där en sida returnerar en felkod 500 på grund av en cachelagrad felaktig layoutstruktur. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 har installerats. Korrigerings-ID är ACSD-66153. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p10

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En sida returnerar ett 500-fel på grund av en cache-lagrad felaktig layoutstruktur.

<u>Steg som ska återskapas</u>:

1. Installera `2.4-develop`.
1. Skapa och installera anpassad modul:
1.1 Lägg till ett anpassat block i layouten `catalog_category_view`.
1.1 Injicera `Magento\Framework\View\Result\Layout` i det anpassade blocket via dess konstruktor.
1. Skapa kategorin **[!UICONTROL shop]**.
1. Öppna **[!UICONTROL two terminal windows]**:
   1. **Terminal 1**: Rensa layoutcachen kontinuerligt:

      ```
      for i in {1..200}; do
        bin/magento cache:clean layout
      done
      ```

   1. **Terminal 2**: Simulera samtidiga begäranden till kategorisidan:

      ```
      for i in {1..200}; do
        curl -s -o /dev/null -w "Request $i: HTTP %{http_code}\n""http://your_magento_base_url/shop.html?req=$i"
      done
      ```

1. Vissa begäranden misslyckas slumpmässigt med en statuskod på 500, och i `var/log/support_report.log` visas följande fel:

   ```
   report.CRITICAL: The element with the "root" ID wasn't found. Verify the ID and try again. [] []
   ```

<u>Förväntade resultat</u>:

Alla begäranden returnerar 200 OK.

<u>Faktiska resultat</u>:

Vissa begäranden returnerar då och då 500 internt serverfel.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
