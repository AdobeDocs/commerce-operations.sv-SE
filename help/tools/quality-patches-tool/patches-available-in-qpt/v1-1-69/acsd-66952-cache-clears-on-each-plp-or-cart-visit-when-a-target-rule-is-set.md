---
title: 'ACSD-66952: Cacheminnet rensas vid varje PLP- eller kundvagnsbesök när en målregel anges'
description: Använd korrigeringsfilen ACSD-66952 för att åtgärda Adobe Commerce-problemet där cache rensades vid varje PLP- eller kundvagnsbesök, vilket orsakade onödig prestandaförsämring när en målregel angavs.
feature: Shopping Cart, Cache, Price Rules
role: Admin, Developer
type: Troubleshooting
exl-id: abff5761-bcf1-4cfc-b5d9-6a7e1ca907e7
source-git-commit: cf0f5992c7b2a51b270a4a1a81fd50305a92759c
workflow-type: tm+mt
source-wordcount: '368'
ht-degree: 0%

---

# ACSD-66952: Cacheminnet rensas vid varje PLP- eller kundvagnsbesök när en målregel anges

Korrigeringen ACSD-66952 åtgärdar ett problem där cachen rensas på varje PLP- eller kundvagnsbesök, vilket orsakar prestandaförluster när en målregel ställs in. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 har installerats. Korrigerings-ID är ACSD-66952. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Problem där cachen rensas på varje PLP- eller kundvagnsbesök, vilket orsakar prestandaförluster när en målregel anges.

<u>Steg som ska återskapas</u>:

1. Generera en liten exempeldatauppsättning.
1. Skapa målregelvärden enligt nedan:
   1. **[!UICONTROL Rule information]**
      * **[!UICONTROL Rule Name]** = *Relaterade produkter*
      * **[!UICONTROL Status]** = *Aktiv*
      * **[!UICONTROL Apply to]** = *Relaterade produkter*
   1. **[!UICONTROL Products to Match]**
      * Låt standardvärdet vara kvar.
   1. **[!UICONTROL Products to Display]**
      * Om **ALLA** av dessa villkor är *true* anger du **[!UICONTROL Product Category]** = *Konstantvärde 11111*
1. Börja övervaka loggarna för cacheogiltigförklaringsbegäranden.
1. Besök produktsidan.
1. Lägg en produkt i kundvagnen och navigera till kundvagnssidan.

<u>Förväntade resultat</u>:

Programmet bör inte göra cacheminnet ogiltigt när du bläddrar på webbplatsen.

<u>Faktiska resultat</u>:

Cachetaggar blir ogiltiga.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool]
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden för Commerce om molninfrastruktur

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken
