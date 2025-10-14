---
title: 'ACSD-53414: Begränsade administratörsanvändare kan visa CMS-sidor utanför sitt behörighetsområde'
description: Använd patchen ACSD-53414 för att åtgärda Adobe Commerce-problemet där en begränsad administratörsanvändare kan se CMS-sidor utanför sitt behörighetsområde.
feature: CMS
role: Admin, Developer
exl-id: 86658336-679b-4fe0-9d26-56064ff0c604
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---

# ACSD-53414: Begränsade administratörsanvändare kan visa CMS-sidor utanför sitt behörighetsområde

Korrigeringen ACSD-53414 åtgärdar ett problem där en begränsad administratörsanvändare kan se CMS-sidor utanför sitt behörighetsområde. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.40 har installerats. Korrigerings-ID är ACSD-53414. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Begränsade administratörsanvändare kan se CMS-sidor utanför sitt behörighetsområde.

<u>Steg som ska återskapas</u>:

1. Skapa en ny webbplats (sub_website), butik (sub_store) och storeview (sub_storeview).
1. Skapa en sub_expert-roll som tillåter omfattningen av sub_website och sub_store. Tilldela endast följande behörigheter: [!UICONTROL Dashboard] och [!UICONTROL Pages].
1. Skapa en ny administratörsanvändare och tilldela den till rollen sub_expert.
1. Tilldela följande CSM-sidor till sub_storeview och standardlagergranskning.

   * [!UICONTROL 404 Not Found] > Undergranskning
   * [!UICONTROL 503 Service Unavailable] > Standardbutiksgranskning

1. Logga in på administratören med den administratörsanvändare som skapades i steg 3.
1. Kontrollera CMS sidstödraster.

<u>Förväntade resultat</u>:

Sidan *[!UICONTROL 503 Service Unavailable]* visas inte för webbadministratören.

<u>Faktiska resultat</u>:

*[!UICONTROL 503 Service Unavailable]* visas för webbadministratören.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
