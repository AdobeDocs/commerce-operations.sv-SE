---
title: 'ACSD-66506: Ett backend-fel inträffar när delade katalogprodukter har tagits bort och omtilldelats'
description: Använd korrigeringsfilen ACSD-66506 för att åtgärda Adobe Commerce-problemet där serverdelen orsakar felet *Den begärda produkten finns inte. Verifiera produkten och försök igen* efter att tidigare tilldelade produkter har tagits bort och tilldela nya till en delad katalog.
feature: B2B
role: Admin, Developer
type: Troubleshooting
source-git-commit: 8f77101832ccfb415d040c202f0fc7221f97419a
workflow-type: tm+mt
source-wordcount: '425'
ht-degree: 0%

---


# ACSD-66506: Ett backend-fel inträffar när delade katalogprodukter har tagits bort och omtilldelats

ACSD-66506-korrigeringen åtgärdar ett problem där serverdelen orsakar felet *Den begärda produkten finns inte. Verifiera produkten och försök igen* när du har tagit bort tidigare tilldelade produkter och tilldelat nya till en delad katalog. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 har installerats. Korrigerings-ID är ACSD-66506. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du har tagit bort tidigare tilldelade produkter och tilldelat nya till en **[!UICONTROL Shared Catalog]** returnerar backend följande fel: *Den begärda produkten finns inte. Verifiera produkten och försök igen*

<u>Steg som ska återskapas</u>:

1. Skapa vissa produkter med prestandaverktygen: `bin/magento setup:perf:generate-fixtures setup/performance-toolkit/profiles/ce/small.xml`
1. Gå till **[!UICONTROL [!DNL B2B] Features]**-konfiguration och ange **[!UICONTROL Enable Company]** och **[!UICONTROL Enable Shared Catalog]** till `Yes`.
1. Skapa en ny delad katalog.
1. Tilldela alla genererade produkter till den nyligen skapade delade katalogen.
1. Använd **[!UICONTROL Product Import]** för att ta bort en produkt som har tilldelats den delade katalogen.
   1. Exportera en produkt som filtrerats med SKU.
   1. Välj **[!UICONTROL Import Behavior: Delete]** och importera sedan samma fil.
1. Öppna **[!UICONTROL Shared Catalog]** och konfigurera priser och struktur.
   1. Välj **[!UICONTROL Set Pricing and Structure]**.
   1. Klicka på **[!UICONTROL Next]** och sedan på **[!UICONTROL Generate Catalog]**.
   1. Klicka på **[!UICONTROL Save]**.

<u>Förväntade resultat</u>:

Inga fel inträffar och produkterna finns kvar i den delade katalogen även om ett fel inträffar.

<u>Faktiska resultat</u>:

Ett fel inträffar: *Den begärda produkten finns inte. Verifiera produkten och försök igen*, så tas alla produkter bort från den delade katalogen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
