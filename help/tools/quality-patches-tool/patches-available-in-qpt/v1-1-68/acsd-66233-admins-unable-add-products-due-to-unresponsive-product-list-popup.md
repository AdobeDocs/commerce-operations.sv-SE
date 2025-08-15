---
title: 'ACSD-66233: Administratörer kan inte lägga till produkter på grund av att popup-fönstret för produktlistan inte svarar'
description: Använd korrigeringsfilen ACSD-66233 för att åtgärda Adobe Commerce-problemet där administratörer inte kan lägga till produkter i kategorier eftersom popup-fönstret [!UICONTROL Add Product] i Visual Merchandiser läses in oändligt.
feature: Inventory, Merchandising
role: Admin, Developer
type: Troubleshooting
exl-id: 2e01e62d-b6f9-4aa5-9040-7908aa83d422
source-git-commit: a1241f709fc1b7128d1d267c54586c60dadab436
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-66233: Administratörer kan inte lägga till produkter på grund av att popup-fönstret för produktlistan inte svarar

Korrigeringen ACSD-66233 åtgärdar ett problem där administratörer inte kan lägga till produkter i kategorier eftersom popup-fönstret [!UICONTROL Add Product] i Visual Merchandiser läses in oändligt. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 har installerats. Korrigerings-ID är ACSD-66233. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.8 - 2.4.8-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett problem där popup-fönstret [!UICONTROL Add Product] i Visual Merchandiser läses in oavbrutet, vilket förhindrar administratörer att lägga till produkter i kategorier.

<u>Steg som ska återskapas</u>:

1. Installera och aktivera lagermodulerna.
1. Skapa ett stort antal lagerkällor (till exempel 700).
1. Skapa flera lagerlager (till exempel 12) och tilldela dem lagerkällor.
1. Skapa vissa produkter och tilldela dem till lagerkällorna.
1. Skapa en kategori.
1. Expandera avsnittet [!UICONTROL Products in Category].
1. Klicka på knappen [!UICONTROL Add Product].
1. Lägg märke till popup-fönstret med listan över produkter.

<u>Förväntade resultat</u>:

Produktlistan läses in i popup-fönstret inom rimlig tid.

<u>Faktiska resultat</u>:

Popup-fönstret läses in oavbrutet och visar inte produktlistan.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
