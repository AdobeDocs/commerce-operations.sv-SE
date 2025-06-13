---
title: 'ACSD-53239: Lagerindexeraren rensar alla cacheminnen'
description: Använd korrigeringsfilen ACSD-53239 för att åtgärda Adobe Commerce-problemet där alla cacheminnen rensas i [!UICONTROL Update on Schedule]-läget.
feature: GraphQL, Inventory, Catalog Management
role: Admin, Developer
exl-id: 69e71e2d-8f26-4200-ad4a-6bd9e45627e4
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '323'
ht-degree: 0%

---

# ACSD-53239: Lagerindexeraren rensar alla cacheminnen i [!UICONTROL Update on Schedule]-läget

Korrigeringen ACSD-53239 åtgärdar ett problem där alla cacheminnen rensas i [!UICONTROL Update on Schedule]-läget. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.36 är installerad. Korrigerings-ID är ACSD-53239. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.5-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Lagerindexeraren rensar alla cacheminnen i [!UICONTROL Update on Schedule]-läget.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Catalog Products]** och välj cirka *1200* produkter.
2. Uppdatera *[!UICONTROL Qty]* till ett nytt värde och klicka på **[!UICONTROL Save]**.
3. Kör `bin/magento cron:run` omedelbart efter att du har sparat.
4. Kör följande GraphQL-fråga:

   ```GraphQL
   {
     storeConfig {
     absolute_footer
     }
   }
   ```

<u>Förväntade resultat</u>

Frågan bearbetas inom den vanliga tiden.

<u>Faktiska resultat</u>

Frågan bearbetas ovanligt långsamt.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
