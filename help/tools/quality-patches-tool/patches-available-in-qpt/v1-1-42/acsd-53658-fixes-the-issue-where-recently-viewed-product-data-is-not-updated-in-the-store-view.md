---
title: 'ACSD-53658: **[!UICONTROL Recently Viewed Product]** data har inte uppdaterats korrekt i butiksvyn'
description: Använd korrigeringsfilen ACSD-53658 för att åtgärda Adobe Commerce-problemet där **[!UICONTROL Recently Viewed Product]**-data inte uppdateras korrekt i butiksvyn.
feature: CMS, Personalization
role: Admin, Developer
exl-id: a91fac3d-cb6f-4f65-aec2-d28cee4fd39f
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '374'
ht-degree: 0%

---

# ACSD-53658: **[!UICONTROL Recently Viewed Product]**-data har inte uppdaterats korrekt i butiksvyn

ACSD-53658-korrigeringen åtgärdar ett problem där **[!UICONTROL Recently Viewed Product]**-data inte uppdateras korrekt i butiksvyn. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42 är installerad. Korrigerings-ID är ACSD-53658. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

**[!UICONTROL Recently Viewed Product]**-data har inte uppdaterats korrekt i butiksvyn.

<u>Steg som ska återskapas</u>:

1. Logga in på panelen Admin.
1. Skapa en andra butiksvy för standardwebbplatsen.
1. Skapa en enkel produkt.
1. Ange ett annat produktnamn för den nya butiksvyn.
1. Skapa en **[!UICONTROL Recently Viewed Product]**-widget.
1. Konfigurera den här widgeten så att den visas på hemsidan.
1. Öppna produktsidan på Storefront från standardbutiksvyn.
1. Öppna hemsidan.
1. Växla till den andra butiksvyn genom att använda butiksväljaren.

<u>Förväntade resultat</u>:

Produktnamnet uppdateras i widgeten.

<u>Faktiska resultat</u>:

Produktnamnet uppdateras inte i widgeten.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
