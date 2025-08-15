---
title: 'ACSD-55231: Fel hittades inte i SKU när snabbordningsfunktioner användes'
description: Använd patchen ACSD-55231 för att åtgärda Adobe Commerce-problemet där du fick *'SKU:n hittades inte i katalogfelet* när du försökte lägga till en produkt i kundvagnen med hjälp av snabbbeställningsfunktionerna.
feature: Products, Checkout, B2B
role: Admin, Developer
exl-id: f0a04773-7395-4945-a72b-5a6a018bc94e
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '496'
ht-degree: 0%

---

# ACSD-55231: Fel hittades inte i SKU när snabbordningsfunktioner användes

Korrigeringen ACSD-55231 åtgärdar ett fel där *&#39;SKU:n hittades inte i katalogfelet* när du försöker lägga till en produkt i vagnen med hjälp av snabborderfunktioner. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.44 har installerats. Korrigerings-ID är ACSD-55231. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det gick inte att hitta SKU:n *i katalogen* vid sökning efter produkter att lägga till i vagnen med hjälp av snabbordningsfunktioner.

<u>Steg som ska återskapas</u>:

1. Installera Adobe Commerce med B2B-moduler.
1. Navigera till **[!UICONTROL Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]** och ange:
   * **[!UICONTROL Enable company]**: *Ja*
   * **[!UICONTROL Enable Shared Catalog]**: *Ja*
   * **[!UICONTROL Enable Quick Order]**: *Ja*
1. Spara konfigurationen ovan.
1. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Shared Catalogs]** och skapa en ny delad katalog.
1. Navigera till **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** och skapa en ny kund:
   * I gruppfältet väljer du den nyligen skapade delade katalogen och ställer in *[!UICONTROL Allow remote shopping assistance]* på *Ja*.
1. Generera en enkel produkt med SKU *p12*, associera den med kategorin *c1* och välj sedan den nyligen skapade delade katalogen i avsnittet [!UICONTROL Product in Shared Catalog].
1. Kör:

   ```
   bin/magento ind:rei 
   bin/magento c:f 
   bin/magento cron:run (multiple times)
   ```

1. Uppdatera administratörssidan.
1. Navigera till **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** och redigera kunden som skapades tidigare.
1. Klicka på **[!UICONTROL Login as customer]**.
1. Gå till **[!UICONTROL Quick order]**.
1. Sök i SKU:n *p12* och klicka på **[!UICONTROL Product Suggestion]**.
1. Lägg produkten i kundvagnen och beställ.
1. Gå tillbaka till **[!UICONTROL Quick Order]**, sök efter SKU *p12* igen och klicka på **[!UICONTROL Product Suggestion]**.

<u>Förväntade resultat</u>:

Du kan lägga till produkten i kundvagnen med hjälp av snabbbeställningsfunktionerna.

<u>Faktiska resultat</u>:

Du kan inte lägga till produkten i kundvagnen med hjälp av snabbbeställningsfunktionen och få *&quot;SKU:n hittades inte i katalogen&quot;*&quot; vid sökning efter produkt-SKU:n.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
