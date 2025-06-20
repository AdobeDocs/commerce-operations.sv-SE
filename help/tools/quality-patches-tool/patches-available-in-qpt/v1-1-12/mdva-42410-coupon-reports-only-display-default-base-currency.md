---
title: 'MDVA-42410: Kuponrapporter visar endast standardbasvalutan'
description: MDVA-42410-korrigeringen åtgärdar ett problem där kupongen bara visar basvalutan. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 är installerat. Korrigerings-ID är MDVA-42410. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: Orders
role: Admin
exl-id: 97b4d9cf-12fd-4659-ad71-914c8422da37
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# MDVA-42410: Kuponrapporter visar endast standardbasvalutan

MDVA-42410-korrigeringen åtgärdar ett problem där kupongen bara visar basvalutan. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.12 är installerat. Korrigerings-ID är MDVA-42410. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.0 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

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
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
