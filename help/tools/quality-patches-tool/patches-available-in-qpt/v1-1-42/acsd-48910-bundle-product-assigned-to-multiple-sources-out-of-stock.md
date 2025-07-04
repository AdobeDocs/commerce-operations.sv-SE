---
title: 'ACSD-48910: Paketerad produkt som tilldelats flera källor lämnar lagret efter faktura och leverans'
description: Använd patchen ACSD-48910 för att åtgärda Adobe Commerce-problemet där den paketerade produkt som tilldelats flera källor går ut ur lagret efter att en order har fakturerats och skickats, även om den fortfarande har en kvantitet som inte är noll.
feature: Products, Inventory
role: Admin, Developer
exl-id: c8d86531-2db5-4115-92d5-a8d391c4f75d
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# ACSD-48910: Paketerad produkt som tilldelats flera källor lämnar lagret efter faktura och leverans

Korrigeringen ACSD-48910 åtgärdar ett problem där den paketerade produkt som tilldelats flera källor lämnar lagret efter att en order har fakturerats och skickats, även om den fortfarande har en kvantitet som inte är noll. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.42 är installerad. Korrigerings-ID är ACSD-48910. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.5-p5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Den paketerade produkt som tilldelats till flera källor går ut ur lagret efter fakturering och leverans, även om den fortfarande är tillgänglig.

<u>Steg som ska återskapas</u>:

1. Skapa två webbplatser.
1. Skapa två butiker/butiksvyer (en per webbplats).
1. Skapa två enkla produkter (kvantitet = 10) och tilldela dem till både lager och webbplatser.
1. Skapa en paketerad produkt och lägg till dessa enkla produkter i den. Tilldela den paketerade produkten till båda webbplatserna.
1. Gå till butiken och lägg den paketerade produkten i kundvagnen.
1. Checka ut och beställ.
1. Fakturera och skicka ordern från administratören.

<u>Förväntade resultat</u>:

Den paketerade produkten finns kvar i lager eftersom vi bara köpte 1 av 10 artiklar.

<u>Faktiska resultat</u>:

Den paketerade produkten ändrar sin status till en produkt som inte finns i lager.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
