---
title: 'MDVA-42410: Kuponrapporter visar endast standardbasvaluta'
description: MDVA-42410-korrigeringen åtgärdar ett problem där kupongen bara visar basvalutan. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 är installerat. Korrigerings-ID är MDVA-42410. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-42410: Kuponrapporter visar endast standardbasvalutan

MDVA-42410-korrigeringen åtgärdar ett problem där kupongen bara visar basvalutan. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 är installerat. Korrigerings-ID är MDVA-42410. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kupongrapporter visar endast standardbasvalutan.

<u>Steg som ska återskapas</u>:

1. Skapa ytterligare en webbplats-, butik- och butiksvy.
1. Ange en annan valuta för den nya webbplatsen. Till exempel euro.
1. Gå till **Store** > **Valutakurser** och konfigurera valutakurser till **Euro**.
1. Skapa en **kundvagnsprisregel** med en viss kupong - **Test**.
1. Gå till fronten och lägg en order med kupongen **Test** på den nya webbplatsen.
1. Gå till **Rapporter** > **Försäljning** > **Kuponger**.
1. Välj den nya webbplatsen i listrutan Omfång.
1. Uppdatera statistik och kör rapporter.

<u>Förväntade resultat</u>:

Kupongrapporter visar den nya webbplatsens valuta som euro.

<u>Faktiska resultat</u>:

Standardbasvalutan (USD i det här fallet) används i kupongrapporter för den nya webbplatsen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
