---
title: 'ACSD-66301: Om du flyttar produkter från en beställning till kundvagnen i Commerce Admin matchar inte antalet licenser'
description: Använd patchen ACSD-66301 för att åtgärda Adobe Commerce-problemet där produkter i kundvagnen inte tas bort när du skapar en order från Admin-panelen efter att de lagts till i ordern.
feature: Orders, Products
role: Admin, Developer
type: Troubleshooting
source-git-commit: 9a4224c02634514a9428dc6b0daf4c1d5f5c7c43
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 0%

---


# ACSD-66301: Om du flyttar produkter från en beställning tillbaka till kundvagnen i Commerce Admin matchar inte antalet licenser

Korrigeringen ACSD-66301 åtgärdar ett problem där det uppstår problem när produkter flyttas tillbaka från en beställning till varukorgen i Admin, vilket resulterar i att kvantiteten inte matchar. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 har installerats. Korrigerings-ID är ACSD-66301. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p10, 2.4.7-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p9 - 2.4.6-p11, 2.4.7-p4 - 2.4.7-p6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om du flyttar produkter från en beställning tillbaka till kundvagnen i Commerce Admin blir antalet felaktiga.

<u>Steg som ska återskapas</u>:

1. Skapa en användare i butiken.
2. Lägg en produkt i kundvagnen med kvantitet = *5*.
3. Gå till panelen Admin och öppna användarkontot där produkten lades till.
4. Klicka på **[!UICONTROL Create Order]**.
5. I den vänstra panelen kan du visa kundens aktiviteter, inklusive produkt och tillagd kvantitet.
6. Lägg till produkten i ordern.
7. Uppdatera kvantiteten = *4* i huvudorderavsnittet.
8. Klicka på knappen **[!UICONTROL Update Items and Quantities]**.
9. Överför de valda artiklarna från ordern tillbaka till kundens kundvagn.

<u>Förväntade resultat</u>:

Produkten har lagts till i kundvagnen med den nya kvantiteten = *4*.

<u>Faktiska resultat</u>:

Produkten har lagts till i kundvagnen med den gamla kvantiteten = *5*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
