---
title: 'ACSD-64684: Valideringsfel när ett presentkort med ett värde över 999 sparas på grund av kommatecken i tusen (1 000)'
description: Använd patchen ACSD-64684 för att åtgärda Adobe Commerce-problemet där ett valideringsfel inträffar när du sparar ett presentkort med ett värde över 999 på grund av kommatecken i "1 000" (1 000).
feature: Catalog Management
role: Admin, Developer
exl-id: 327c5d28-b52c-4da9-a905-8a3deb755241
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---

# ACSD-64684: Valideringsfel när ett presentkort med ett värde över 999 sparas på grund av kommatecken i tusen (1 000)

Korrigeringen ACSD-64684 åtgärdar ett problem där ett valideringsfel inträffar när ett presentkort sparas med ett värde över 999 på grund av kommatecken i &quot;1 000&quot; (1 000). Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 har installerats. Korrigerings-ID är ACSD-64684. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett valideringsfel inträffar när du redigerar och sparar ett presentkort med ett värde större än 999 på grund av kommatecken (tusentalsavgränsare) i talet, t.ex. &quot;tusen&quot; (1 000).

<u>Steg som ska återskapas</u>:

1. Skapa en presentkortsprodukt.
   1. Ange 1 000 som [!UICONTROL Amount].
   1. Klicka på **[!UICONTROL Save]**.

<u>Förväntade resultat</u>:

* Det nya presentkortet med ett belopp på 1 000 sparas.

<u>Faktiska resultat</u>:

* Ett valideringsfel inträffar när presentkortsbeloppet är större än 999.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
