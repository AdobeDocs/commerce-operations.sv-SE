---
title: 'ACSD-64149: Kundsegment med villkoret [!UICONTROL Date range] kan sparas när endast ett datum har redigerats'
description: Använd patchen ACSD-64149 för att åtgärda Adobe Commerce-problemet där kundsegment med ett **[!UICONTROL Date range]**-villkor kan sparas när endast ett av datumen redigeras.
feature: Customers, Admin Workspace
role: Admin, Developer
source-git-commit: c1c5256aee44ce65e9339cf3985e53f710fc7c8a
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 0%

---


# ACSD-64149: Kundsegment med villkoret [!UICONTROL Date range] kan sparas när endast ett datum har redigerats

Korrigeringen ACSD-64149 åtgärdar ett problem där ett kundsegment med ett datumintervall kan sparas när endast ett av datumen redigeras. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60 har installerats. Korrigerings-ID är ACSD-64149. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du redigerar ett befintligt kundsegment med ett villkor för produkter i kundvagnen som anges av ett datumintervall misslyckas konsumenten `matchCustomerSegmentProcessor` med ett SQL-fel.

<u>Steg som ska återskapas</u>:

1. Kontrollera att konsumenten `matchCustomerSegmentProcessor` körs:

   ```bash
   $ bin/magento que:cons:st matchCustomerSegmentProcessor
   ```

1. Gå till **[!UICONTROL Magento backend]**.
1. Gå till **[!UICONTROL Customers]** > **[!UICONTROL Segments]**.
1. Klicka på **[!UICONTROL Add Segment]**.
1. Ange en **[!UICONTROL Segment Name]**, markera en webbplats under **[!UICONTROL Assigned to Website]** och kontrollera att **[!UICONTROL Status]** är inställd på *Aktiv*.
1. Klicka på **[!UICONTROL Save and Continue Edit]**.
1. Gå till fliken **[!UICONTROL Conditions]** och lägg till ett nytt villkor: *Produkter{} > {}Produktlista*{*}*.
1. Lägg till ett undervillkor för **[!UICONTROL Date range]** och ange ett giltigt **[!UICONTROL Date range]**.
1. Klicka på den gröna bekräftelseknappen bredvid **[!UICONTROL Date range]**.
1. Klicka på **[!UICONTROL Date range]** igen, markera datumväljaren, redigera ett av datumvärdena och bekräfta genom att klicka på den gröna knappen.

<u>Förväntade resultat</u>:

**[!UICONTROL Date range]**-väljaren ska inte lägga till tid till datumet när du redigerar.

<u>Faktiska resultat</u>:

* **[!UICONTROL Date range]**-väljaren lägger till tid till datumet:
   * Ett datum har bara datumet, medan det andra har både det angivna datumet och den angivna tiden.
* Följande fel visas i loggarna:

  ```
  report.CRITICAL: SQLSTATE[42000]: Syntax error or access violation: 1064 You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ')' at line 2, query was: SELECT `item`.`quote_id` FROM `quote_item` AS `item`
  INNER JOIN `quote` AS `list` ON item.quote_id = list.entity_id WHERE (list.is_active = 1) AND () [] []
  ```


## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: Uppgraderingar och korrigeringar > Tillämpa korrigeringar i guiden Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
