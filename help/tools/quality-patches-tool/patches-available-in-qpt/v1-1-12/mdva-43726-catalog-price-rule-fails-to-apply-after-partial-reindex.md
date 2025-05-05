---
title: 'MDVA-43726: Katalogprisregeln kan inte tillämpas efter partiell omindexering'
description: MDVA-43726-korrigeringen åtgärdar ett problem där katalogprisregeln som baseras på butiksattributmatchning inte kan tillämpas efter partiell omindexering. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 är installerat. Korrigerings-ID är MDVA-43726. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: Catalog Management, Categories, Orders, Price Rules
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# MDVA-43726: Katalogprisregeln kan inte tillämpas efter partiell omindexering

MDVA-43726-korrigeringen åtgärdar ett problem där katalogprisregeln som baseras på butiksattributmatchning inte kan tillämpas efter partiell omindexering. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.12 är installerat. Korrigerings-ID är MDVA-43726. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.3 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Katalogprisregeln som baseras på matchning av butiksattribut kan inte tillämpas efter partiell omindexering.

<u>Steg som ska återskapas</u>:

1. Ställ in indexeringsläget så att det körs enligt schema.
1. Skapa två konfigurerbara produktattribut. Exempel: Färg (visuell färgruta) och Storlek (färgruta).
1. Skapa en konfigurerbar produkt med båda attributen som skapas i steg 2.
1. När du har skapat produkterna skapar du ett **Ja/Nej**-typattribut och gör det synligt i regelvillkoren.
1. Lägg till det här attributet i standardattributuppsättningen.
1. Skapa en katalogprisregel som ska användas när det här attributet är inställt på **Ja**.
1. Öppna en av de enkla produkterna som hör till den konfigurerbara produkten.
1. Ändra omfattningen för att lagra vyn och uppdatera attributvärdet till **Ja**.
1. Kör `CRON` och kontrollera priset på frontend.
1. Kör en fullständig omindexering. Kontrollera priset på fronten igen.
1. Uppdatera den konfigurerbara produktkategorin.
1. Kör `CRON` och kontrollera priset igen på frontend.

<u>Förväntade resultat</u>:

Katalogregeln tillämpas korrekt utan en fullständig omindexering med inkrementella indexerare.

<u>Faktiska resultat</u>:

Katalogregeln gäller inte utan att du behöver köra ett fullständigt omindex.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
