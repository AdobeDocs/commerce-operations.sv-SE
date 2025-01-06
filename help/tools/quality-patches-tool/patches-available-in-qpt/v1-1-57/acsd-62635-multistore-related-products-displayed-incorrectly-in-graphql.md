---
title: 'ACSD-62635: Produkter som är relaterade till flera lager visas felaktigt i  [!DNL GraphQL]'
description: Använd patchen ACSD-62635 för att åtgärda Adobe Commerce-problemet där produkter som hör till flera butiker inte visas korrekt i produktfrågan  [!DNL GraphQL] .
feature: B2B
role: Admin, Developer
source-git-commit: 8e6f6590dbed43eb8ce75b694a05ee951b538814
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-62635: Produkter som är relaterade till flera lager visas felaktigt i [!DNL GraphQL]

Korrigeringen ACSD-62635 åtgärdar ett problem där produkter som är relaterade till flera butiker inte visas korrekt i produktfrågan [!DNL GraphQL]. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) 1.1.57 är installerad. Korrigerings-ID är ACSD-62635. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När B2B är aktiverat returnerar [!DNL GraphQL]-begäran alla relaterade produkter från alla webbplatser, även om ett butiksvyscope används i begäran.

<u>Steg som ska återskapas</u>:

1. Skapa två webbplatser, butiker och butiksvyer.
1. Skapa följande enkla produkter:
   * En huvudversion med SKU *product1* tilldelad till alla webbplatser
   * En tilldelad endast *webbplats 1*
   * En tilldelad endast *webbplats 2*
   * En tilldelad till både *webbplats 1* och *webbplats 2*
1. Lägg till alla produkter som hör till *product1*.
1. Aktivera [!UICONTROL B2B] och [!UICONTROL Shared Catalog].
1. Lägg till alla produkter i den delade standardkatalogen.
1. Skicka [!DNL GraphQL]-begäran om att hämta *product1* och dess relaterade produkter med butikskoden *Website 1* i rubriken.

<u>Förväntade resultat</u>:

Svaret innehåller endast relaterade produkter från de webbplatser som motsvarar den butikskod som skickats i begärandehuvudet.

<u>Faktiska resultat</u>:

Svaret innehåller alla relaterade produkter från alla webbplatser, oavsett vilken butikskod som har angetts i begäran.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
