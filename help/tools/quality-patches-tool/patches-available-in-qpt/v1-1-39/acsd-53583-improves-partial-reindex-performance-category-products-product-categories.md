---
title: 'ACSD-53583: Förbättra prestanda för partiell omindexering för [!UICONTROL Category Products] och [!UICONTROL Product Categories] indexerare'
description: Använd patchen ACSD-53585 för att förbättra prestandan för partiell omindexering för kategoriprodukter och produktkategoriindexerare.
feature: Products, Categories
role: Admin, Developer
exl-id: 11e60cc2-1f7e-4e4a-a5eb-0f1dbe399ef2
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# ACSD-53583: Förbättra partiell indexering för indexerare för kategoriprodukter och produktkategorier

Korrigeringen ACSD-53583 förbättrar prestandan för partiell omindexering för indexerare för *Kategoriprodukter* och *produktkategorier*. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.39 har installerats. Korrigerings-ID är ACSD-53583. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p3
* Inte kompatibel med modulen [!DNL Live Search]. Om du vill tillämpa den här korrigeringen på installationen av [!DNL Live Search] måste du begära en extra ACSD-55719-korrigering.

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ofullständig indexering tar längre tid än fullständig indexering.

<u>Steg som ska återskapas</u>:

1. Vrid alla indexerare till *Uppdatera enligt schema*.
1. Generera data med [!DNL Performance Toolkit] (medelprofil).
1. Gör ändringar i alla produkter och kategorier så att de ligger i indexeftersläpningen och alla index är inaktiva.
1. Utför partiell omindexering för indexerare för *Kategoriprodukter* och *produktkategorier*.

<u>Förväntade resultat</u>:

Ofullständig indexering anropas en gång per produkt och tar nästan samma tid som en fullständig indexering eftersom alla produkter och kategorier har ändrats.

<u>Faktiska resultat</u>:

Partiell omindexering anropas många gånger per produkt och tar längre tid än fullständig omindexering.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
