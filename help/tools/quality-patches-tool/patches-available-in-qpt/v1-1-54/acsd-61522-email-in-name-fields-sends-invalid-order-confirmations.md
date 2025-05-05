---
title: "ACSD-61522: E-postadresser i fälten *Förnamn och Efternamn* skickar ogiltiga orderbekräftelser"
description: Använd korrigeringsfilen ACSD-61522 för att åtgärda Adobe Commerce-problemet där det går att ange e-postadresser i en gästkunds fält *[!UICONTROL First Name]* och *[!UICONTROL Last Name]*, vilket leder till att ogiltiga orderbekräftelsemeddelanden skickas.
feature: Checkout, Customers
role: Admin, Developer
source-git-commit: d56f4fda007c1499bdba82ac3db9ac5ea1d34b0e
workflow-type: tm+mt
source-wordcount: '361'
ht-degree: 0%

---


# ACSD-61522: E-postadresser i fälten *Förnamn och Efternamn* skickar ogiltiga orderbekräftelser

Korrigeringen ACSD-61522 åtgärdar ett problem där det går att ange e-postadresser i en gästkunds *[!UICONTROL First Name]*- och *[!UICONTROL Last Name]*-fält, vilket leder till att ogiltiga e-postmeddelanden med orderbekräftelse skickas. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.54 har installerats. Korrigerings-ID är ACSD-61522. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p9

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Systemet tillåter att e-postadresser anges i en gästkunds *[!UICONTROL First Name]*- och *[!UICONTROL Last Name]*-fält, vilket resulterar i att ogiltiga orderbekräftelsemeddelanden skickas.

<u>Steg som ska återskapas</u>:

1. Lägg valfri produkt i kundvagnen som gästkund.
1. Gå till **[!UICONTROL Checkout]**.
1. Fyll i fältet *[!UICONTROL Email Address]* med *test1@example.com*.
1. Fyll fältet *[!UICONTROL First Name]* med *<test2@example.com>*.
1. Fyll *[!UICONTROL Last Name]* med *<test3@example.com>*.
1. Fyll i andra obligatoriska fält.
1. Beställ.

<u>Förväntade resultat</u>:

E-postadresser kan inte användas i fälten *[!UICONTROL First Name]* och *[!UICONTROL Last Name]*.

<u>Faktiska resultat</u>:

1. Ordern placeras.
1. *[!UICONTROL First Name]* och *[!UICONTROL Last Name]* fält sparas som de anges.
1. E-postmeddelanden med orderbekräftelse skickas till alla tre e-postmeddelandena.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
