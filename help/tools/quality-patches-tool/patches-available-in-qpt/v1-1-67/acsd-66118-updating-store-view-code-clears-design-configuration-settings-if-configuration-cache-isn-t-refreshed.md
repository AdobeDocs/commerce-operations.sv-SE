---
title: 'ACSD-66118: [!UICONTROL Store View Code] rensar [!UICONTROL Design Configuration]-inställningarna om [!UICONTROL Configuration Cache] inte uppdateras'
description: Använd korrigeringsfilen ACSD-66118 för att åtgärda Adobe Commerce-problemet där uppdateringen av [!UICONTROL Store View Code] rensar [!UICONTROL Design Configuration] (temat och anpassade inställningar) om [!UICONTROL Configuration Cache] inte uppdateras korrekt.
feature: Cache, Configuration, Themes
role: Admin, Developer
type: Troubleshooting
exl-id: ecfdff54-99e0-4dbe-a0bb-80f60aafc7b6
source-git-commit: 468c780f355c99cf06d557e530e81c414a01961e
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 0%

---

# ACSD-66118: **[!UICONTROL Store View Code]** rensar **[!UICONTROL Design Configuration]**-inställningarna om **[!UICONTROL Configuration Cache]** inte uppdateras

ACSD-66118-korrigeringen åtgärdar ett problem där **[!UICONTROL Store View Code]** rensar **[!UICONTROL Design Configuration]**-inställningarna om **[!UICONTROL Configuration Cache]** inte uppdateras. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 har installerats. Korrigerings-ID är ACSD-66118. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

**[!UICONTROL Design Configuration]** inställningar (till exempel tema och anpassade inställningar) rensas när fältet **[!UICONTROL Store View Code]** uppdateras, om **[!UICONTROL Configuration Cache]** inte uppdateras.

<u>Steg som ska återskapas</u>:

1. Logga in på panelen **[!UICONTROL Admin]**.
2. Navigera till **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL All Stores]**.
3. Redigera en butiksvy som har ett anpassat tema konfigurerat i **[!UICONTROL Content]** > *[!UICONTROL Design]* > **[!UICONTROL Configuration]**.
4. Ändra fältet **[!UICONTROL Code]** (till exempel från `storeview_1` till `storeview_main`).
5. Klicka på **[!UICONTROL Save Store View]** om du vill spara ändringarna.
6. Uppdatera eller öppna sidan **[!UICONTROL Content]** > *[!UICONTROL Design]* > **[!UICONTROL Configuration]** för den uppdaterade sidan **[!UICONTROL Store View]** igen, så markeras inget tema.

<u>Förväntade resultat</u>:

När **[!UICONTROL Store View Code]** har uppdaterats ska **[!UICONTROL Design Configuration]** (inklusive temat och anpassade inställningar) förbli intakt.

<u>Faktiska resultat</u>:

**[!UICONTROL Design Configuration]** har rensats. Temat återgår till standardinställningarna och anpassade inställningar går förlorade.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
