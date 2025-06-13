---
title: 'ACSD-46767: [!UICONTROL Category]-sidans cachning blir ogiltig när lagerkvantiteten ändras'
description: Använd korrigeringsfilen ACSD-46767 för att åtgärda Adobe Commerce-problemet där sidan [!UICONTROL Category] cache-lagring gör ogiltig när lagerkvantiteten ändras, även om produkten fortfarande finns i lager.
feature: Cache, Products, Inventory
role: Admin, Developer
exl-id: 5872dca7-fdef-47ad-8718-bf343cd3a42a
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# ACSD-46767: [!UICONTROL Category]-sidans cachning blir ogiltig när lagerkvantiteten ändras

Korrigeringen ACSD-46767 åtgärdar ett problem där sidan [!UICONTROL Category] cachelagras som ogiltig när lagerkvantiteten ändras, även om produkten fortfarande finns i lager. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.46 har installerats. Korrigerings-ID är ACSD-46767. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5-p5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

[!UICONTROL Category] sidor cachas när lagerkvantiteten ändras.

<u>Steg som ska återskapas</u>:

1. Skapa några produkter och lägg till dem i samma kategori.
1. Öppna sidan *[!UICONTROL Category]* i butiken för att se till att sidan är cachelagrad.
1. Lägg beställningen med en av produkterna i kategorin *(produktkvantiteten har ändrats, men produkten finns fortfarande i lager)*.
1. Öppna sidan [!UICONTROL Category] i butiken igen.

<u>Faktiska resultat</u>:

Sidan läses inte in från cachen. Den återskapas.

<u>Förväntade resultat</u>:

Sidan läses in från cachen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
