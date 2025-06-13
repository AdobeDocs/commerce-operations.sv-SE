---
title: 'ACSD-43887: Felaktig information visas på betalningssidan för utcheckning'
description: Korrigeringen ACSD-43887 åtgärdar ett problem där felaktiga detaljer visas på betalningssidan för utcheckning när inköpsorder för företag är aktiverade. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 är installerat. Korrigerings-ID är ACSD-43887. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
feature: B2B, Checkout, Orders, Payments, User Account
role: Admin
exl-id: e150f093-9f1a-4ba5-bdcf-90e7f42a29c3
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# ACSD-43887: Felaktig information visas på betalningssidan för utcheckning

Korrigeringen ACSD-43887 åtgärdar ett problem där felaktiga detaljer visas på betalningssidan för utcheckning när inköpsorder för företag är aktiverade. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.17 är installerat. Korrigerings-ID är ACSD-43887. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Felaktiga detaljer visas på betalningssidan i kassan när inköpsorder för företag är aktiverade.

<u>Förutsättningar</u>:

1. B2B-moduler är installerade.
1. Aktivera företag är _Ja_. Gå till **Lagrar** > **Konfigurationer** > **Allmänt** > **B2B-funktioner** > **Aktivera företag** > **Ja**.
1. Aktivera inköpsorder är inställt på _Ja_. Gå till **Konfiguration för ordergodkännande** > **Aktivera inköpsorder** > **Ja**.
1. PayPal Express är konfigurerad som betalningsmetod.

<u>Steg som ska återskapas</u>:

1. Skapa en virtuell produkt.
1. Registrera ett företagskonto från frontend med en företagsadministratör.
1. Godkänn företagskontot från serverdelen och ställ in **Aktivera inköpsorder** som _Ja_ när du godkänner företaget.
1. Gå till förgrunden och logga in med det företagsadministratörskonto som skapades i steg två.
1. Skapa en standardanvändare för företaget. Gå till **Företagsanvändare** > **Lägg till ny användare**.
1. Skapa en godkännanderegel för företaget. Gå till **Godkännanderegler** > **Lägg till ny regel**.

   * Regeltyp: Ordersumma
   * Ordersumma: är större än eller lika med $1
   * Kräver godkännande från: Företagsadministratör

1. Logga ut och logga in med standardanvändarkontot.
1. Lägg den virtuella produkt som skapats i steg ett i kundvagnen och fortsätt till kassan.
1. Välj PayPal Express som betalningsmetod och klicka på **Placera inköpsorder**.
1. Logga ut och logga in med företagets administratörskonto.
1. Gå till **Mina inköpsorder** och från **Företagsinköpsorder** klickar du på **Visa** för den order som skapats i steg 9.
1. Godkänn inköpsordern. Inköpsorderstatusen ska vara&quot;Godkänd: Väntande betalning&quot;.
1. Logga ut och logga in med företagets standardanvändarkonto.
1. Gå till **Mina inköpsorder** > **Visa** > **Montera order**.
1. Kontrollera **ordersammanfattningen**.

<u>Förväntade resultat</u>:

Ordersammanfattningen visar korrekta värden som inte är noll.

<u>Faktiska resultat</u>:

Ordersammanfattningens totalvärde är noll.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
