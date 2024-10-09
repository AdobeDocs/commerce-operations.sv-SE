---
title: "ACSD-60632: Adressen har sparats vid varje orderförsök"
description: Använd patchen ACSD-60632 för att åtgärda Adobe Commerce-problemet där en ny adress sparas med varje orderplaceringsförsök, oavsett om ordern har skapats eller inte.
feature: Orders, Products
role: Admin, Developer
source-git-commit: d68d6f7501e7dd6faf36f8506d1b0aab028eed58
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 0%

---

# ACSD-60632: Adressen har sparats vid varje orderförsök

Korrigeringen ACSD-60632 åtgärdar ett problem där en ny adress sparas vid varje orderplaceringsförsök, oavsett om ordern har skapats eller inte. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.51 är installerad. Korrigerings-ID är ACSD-60632. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p8 - 2.4.7-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Varje gång en order placeras sparas en ny adresspost i systemet, oavsett om ordern har skapats eller inte.

<u>Steg som ska återskapas</u>:

1. Aktivera betalningsmetod **[!DNL PayPal Payflow Link]**:
   * På en lokal dator kan systemet inte ta emot API-anrop från [!DNL PayPal Payflow Link] utan en verklig IP.
1. Skapa en enkel produkt.
1. Skapa en registrerad kund utan adress.
1. Lägg produkten i kundvagnen.
1. Gå till kassan.
1. Fyll i adressen. Kontrollera att den första adressen skapas i det här steget.
1. Markera alternativknappen **[!UICONTROL Credit Card (Payflow Link)]** på sidan *[!UICONTROL Review and Payments]*.
1. Klicka på **[!UICONTROL Continue]**:
   * Utcheckningssidan återgår till steget *[!UICONTROL Review and Payments]* med den ifyllda adressen och det förväntade felmeddelandet.
1. Välj alternativknappen *[!UICONTROL Credit Card (Payflow Link)]* igen.
1. Klicka på **[!UICONTROL Continue]**.

<u>Förväntade resultat</u>:

Ingen ny adress skapas för det andra orderplaceringsförsöket.

<u>Faktiska resultat</u>:

En ny adress skapas efter varje försök till orderplacering.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
