---
title: 'ACSD-58108: SQL-fel inträffar i det anpassade modultillägget för sorteringsrutnät på grund av att det saknas ett kopplingstabellnamn'
description: Använd patchen ACSD-58108 för att åtgärda Adobe Commerce-problemet där ett namn på kopplingsregister som saknas i det anpassade modultillägget för orderstödraster orsakar SQL-fel vid filtrering av vissa kolumner.
feature: Orders, System
role: Admin, Developer
type: Troubleshooting
source-git-commit: 26009fee51fb81e2517ad09319bac1190d127564
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---


# ACSD-58108: SQL-fel inträffar i det anpassade modultillägget för sorteringsrutnät på grund av att det saknas ett kopplingstabellnamn

Korrigeringen ACSD-58108 åtgärdar ett problem där ett saknat kopplingstabellnamn i det anpassade modultillägget för orderstödraster orsakar SQL-fel vid filtrering av vissa kolumner. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 har installerats. Korrigerings-ID är ACSD-58108. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.5.0.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.7-p6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det saknade namnet på kopplingstabellen i den ursprungliga hämtningstabellen orsakar SQL-fel i orderstödrastret när ett anpassat modultillägg används. Problemet inträffar eftersom funktionen `addFilterToMap` inte fungerar för vissa kolumner när den har anslutits till tabellen **[!UICONTROL sales_order_item]**, vilket resulterar i fel vid filtrering.

<u>Steg som ska återskapas</u>:

&#x200B;01. Installera en 2.4-framkallningsinstans.
&#x200B;02. Skapa en ny order.
&#x200B;03. Installera en anpassad modul med ett SQL-tillägg.
&#x200B;04. Navigera till **[!UICONTROL Admin]** > **[!UICONTROL Sales]** > **[!UICONTROL Orders]**.
&#x200B;05. Använd filtret **[!UICONTROL Purchase Date]** och vänta på resultatet.
&#x200B;06. Använd filtret **[!UICONTROL Product SKU]**.

<u>Förväntade resultat</u>:

Filtreringsordningen i rutnätet fungerar utan fel.

<u>Faktiska resultat</u>:

Ett fel inträffar när filter tillämpas i orderstödrastret.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
