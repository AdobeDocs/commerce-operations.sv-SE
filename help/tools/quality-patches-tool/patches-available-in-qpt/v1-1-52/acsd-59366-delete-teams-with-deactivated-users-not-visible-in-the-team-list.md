---
title: "ACSD-59366: Ta bort team med inaktiverade användare som inte visas i teamlistan"
description: Använd korrigeringsfilen ACSD-59366 för att åtgärda Adobe Commerce-problemet om ett fel inträffar när du försöker ta bort ett team som innehåller inaktiverade användare som inte visas i grupplistan.
feature: GraphQL, Companies
role: Admin, Developer
source-git-commit: 8037db7a89cd850385dc88750e881f68ae62172f
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-59366: Ta bort team med inaktiverade användare som inte visas i teamlistan

ACSD-59366-korrigeringen åtgärdar ett problem där ett fel inträffar när du försöker ta bort ett team som innehåller inaktiverade användare som inte visas i grupplistan. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.52 har installerats. Korrigerings-ID är ACSD-59366. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett fel inträffar när du tar bort ett team som innehåller inaktiverade användare som inte visas i grupplistan.

<u>Förutsättningar</u>:

Adobe Commerce B2B-moduler installeras och företag aktiveras.

<u>Steg som ska återskapas</u>:

1. Skapa och logga in med en företagsanvändare.
1. Skapa ett nytt team under företagsstrukturen.
1. Skapa en ny användare under det nya teamet.
1. Redigera den nya användaren och inaktivera.
1. Markera teamet och ta bort det.

<u>Förväntade resultat</u>:

Teamet har en eller flera inaktiva användare. Om du tar bort teamet tas tilldelningen av dessa användare bort. Du kan hitta inaktiva användare i avsnittet [!UICONTROL Company Users].

<u>Faktiska resultat</u>:

Ett fel inträffar när du försöker ta bort ett team med en inaktiverad användare.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.


