---
title: 'MDVA-38666: Administratörsanvändaren kan inte ändra konfigurerbara produktalternativ'
description: MDVA-38666-korrigeringen löser problemet där administratörsanvändaren inte kan ändra konfigurerbara produktalternativ i kundvagnen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 är installerat. Patch-ID:t är MDVA-38666. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: Admin Workspace, Configuration, Products
role: Admin
source-git-commit: 7f17f1b286f635b8f65ac877e9de5f1d1a6a6461
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-38666: Administratörsanvändaren kan inte ändra konfigurerbara produktalternativ

MDVA-38666-korrigeringen löser problemet där administratörsanvändaren inte kan ändra konfigurerbara produktalternativ i kundvagnen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.9 har installerats. Patch-ID:t är MDVA-38666. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.3.4-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.2 - 2.3.5-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratörsanvändaren kan inte ändra de konfigurerbara produktalternativen i kundvagnen.

<u>Steg som ska återskapas</u>:

1. Ange kundkontots omfång till Global.
1. Skapa två webbplatser med butiker.
1. Skapa två konfigurerbara produkter och tilldela dem till varje webbplats.
1. Skapa ett kundkonto i förgrunden och logga in.
1. Lägg en produkt i kundvagnen och gör en utcheckning (detta görs för att göra offert-ID olika på varje webbplats).
1. Lägg en produkt i kundvagnen och lämna den.
1. Byt till den andra webbplatsen och lägg till produkten i kundvagnen (samma inloggning ska fungera eftersom kundkontots omfång är Global).
1. Öppna kunden från administratören och gå till kundvagnsfliken.
1. Växla butik från listrutan och försök ändra konfigurationen.

<u>Förväntade resultat</u>:

Användaren får en popup med konfigurerbara alternativ.

<u>Faktiska resultat</u>:

Inget popup-formulär visas. Användaren kan inte ändra konfigurationen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
