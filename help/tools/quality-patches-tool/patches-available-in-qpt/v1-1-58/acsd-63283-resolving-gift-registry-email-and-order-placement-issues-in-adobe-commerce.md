---
title: 'ACSD-63283: Löser [!UICONTROL Gift Registry] e-post- och orderplaceringsproblem i Adobe Commerce'
description: Använd korrigeringsfilen ACSD-63283 för att åtgärda Adobe Commerce-problemet där beställning av objekt från [!UICONTROL Gift Registry] orsakar ett undantag och säkerställer att [!UICONTROL Gift Registry Updates] bara inkluderar rätt objekt.
feature: Gift, Shopping Cart
role: Admin, Developer
source-git-commit: a9dd031ba004954074a0551315e80a2bd733f690
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-63283: Löser [!UICONTROL Gift Registry] e-post- och orderplaceringsproblem i Adobe Commerce

Korrigeringen ACSD-63283 åtgärdar ett problem där beställning av objekt från [!UICONTROL Gift Registry] orsakar ett undantag och säkerställer att [!UICONTROL Gift Registry Updates] bara inkluderar rätt objekt. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 har installerats. Korrigerings-ID är ACSD-63283. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

>[!NOTE]
>Den här korrigeringen ersätter och utökar QPT-korrigeringen [ACSD-56280](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/patches-available-in-qpt/v1-1-44/acsd-56280-gift-registry-purchases-are-not-completed).

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Funktionen [!UICONTROL Gift Registry] i Adobe Commerce påverkas av två viktiga problem:

* När en kund gör en beställning av artiklar från sin [!UICONTROL Gift Registry] misslyckas processen på grund av att ett undantag utlöses.
* Dessutom innehåller e-postmeddelandet [!UICONTROL Gift Registry Updates] som skickas till registerägaren felaktigt objekt från alla presentregister, i stället för att begränsa uppdateringarna av objekt i det specifika registret som uppdateras.

<u>Steg som ska återskapas</u>:

1. Skapa två produkter: produkt A och produkt B.
1. Skapa två kunder: kund A och kund B.
1. Logga in som kund A och skapa en ny [!UICONTROL Gift Registry].
1. Navigera till produkt A:s produktsida och lägg till den i [!UICONTROL Wishlist]. Öppna [!UICONTROL Wishlist Page] och flytta produkt A till [!UICONTROL Gift Registry] med [!UICONTROL Add to Gift Registry].
1. Logga in som kund B, skapa en ny [!UICONTROL Gift Registry] och lägg till produkt B i den.
1. Som kund B delar du [!UICONTROL Gift Registry] via e-post: **[!UICONTROL My Account]> [!UICONTROL Gift Registry] >[!UICONTROL Share]**.
1. Logga ut som kund B.
1. Klicka på länken i e-postmeddelandet. Lägg till produkt B i [!UICONTROL Cart] och beställ.

<u>Förväntade resultat</u>:

Kund B får e-postmeddelandet med uppdaterade artiklar endast från presentregistret.

<u>Faktiska resultat</u>:

Kund B får e-postmeddelandet med artiklar från alla presentregister.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
