---
title: 'ACSD-52202: Standardvärdet för lagersaldokvantitet ändras till 0 om standardvärdet för lagersaldo är 0.'
description: Använd patchen ACSD-52202 för att åtgärda Adobe Commerce-problemet där standardkvantiteten för lagerförsäljning ändras till 0 om standardvärdet för lagersaldo är 0.
feature: Inventory, Products
role: Admin
exl-id: 2ba5cc3b-9774-49f6-948f-371ab3c0c9df
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '420'
ht-degree: 0%

---

# ACSD-52202: Standardvärdet för lagerförsäljningsvärde ändras till 0 om icke-standardlagervärdet är 0 i en order

Korrigeringen ACSD-52202 åtgärdar ett problem där en standardkvantitet (kvantitet) för lagerförsäljning ändras till 0 om icke-standardlager ställs in på 0 i en order. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.35 har installerats. Korrigerings-ID är ACSD-52202. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Standardlagerförsäljningsvärdet ändras till 0 om icke-standardlagervärdet är 0 i en order.

<u>Steg som ska återskapas</u>:

1. Logga in på [!DNL Admin].
1. Skapa **webbplats2**.
1. Skapa anpassad **källa2**.
1. Skapa anpassad **stock2**.
1. Tilldela **source2** och **stock2** till **website1** och standardkällan och standardresursen till standardwebbplatsen.
1. Skapa en enkel produkt och tilldela **kvantitet** = *10* som standardkälla och **kvantitet** = *1* för **källa2** -källan.
1. Placera en order med **kvantitet** = *1* för **webbplats2**.
1. Skapa en faktura och en leverans.
1. Kontrollera den enkla produkten **försäljningsbar kvantitet**.

<u>Förväntade resultat</u>:

Den **försäljningsbara kvantiteten** = *10* för **källa2**.

<u>Faktiska resultat</u>:

Den **försäljningsbara kvantiteten** = *0* för båda källorna.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
