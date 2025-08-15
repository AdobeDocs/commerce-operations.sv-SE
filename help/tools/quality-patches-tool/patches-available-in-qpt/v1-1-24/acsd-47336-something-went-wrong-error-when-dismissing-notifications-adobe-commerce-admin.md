---
title: 'ACSD-47336: [!UICONTROL Something went wrong]-fel vid inaktivering av meddelanden i Adobe Commerce Admin'
description: Använd ACSD-47336-korrigeringen för att åtgärda Adobe Commerce-problemet där användaren ser [!UICONTROL Something went wrong]-fel när meddelanden i  [!DNL Commerce] administratören stängs av.
feature: Admin Workspace
role: Admin
exl-id: da0c0119-6720-493f-a278-d573ed898a63
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '341'
ht-degree: 0%

---

# ACSD-47336: _[!UICONTROL Something went wrong]_-fel vid inaktivering av meddelanden i Adobe Commerce Admin

ACSD-47336-korrigeringen åtgärdar ett problem där användaren ser felet _[!UICONTROL Something went wrong]_&#x200B;när meddelanden i [!DNL Commerce]-administratören stängs av. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 har installerats. Korrigerings-ID är ACSD-47336. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder): 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder): 2.4.0 - 2.4.5-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Användaren ser _[!UICONTROL Something went wrong]_-fel när meddelanden i [!DNL Commerce]-administratören stängs av.

<u>Steg som ska återskapas</u>:

1. Utför en gruppåtgärd (t.ex. satsvis uppdatering av produktattribut från produktrutnätet).
1. Slutför åtgärden (kör t.ex. `bin/magento queue:consumer:start product_action_attribute.update`).
1. Uppdatera administratörssidan för [!DNL Commerce], expandera administratörsmeddelandeavsnittet och klicka på länken **[!UICONTROL Dismiss All Completed Tasks]**.

<u>Förväntade resultat</u>:

Felet _[!UICONTROL Something went wrong]_&#x200B;ska inte visas när de slutförda aktiviteterna rensas.

<u>Faktiska resultat</u>:

Felet _[!UICONTROL Something went wrong]_&#x200B;visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
