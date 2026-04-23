---
title: 'ACSD-6411: Korrigerar *InvalidArgumentException: Klassen finns inte*-fel vid inställning av kapslade villkor för en produktkomponent i  [!DNL Page Builder]'
feature: Products, Page Builder
role: Admin, Developer
exl-id: dc39c65b-fb78-4105-b0e8-92a78b49adaf
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-6411: Korrigerar felet *InvalidArgumentException: Klassen finns inte* när kapslade villkor för en produktkomponent anges i [!DNL Page Builder]

Korrigeringen ACSD-6411 åtgärdar ett problem där *InvalidArgumentException: klassen finns inte* fel i `vendor/magento/module-rule/Model/ConditionFactory.php:50` när kapslade villkor för en produktkomponent ställs in i [!DNL Page Builder]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60 har installerats. Korrigerings-ID är ACSD-6411. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder)  2.4.6-p8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Felet *InvalidArgumentException: Klassen finns inte i /app/&lt;project id\>/vendor/magento/module-rule/Model/ConditionFactory.php* genereras när ett *[!UICONTROL Conditions Combination]* läggs till i villkoret [!DNL Page Builder] för produktwidgeten.

<u>Steg som ska återskapas</u>:

1. Logga in på Adobe Commerce-administratören.
1. Gå till **[!UICONTROL Content]** > *[!UICONTROL Elements]* > **[!UICONTROL Pages]**.
1. Lägg till en ny sida (eller redigera en befintlig sida).
1. Expandera avsnittet **[!UICONTROL Content]** och klicka på **[!UICONTROL Edit with Page Builder]**.
1. Lägg till en ny rad och sedan widgeten **[!UICONTROL Products]**.
1. Konfigurera widgeten **[!UICONTROL Products]**.
1. Välj **[!UICONTROL Condition]** under **[!UICONTROL Select Products By]**.
1. Lägg till ett nytt villkor och välj **[!UICONTROL Conditions Combination]** i listrutan.

<u>Förväntade resultat</u>:

Inga fel i loggar.

<u>Faktiska resultat</u>:

Följande undantag registreras i loggarna:

*report.CRITICAL: InvalidArgumentException: Klassen finns inte i vendor/magento/module-rule/Model/ConditionFactory.php:50*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
