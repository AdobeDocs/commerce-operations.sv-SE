---
title: 'ACSD-56886: Den konfigurerbara produkten blir inte i lager när underordnade produkter inaktiveras'
description: Använd patchen ACSD-56886 för att åtgärda Adobe Commerce-problemet där den konfigurerbara produkten blir otillgänglig när produkter inaktiveras.
feature: Products
role: Admin, Developer
exl-id: 5e9c1fd4-b56a-42c0-83e7-75e868213124
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-56886: Den konfigurerbara produkten blir inte i lager när underordnade produkter inaktiveras

Korrigeringen ACSD-56886 åtgärdar ett problem där den konfigurerbara produkten inte finns i lager när underordnade produkter inaktiveras. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.45 har installerats. Korrigerings-ID är ACSD-56886. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Den konfigurerbara produkten blir inte i lager när underordnade produkter inaktiveras.

<u>Steg som ska återskapas</u>:

1. Logga in som administratör.
1. Ange alla indexerare i läget **[!UICONTROL Update By Schedule]**.
1. Skapa följande konfigurerbara produkt:

   * Namn = *TEST KONFIGURABLE 1*
   * Attribut = *färg*
   * Värden = *röd* och *svart*
   * Priset för den **röda** underordnade produkten = *$100*;
   * Priset för den svarta underordnade produkten = *$200*.

1. Skapa följande schemalagda uppdatering för den konfigurerbara produkten:

   * Startdatum = *3* minuter från och med nu.
   * Slutdatum = *5* minuter efter startdatum.
   * Produktnamn = *TEST CONFIGURABLE 1 edited*.
   * Inaktivera den underordnade **röda**-produkten i avsnittet **Konfigurerbar**.

1. Vänta på startdatumet.
1. Öppna den konfigurerbara produktinformationen på Storefront.

<u>Förväntade resultat</u>:

Den konfigurerbara produkten visas som **I Stock** med etiketten **Så lite som 200** .

<u>Faktiska resultat</u>:

Den konfigurerbara produkten visas som **Utanför lager**.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
