---
title: 'ACSD-50813: Administratören kan inte lägga till paketerade produkter som innehåller ett snedstreck'
description: Använd patchen ACSD-50813 för att åtgärda prestandaproblemet i Adobe Commerce där administratören inte kan lägga till paketerade produkter som innehåller ett snedstreck (`/`) i SKU:n med funktionen *Lägg till produkter efter SKU* i administratörsbeställningen.
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-50813: Administratören kan inte lägga till paketerade produkter som innehåller ett snedstreck

Korrigeringen ACSD-50813 åtgärdar ett problem där administratören inte kan lägga till paketerade produkter som innehåller ett snedstreck (`/`) i SKU:n med funktionen *[!UICONTROL Add Products by SKU]* i administratörsordningen. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.34 har installerats. Korrigerings-ID är ACSD-50813. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratören kan inte lägga till paketerade produkter som innehåller ett snedstreck (`/`) i SKU:n med funktionen *[!UICONTROL Add Products by SKU]* i administratörsordningen.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Catalog]** > **[!UICONTROL Products]**.
1. Skapa en enkel produkt.
1. Skapa en ny paketerad produkt.
1. Lägg till ett snedstreck (`/`) mitt i SKU:n (Exempel: *Bu/ndle*).
1. Lägg till ett paketerat alternativ med **[!UICONTROL Input Type]** = *[!UICONTROL Dropdown]*.
1. Tilldela alternativet minst en enkel produkt.
1. Gå till **[!UICONTROL Sales]** > **[!UICONTROL Orders]** och skapa en ny order.
1. Klicka på **[!UICONTROL Add Products by SKU]**.
1. Ange din SKU och klicka på **[!UICONTROL Add to Order]**.
1. Öppna konsolen.
1. Klicka på **[!UICONTROL Configure]**.

<u>Förväntade resultat</u>:

Det finns inget fel.

<u>Faktiska resultat</u>:

JS-fel i konsolen:

*Ohanterat fel: Syntaxfel, okänt uttryck: div[id=sku_bu/ndle]*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
