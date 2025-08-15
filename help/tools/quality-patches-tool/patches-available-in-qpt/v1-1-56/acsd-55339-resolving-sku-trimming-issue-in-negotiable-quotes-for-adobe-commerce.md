---
title: 'ACSD-55339: Löser SKU-trimningsproblem i överlåtbara offerter för Adobe Commerce'
description: Använd patchen ACSD-55339 för att åtgärda Adobe Commerce-problemet där produkter-SKU:er med inledande nollor trimmas, vilket ger upphov till förhandlingsfel.
feature: B2B, Quotes
role: Admin, Developer
exl-id: 7a9f92df-fb3e-4723-b731-155c6c4fc431
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---

# ACSD-55339: Löser SKU-trimningsproblem i överlåtbara offerter för Adobe Commerce

Korrigeringen ACSD-55339 åtgärdar ett problem där SKU:er med inledande nollor trimmas, vilket resulterar i fel under förhandlingsprocessen. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.56 har installerats. Korrigerings-ID är ACSD-55339. Observera att problemet är planerat att åtgärdas i Adobe Commerce B2B 1.5.0.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Numeriska SKU:er med inledande nollor trimmas när de används i överlåtbara offerter, vilket resulterar i fel som förhindrar uppdatering av kvantiteter eller prissättning.

<u>Steg som ska återskapas</u>:

1. Navigera till avsnittet för att skapa produkten på administratörspanelen.
1. Ange [!UICONTROL SKU] för produkten som 01910.
1. Logga in i butiken och utför följande åtgärder:
   1. Lägg produkten i kundvagnen.
   1. Visa och redigera kundvagnen.
   1. Begär en offert.
1. Gå till [!UICONTROL admin] > [!UICONTROL Quote] > [!UICONTROL View] och [!UICONTROL Add Products by SKU] - 1910.

**Obs!** SKU:n visas som *1910* i stället för som *01910*. Denna diskrepans förhindrar användaren från att uppdatera kvantiteten eller ange priser, eftersom det inte finns någon produkt med SKU 1910 i katalogen.

<u>Förväntade resultat</u>:

Den överlåtbara offerten ska uppdateras utan fel.

<u>Faktiska resultat</u>:

Ett varningsmeddelande visas som anger att produkten inte finns.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
