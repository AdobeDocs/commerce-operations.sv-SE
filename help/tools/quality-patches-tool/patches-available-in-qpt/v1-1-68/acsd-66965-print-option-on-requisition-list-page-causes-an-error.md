---
title: 'ACSD-66965: Alternativet [!UICONTROL Print] på sidan [!UICONTROL Requisition List] orsakar ett fel'
description: Använd korrigeringsfilen ACSD-66965 för att åtgärda ett problem i Adobe Commerce där alternativet [!UICONTROL Print] på sidan [!UICONTROL Requisition List] orsakar ett fel.
feature: B2B
role: Admin, Developer
type: Troubleshooting
source-git-commit: 7682a326a6c703a08dd6d0fac5319ac38e1bc3c8
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---


# ACSD-66965: Alternativet **[!UICONTROL Print]** på sidan **[!UICONTROL Requisition List]** orsakar ett fel

Korrigeringen ACSD-66965 åtgärdar ett problem där alternativet **[!UICONTROL Print]** på sidan **[!UICONTROL Requisition List]** orsakar ett fel. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 har installerats. Korrigerings-ID är ACSD-66965. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3 - 2.4.8-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Alternativet **[!UICONTROL Print]** på sidan **[!UICONTROL Requisition List]** orsakar ett fel på grund av en objektreferens som är null i `Grid.php`.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL B2B Features]**.
1. Ange **[!UICONTROL Enable Company]**, **[!UICONTROL Enable Shared Catalog]** och **[!UICONTROL Enable Requisition List]** till `Yes`.
1. Skapa två enkla produkter.
1. Logga in i butiken och öppna sidan **[!UICONTROL My Account]**.
1. Skapa en rekvisitionslista.
1. Tilldela båda produkterna till rekvisitionslistan.
1. Gå till rekvisitionslistan och visa produkterna.
1. Klicka på **[!UICONTROL Print]**.

<u>Förväntade resultat</u>:

Alternativet **[!UICONTROL Print]** på sidan **[!UICONTROL Requisition List]** visar förhandsvisningen utan fel.

<u>Faktiska resultat</u>:

Följande felmeddelande visas: *Ett fel uppstod när programmet kördes. Mer information finns i undantagsloggen.*

```
Call to a member function setCollection() on null in /vendor/magento/module-requisition-list/Block/Requisition/View/Items/Grid.php:146
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
