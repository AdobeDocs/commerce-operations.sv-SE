---
title: 'ACSD-64592: Länkar till presentkort som inte är standard för butik dirigerar om till standardwebbplatsen'
description: Använd patchen ACSD-64592 för att åtgärda problemet där länken Presentkortskod i e-postmeddelandet har standardwebbplatsens URL när ett virtuellt presentkort köps från den sekundära (ej standard) webbplatsen.
feature: Gift, Products
role: Admin, Developer
source-git-commit: 39866e1cf8f2afd892c9e151259a446d0277d58f
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---


# ACSD-64592: Länkar till presentkort som inte är standard för butik dirigerar om till standardwebbplatsen

Korrigeringen ACSD-64592 åtgärdar ett problem där ett virtuellt presentkort som finns på flera platser, om det köps från en sekundär (icke-primär) webbplats, kommer e-postmeddelandet som innehåller länken Presentkortskod att dirigera användare till standardwebbplatsens URL. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När ett virtuellt presentkort köps från en sekundär (icke-standard) webbplats i en konfiguration med flera webbplatser dirigeras användarna till standardwebbplatsens URL via e-postmeddelandet som innehåller länken Presentkortskod.

<u>Steg som ska återskapas</u>:

1. Skapa en sekundär webbplats-, butiks- och butiksvy.
1. Konfigurera olika bas-URL:er för basen och den sekundära webbplatsen.
1. Skapa ett virtuellt presentkort med några beloppsalternativ.
1. Generera en ny kodpool på **[!UICONTROL Marketing]** > **[!UICONTROL Promotions]** > **[!UICONTROL Gift Card Accounts]**.
1. Lägg en order med presentkortsprodukten på den sekundära webbplatsen.
1. Fakturera ordern i Commerce-administratören.
1. Kontrollera URL:en i länken Presentkortskod för *Du har fått en gåva från e-postmeddelandet Två*.

<u>Förväntade resultat</u>:

Länken Presentkortskod ska ha länken till den andra webbplatsen.

<u>Faktiska resultat</u>:

Länken Presentkortskod har webbplatsens standardwebbadress, även om beställningen finns på den andra webbplatsen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:
* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
