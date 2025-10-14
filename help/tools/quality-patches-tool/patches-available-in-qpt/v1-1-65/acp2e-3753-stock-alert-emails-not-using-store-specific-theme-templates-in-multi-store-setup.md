---
title: 'ACP2E-3753: Stock-varningsmeddelanden som inte använder butiksspecifika temamallar vid konfiguration av flera butiker'
description: Använd programfixen ACP2E-3753 för att åtgärda Adobe Commerce-problemet där produktvarningsmeddelanden i en konfiguration för flera butiker alltid skickas med standardtemat, oavsett butiks- eller temakonfiguration.
feature: Themes, Personalization
role: Admin, Developer
exl-id: ad44ffdd-f122-4119-83e3-1816951b662c
source-git-commit: 2089fed83a207f9d0211273652ea320d2590f8d5
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---

# ACP2E-3753: Stock-varningsmeddelanden som inte använder butiksspecifika temamallar vid konfiguration av flera butiker

Programfixen ACP2E-3753 åtgärdar ett problem där produktvarningsmeddelanden i en konfiguration med flera butiker alltid skickades med standardtemat, oavsett butiks- eller temakonfiguration. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.65 har installerats. Korrigerings-ID är ACP2E-3753. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p11

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produktvarningsmeddelanden skickas alltid med standardtemat, oavsett butiks- eller temakonfiguration.

<u>Steg som ska återskapas</u>:

1. Skapa två webbplatser, butiker och butiksvyer.
1. Skapa två olika teman och tilldela dem till olika butiker.
1. Produktvarningsinställningen är standardomfånget som körs varje minut.
1. Åsidosätt/lägg till innehåll i filen `stock.phtml` för båda temana. Exempel på filplats:

   ```
   app\design\frontend\Adobe\Taiwan\Magento_ProductAlert\templates\email\stock.phtml
   app\design\frontend\Adobe\Japan\Magento_ProductAlert\templates\email\stock.phtml
   ```

1. Skapa en användare för varje butik och prenumerera på varningen om produktlager.
1. Utlös varningen om produktlager för att skicka e-postmeddelanden.

<u>Förväntade resultat</u>:

E-postmeddelandet bör innehålla ändringar på temanivå.

<u>Faktiska resultat</u>:

E-postmeddelandena innehåller inte de mallar som angetts för respektive webbplats/butik.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
