---
title: "ACSD-48293: sammansatta produkter ur lager vid försäljning av underordnade produkter som återköpts"
description: Använd patchen ACSD-48293 för att åtgärda Adobe Commerce-problemet där de sammansatta produkterna hamnar utanför lagret när de utsålda underordnade produkterna skickas tillbaka till lagret.
feature: Admin Workspace, Orders, Products
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# ACSD-48293: Sammansatta produkter som inte ingår i lager när de säljs ut i underprodukter som återställs

Korrigeringen ACSD-48293 åtgärdar ett problem där de sammansatta produkterna hamnar utanför lagret när de utsålda underordnade produkterna skickas tillbaka till lagret. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.25 är installerad. Korrigerings-ID är ACSD-48293. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Sammansatta produkter går ut ur lager när de underordnade produkterna som sålts returneras till lager.

<u>Steg som ska återskapas</u>:

1. Skapa en sekundär webbplats-, butiks- och butiksvy.
1. Skapa två källor och resurser och tilldela dem till varje webbplats.
1. Aktivera alternativet för att visa färdiga produkter under **[!UICONTROL Store]** > **[!UICONTROL Config]** > **[!UICONTROL Catalog]** > **[!UICONTROL Inventory]** > **[!UICONTROL Stock Options]** > **[!UICONTROL Display Out-of-Stock Products]** = *[!UICONTROL Yes]*.
1. Skapa en konfigurerbar produkt med en associerad produkt med hjälp av den primära webbplatsens Stock-källa (ange kvantitet = 1).
1. Gör en beställning av den konfigurerbara produkten.
1. Kör kronen.
1. Öppna den konfigurerbara produkten från butiken och bekräfta att den inte är i lager.
1. Öppna den konfigurerbara produkten från [!UICONTROL Admin] och ställ in **[!UICONTROL Manage Stock Option]** på *[!UICONTROL No]*.
1. Kör kronen.
1. Leverera beställningen och lägg till kvantitet till den enkla produkt som lagrar den.
1. Kör kronen.
1. Kontrollera produkttillgängligheten i butiken.

<u>Förväntade resultat</u>:

Den konfigurerbara produkten finns i lager.

<u>Faktiska resultat</u>:

Den konfigurerbara produkten är inte i lager.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
