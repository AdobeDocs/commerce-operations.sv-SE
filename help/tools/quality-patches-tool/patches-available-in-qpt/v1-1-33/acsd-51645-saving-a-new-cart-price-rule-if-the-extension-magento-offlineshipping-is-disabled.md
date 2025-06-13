---
title: 'ACSD-51645: Spara en ny kundprisregel om tillägget Magento_OfflineShipping är inaktiverat'
description: Använd patchen ACSD-51645 för att åtgärda Adobe Commerce-problemet när ett fel inträffar när en ny kundprisregel sparas om tillägget Magento_OfflineShipping är inaktiverat.
exl-id: ce747ae4-6d2f-41c0-ba75-7da72be359c7
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 0%

---

# ACSD-51645: Spara en ny kundprisregel om tillägget Magento_OfflineShipping är inaktiverat

Korrigeringen ACSD-51645 åtgärdar ett problem där ett fel inträffar när en ny kundprisregel sparas om tillägget Magento_OfflineShipping är inaktiverat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.33 är installerad. Korrigerings-ID är ACSD-51645. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett fel uppstod när en ny kundprisregel skulle sparas om tillägget `Magento_OfflineShipping` är inaktiverat.

<u>Steg som ska återskapas</u>:

1. Inaktivera modulen `Magento_OfflineShipping`.
1. Logga in på **Admin**.
1. Gå till **[!UICONTROL Marketing]** > **[!UICONTROL Cart Price Rules]**.
1. Skapa en ny **[!UICONTROL Cart Price Rule]**.
1. Fyll i obligatoriska fält.
1. Spara **[!UICONTROL Cart Price Rule]**.

<u>Förväntade resultat</u>:

Kundprisregeln har sparats.

<u>Faktiska resultat</u>:

Följande fel inträffar:
`report.ERROR: Warning: Undefined array key "simple_free_shipping" in app/code/Magento/SalesRule/Controller/Adminhtml/Promo/Quote/Save.php on line 67 [] []`

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](<https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html>) i [!DNL Quality Patches Tool]-handboken.
