---
title: 'ACSD-62146: Den valda faktureringsadressen försvinner på betalningssidan för utcheckning'
description: Använd korrigeringsfilen ACSD-62146 för att åtgärda Adobe Commerce-problemet där den valda faktureringsadressen försvinner på betalningssidan när adresssökning är aktiverad och begränsningen för antal kundadresser är inställd på 1.
feature: Customers, Checkout
role: Admin, Developer
type: Troubleshooting
source-git-commit: 3de3de80383372d0e3bec5485fd65b9d70fe8860
workflow-type: tm+mt
source-wordcount: '382'
ht-degree: 0%

---


# ACSD-62146: Den valda faktureringsadressen försvinner på betalningssidan för utcheckning

Korrigeringen ACSD-62146 åtgärdar ett problem där den valda faktureringsadressen försvinner på betalningssidan när adresssökning är aktiverad och [!UICONTROL Number of Customer Addresses Limit] är inställd på 1. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 har installerats. Korrigerings-ID är ACSD-62146. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Den valda faktureringsadressen försvinner på betalningssidan för utcheckning när adresssökning är aktiverat och **[!UICONTROL Number of Customer Addresses Limit]** är inställd på 1.

<u>Steg som ska återskapas</u>:

1. Om du vill aktivera adresssökning går du till **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Checkout]** > **[!UICONTROL Checkout Options]**.
1. Ange **[!UICONTROL Number of Customer Addresses Limit]** till 1.
1. Skapa en kund och lägg till två olika adresser.
1. Lägg en produkt i kundvagnen och fortsätt till kassan.
1. Klicka på **[!UICONTROL Change Address]** och använd popup-menyn för att ändra adressen.
1. Välj Adress 2 som leveransadress.
1. Klicka på **[!UICONTROL Next]** för att fortsätta till betalningssteget.
1. Kontrollera att fakturerings- och leveransadressen är samma.
1. Uppdatera sidan utan att göra betalningen.

<u>Förväntade resultat</u>:

Leveransadressen visas när fakturerings- och leveransadresserna är desamma.

<u>Faktiska resultat</u>:

Standardfaktureringsadressen och den valda leveransadressen visas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
