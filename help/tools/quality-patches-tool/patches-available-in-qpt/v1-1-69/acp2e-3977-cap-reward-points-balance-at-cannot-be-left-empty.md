---
title: 'ACP2E-3977: Fältet [!UICONTROL Cap Reward Points Balance At] får inte vara tomt'
description: Använd korrigeringsfilen ACP2E-3977 för att åtgärda Adobe Commerce-problemet där fältet **[!UICONTROL Cap Reward Points Balance At]** inte kunde lämnas tomt när fältet **[!UICONTROL Rewards Points Balance Redemption Threshold]** angavs, vilket orsakade ett valideringsfel.
feature: Configuration, Rewards
role: Admin, Developer
type: Troubleshooting
exl-id: 5275911f-4f8c-4b37-af11-24ceb69406c9
source-git-commit: 83ce590c5078d70f0414276e2f03a71bdcdad321
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# ACP2E-3977: Fältet **[!UICONTROL Cap Reward Points Balance At]** får inte vara tomt

Problemet där fältet **[!UICONTROL Cap Reward Points Balance At]** inte kan lämnas tomt åtgärdas av AVS2E-3977-korrigeringen, även när den bör tillåtas. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.69 har installerats. Korrigerings-ID är ACP2E-3977. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p10

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Om **[!UICONTROL Cap Reward Points Balance At]** lämnas tomt utlöses ett valideringsfel, även om det bör inaktivera ändpunkten när den lämnas tom.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Customers]** > **[!UICONTROL Reward points]**.
1. Ange **[!UICONTROL Rewards Points Balance Redemption Threshold]** = *30*.
1. Lämna **[!UICONTROL Cap Reward Points Balance At]** tomt.
1. Spara.

<u>Förväntade resultat</u>:

Ett tomt värde för **[!UICONTROL Cap Reward Points Balance At]** tillåts och inaktiverar begränsningen.

<u>Faktiska resultat</u>:

*Saldot för ap Reward Points är ogiltigt. Balansen måste vara ett positivt tal eller lämnas tom. Verifiera och försök igen.*-fel visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
