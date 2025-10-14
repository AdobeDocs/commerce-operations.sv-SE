---
title: 'ACP2E-3767: Det senaste paketalternativet visas igen när en paketprodukt har sparats'
description: Använd programfixen ACP2E-3767 för att åtgärda Adobe Commerce-problemet där det sista paketalternativet i en paketprodukt inte kunde tas bort.
feature: Products, Catalog Management
role: Admin, Developer
type: Troubleshooting
source-git-commit: f39442925d9cc82087af9e84d91137a0fcd0ec14
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 0%

---


# ACP2E-3767: Det senaste paketalternativet visas igen när en paketprodukt har sparats

Programfixen ACP2E-3767 åtgärdar ett problem där det senaste paketalternativet visas igen när paketprodukten har sparats. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 har installerats. Korrigerings-ID är ACP2E-3767. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det sista paketalternativet i en paketprodukt kan inte tas bort.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]**.
1. Välj **[!UICONTROL Simple Product]** i listrutan.
1. Ange obligatoriska data och spara.
1. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Products]** > **[!UICONTROL Add Product]**.
1. Välj **[!UICONTROL Bundle Product]** i listrutan.
1. Ange obligatoriska data.
1. Klicka på **[!UICONTROL Add Option]** i Paketobjekt.
1. Lägg till en titel i det nya alternativet och klicka sedan på **[!UICONTROL Add Products to Option]**.
1. Välj den tidigare skapade enkla produkten och sedan **[!UICONTROL Add Selected Products]**.
1. Spara paketprodukt.
1. Ta bort paketalternativet och spara.

<u>Förväntade resultat</u>:

1. Paketalternativet har tagits bort.
1. Ett meddelande visas om borttagning inte tillåts.

<u>Faktiska resultat</u>:

1. Paketalternativet är fortfarande aktivt.
1. Inga fel eller meddelanden visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
