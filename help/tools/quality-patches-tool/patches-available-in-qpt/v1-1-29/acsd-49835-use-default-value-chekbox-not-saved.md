---
title: 'ACSD-49835: Kryssrutan [!UICONTROL Use Default Value] sparas inte'
description: Använd korrigeringsfilen ACSD-49835 för att åtgärda Adobe Commerce-problemet där kryssrutan [!UICONTROL Use Default Value] inte har sparats korrekt på en butiksnivå för ett flervalsattribut.
feature: Storefront
role: Admin
exl-id: e8d5a95f-b17d-49fc-a6d3-e03554667438
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '352'
ht-degree: 0%

---

# ACSD-49835: Kryssrutan [!UICONTROL Use Default Value] sparas inte

Korrigeringen ACSD-49835 åtgärdar ett problem där kryssrutan [!UICONTROL Use Default Value] inte har sparats korrekt på en butiksnivå för ett flervalsattribut. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 är installerad. Korrigerings-ID är ACSD-49835. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kryssrutan [!UICONTROL Use Default Value] sparas inte korrekt på en butiksnivå för ett flervalsattribut.

<u>Steg som ska återskapas</u>:

1. Skapa en **[!UICONTROL Multiple-select Attribute]** i **[!UICONTROL Stores]** > **[!UICONTROL Attributes]** > **[!UICONTROL Product]** och lägg till den i en attributuppsättning.
1. Gå till en **[!UICONTROL Product]** och spara **[!UICONTROL Values]** i **[!UICONTROL All Store Views (Default Scope)]**.
1. Gå till en specifik **[!UICONTROL Store View Scope]** och spara produkten.
1. Gå till **[!UICONTROL Store View Scope]** och markera kryssrutan **[!UICONTROL Use Default Value]**.

<u>Förväntade resultat</u>:

Flervalsattributvärden sparas korrekt när kryssrutan [!UICONTROL Use Default Value] i [!UICONTROL Store View Scope] markeras.

<u>Faktiska resultat</u>:

Flervalsattributvärden sparas inte korrekt när kryssrutan [!UICONTROL Use Default Value] i [!UICONTROL Store View Scope] markeras.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
