---
title: 'ACSD-51204: Produkten returneras inte i lager när kreditnotan har skapats'
description: Använd korrigeringsfilen ACSD-51204 för att åtgärda problemet med Adobe Commerce där produkten inte finns i lager när kreditnotan har skapats.
feature: Orders, Products, Returns
role: Admin
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-51204: Produkten returneras inte i lager när kreditnotan har skapats

Korrigeringen ACSD-51204 åtgärdar ett problem där produkten inte återgår i lager efter att kreditnotan har skapats. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.32 är installerad. Korrigerings-ID är ACSD-51204. Observera att problemet har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Den utsålda produkten returneras inte i lager när kreditnotan har skapats.

<u>Steg som ska återskapas</u>:

1. Installera **[!UICONTROL Adobe Commerce]** och aktivera endast **[!UICONTROL Inventory Management Module]** med standardkällan ** och *stock*.
1. Lägg till en **[!UICONTROL new product]** med kvantiteten *10*.
1. Tilldela produkten till **[!UICONTROL default stock]**.
1. Lägg produkten i varukorgen i butiken och beställ 10 för hela den tillgängliga kvantiteten.
1. Generera en *faktura* och *leverans* för ordern på administratörspanelen.
1. Skapa en **[!UICONTROL Credit Memo]** med kryssrutan *återgå till lager* markerad för alla objekt.
1. Kontrollera produktens **[!UICONTROL Salable Quantity]** i Admin.

<u>Förväntade resultat</u>:

Produktens försäljningsbara kvantitet måste återgå till *10*.

<u>Faktiska resultat</u>:

Produktens försäljningsbara kvantitet lämnas som *0*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](<https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html>) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) i [!DNL Quality Patches Tool]-handboken.
