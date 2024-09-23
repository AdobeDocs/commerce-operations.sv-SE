---
title: 'MDVA-40175: Alternativknappar visas inte vid omordning'
description: MDVA-40175-korrigeringen löser problemet där alternativknapparna inte visas när användaren försöker ändra ordningen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 är installerat. Korrigerings-ID är MDVA-40175. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.
feature: Admin Workspace, Orders
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# MDVA-40175: Alternativknappar visas inte när ordningen ändras

MDVA-40175-korrigeringen löser problemet där alternativknapparna inte visas när användaren försöker ändra ordningen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.10 är installerat. Korrigerings-ID är MDVA-40175. Observera att problemet har åtgärdats i Adobe Commerce 2.4.3.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Alternativknappar visas inte i avsnittet Betalnings- och leveransinformation när användare försöker beställa om.

<u>Förutsättningar</u>:

1. Ett kundkonto med en leveransadress och en faktureringsadress skapas.
1. En enkel produkt skapas.
1. Flera leveransmetoder har konfigurerats.
1. Minst en order skapas.

<u>Steg som ska återskapas</u>:

1. Gå till panelen Admin > **Försäljning** > **Beställningar**.
1. Markera den skapade ordern.
1. Klicka på länken **Visa**.
1. Klicka på knappen **Ändra ordning**.
1. Bläddra nedåt på sidan till avsnittet **Betalnings- och leveransinformation**.
1. Klicka på **Klicka för att ändra leveransmetod**.

<u>Förväntade resultat</u>:

Listan med leveransmetoder med alternativknappar visas.

<u>Faktiska resultat</u>:

Listan med leveransmetoder utan alternativknappar visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
