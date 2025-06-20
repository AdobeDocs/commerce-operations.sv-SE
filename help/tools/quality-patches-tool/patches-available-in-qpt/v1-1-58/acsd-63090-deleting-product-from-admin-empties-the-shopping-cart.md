---
title: 'ACSD-63090: Om du tar bort en produkt från Admin töms kundvagnen'
description: Använd patchen ACSD-63090 för att åtgärda Adobe Commerce-problemet där kundens varukorg försvann efter att en produkt raderats efter att den lagts till i kundvagnen.
feature: Shopping Cart, Quotes
role: Admin, Developer
exl-id: c07778cb-390f-4202-9539-7bb159e4b714
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63090: Om du tar bort en produkt från Admin töms kundvagnen

Korrigeringen ACSD-63090 löser problemet där kundens varukorg försvann efter att en produkt tagits bort från Admin, efter att den lagts till i kundvagnen. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.58 har installerats. Korrigerings-ID är ACSD-63090. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kundvagnsartiklar försvinner när en produkt tas bort efter att ha lagts till i kundvagnen.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt med två underordnade produkter.
1. Logga in som en registrerad kund.
1. Lägg båda de underordnade produkterna i kundvagnen.
1. Logga ut från kontot.
1. Ta bort en av de underordnade produkterna från katalogen.
1. Uppdatera priset för den andra underordnade produkten med API:t.

<u>Förväntade resultat</u>:

Den återstående produkten visas i kundvagnen och den befintliga offerten uppdateras i databastabellen `quote`.

<u>Faktiska resultat</u>:

* Minivagnen är tom.
* En ny offertpost genereras i databastabellen `quote`.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
