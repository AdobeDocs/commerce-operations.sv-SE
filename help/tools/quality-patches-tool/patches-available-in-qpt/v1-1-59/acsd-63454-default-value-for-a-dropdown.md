---
title: 'ACSD-63454: Standardvärdet för attributen Listruta och Flera val sparas inte korrekt i databasen'
description: Använd patchen ACSD-63454 för att åtgärda Adobe Commerce-problemet där standardvärdet för en listruta och flera val inte sparas korrekt i databasen.
feature: Attributes, Products
role: Admin, Developer
exl-id: fa79a3bb-e615-44cb-8d84-da892f924fd0
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '401'
ht-degree: 0%

---

# ACSD-63454: Standardvärdet för attributen [!UICONTROL Dropdown] och [!UICONTROL Multiple Select] sparas inte korrekt i databasen

Korrigeringen ACSD-63454 åtgärdar ett problem där standardvärdet för attributen [!UICONTROL Dropdown] och [!UICONTROL Multiple Select] inte sparas korrekt i databasen. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.59 har installerats. Korrigerings-ID är ACSD-63454. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Standardvärdet för attributen [!UICONTROL Dropdown] och [!UICONTROL Multiple Select] sparas inte korrekt i databasen. I stället för att uppdatera standardvärdet läggs det nya värdet till i det gamla, avgränsat med kommatecken.

<u>Steg som ska återskapas</u>:

1. Logga in på serverdelen, gå till **[!UICONTROL Stores]** > *[!UICONTROL Attributes]* > **[!UICONTROL Product]**.
1. Klicka på **[!UICONTROL Add New Attribute]**.
1. Ange följande på fliken **[!UICONTROL Properties]**:
   * **[!UICONTROL Default Label]**: *test*
   * **[!UICONTROL Catalog Input Type for Store Owner]**: *[!UICONTROL Multiple Select]*
   * **[!UICONTROL Manage Options]**: Lägg till två alternativ utan att markera **[!UICONTROL Is Default]**.
1. Klicka på **[!UICONTROL Save Attribute]**.
1. Kontrollera i databasen att kolumnen `default_value` är tom.

   `select attribute_code, default_value from eav_attribute where attribute_code = 'test';`

1. Gå tillbaka och ange ett av de två alternativen som **[!UICONTROL Is Default]**.
1. Kontrollera databasen igen för att se till att `default_value` nu innehåller det valda alternativ-ID:t.
1. Gå tillbaka och ändra standardalternativet genom att välja det andra alternativet.

<u>Förväntade resultat</u>:

Det nya standardvärdet ska ersätta det gamla värdet i databasen.

<u>Faktiska resultat</u>:

I stället för att ersätta standardvärdet med det nya, läggs det nya värdet till det gamla värdet, avgränsat med kommatecken.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
