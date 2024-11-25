---
title: 'ACSD-58735: Administratören kan inte visa övergivna kundvagnar på kundkontot för den associerade webbplatsen'
description: Använd patchen ACSD-58735 för att åtgärda Adobe Commerce-problemet där en begränsad administratör inte kan visa de övergivna kundvagnarna på kundkontosidan i Commerce Admin för en associerad webbplats.
feature: Shopping Cart, Admin Workspace, Customers
role: Admin, Developer
source-git-commit: 35bae8cff40235957f8fea418a43ccead13536da
workflow-type: tm+mt
source-wordcount: '389'
ht-degree: 0%

---



# ACSD-58735: Administratören kan inte visa övergivna kundvagnar på kundkontot för den associerade webbplatsen

Korrigeringen ACSD-58735 åtgärdar ett problem där en administratörsanvändare med en begränsad roll inte kan visa övergivna kunders kundvagnar från Commerce **[!UICONTROL Admin]** > **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** > **[!UICONTROL Select Cart]** > fliken **[!UICONTROL Shopping Cart]**.

Problemet inträffar eftersom om en övergiven kundvagn läses in som standard på Admin-panelen, visas inte det tillhörande butiks-ID:t när stödrastervyn för flera webbplatser.

Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.55 är installerad. Patch-ID:t är ACSD-58735. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.5.0.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Begränsade administratörer kan inte visa övergivna kundvagnar på kundkontosidan på Admin-panelen.

<u>Steg som ska återskapas</u>:

1. Skapa en administratörsroll med åtkomst till endast en av webbplatserna.
1. Skapa en övergiven kundvagn.
1. Logga in som en admin-användare med fullständig behörighet. Kontrollera **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** och se att kundvagnen visas.
1. Kontrollera **[!UICONTROL Reports]** > **[!UICONTROL Abandoned Carts]** som begränsad administratörsanvändare.

<u>Förväntade resultat</u>:

Den begränsade administratören kan se övergivna kundvagnar för den associerade webbplatsen.

<u>Faktiska resultat</u>:

Den begränsade administratören kan inte se övergivna kundvagnar för den associerade webbplatsen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
