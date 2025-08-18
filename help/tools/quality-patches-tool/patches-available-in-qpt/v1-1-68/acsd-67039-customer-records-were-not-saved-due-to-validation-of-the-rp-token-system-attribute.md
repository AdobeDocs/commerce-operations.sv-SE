---
title: 'ACSD-67039: Kundposter sparades inte på grund av systemattributsvalidering för rp_token'
description: Använd patchen ACSD-67039 för att åtgärda Adobe Commerce-problemet där kodningsdiakritiska tecken orsakar valideringsavbrott för rp_token.
feature: Customers, Admin Workspace
role: Admin, Developer
type: Troubleshooting
exl-id: e5995e28-b6b5-4955-a52a-895842c6b6e8
source-git-commit: 17c35f6da57440c2704879309a58c46b2c4eea25
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 0%

---

# ACSD-67039: Kundposter sparades inte på grund av `rp_token` systemattributsvalidering

Korrigeringen ACSD-67039 åtgärdar ett problem där kundposter inte sparades på grund av valideringen av systemattributet `rp_token` och diakritikvalidering tillämpades bara på den resulterande kundens e-post. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 har installerats. Korrigerings-ID är ACSD-67039. Observera att detta problem har åtgärdats i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p9

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p9 - 2.4.6-p11

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kodningsdiakritiska tecken orsakar valideringsfel på `rp_token`, som inte ingår i valideringen. Diakritiska tecken tillåts bara för e-postadresser, som det är tänkt.

<u>Steg som ska återskapas</u>:

1. Installera Adobe Commerce 2.4.4-versionen.
1. Skapa en kund.
1. Uppgradera Adobe Commerce till version 2.4.6 från version 2.4.4 där kunden redan är skapad.
1. Ange krypteringsnyckeln till `env.php` =
   *d337b914e91ff703b1e94ba4156aadf0*
1. Ange värdena nedan i databasen för alla kunder i tabellen `customer_entity`:
*`rp_token` = *incr4869*
*`rp_token_created_at` = *2021-04-29 20:06:14*
1. Gå till **[!UICONTROL Customers]** > **[!UICONTROL All Customers]** på Admin-panelen.
1. Redigera kunden som du just uppdaterade värdena för ovan.
1. Klicka på **[!UICONTROL Save Customer]** eller **[!UICONTROL Save and Continue Edit]**.

<u>Förväntade resultat</u>:

Kundvärdena har sparats.

<u>Faktiska resultat</u>:

Kundposten har inte sparats och administratörsanvändaren ser felmeddelandet *Något gick fel när kunden sparades.*
`system.log` innehåller följande fel:

```
report.CRITICAL: Exception message: Notice: iconv(): Detected an incomplete multibyte character in input string in /vendor/magento/module-eav/Model/Attribute/Data/Text.php on line 190
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool]
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden för Commerce om molninfrastruktur

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken
