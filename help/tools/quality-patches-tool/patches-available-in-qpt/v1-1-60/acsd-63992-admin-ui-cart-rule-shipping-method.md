---
title: 'ACSD-63992: [!UICONTROL Cart Price Rule] med villkorsfel för kupong och leveransmetod i Admin UI'
description: Använd patchen ACSD-63992 för att åtgärda Adobe Commerce-problemet där [!UICONTROL Cart Price Rule] med en kupong och ett villkor som baseras på en leveransmetod inte kan tillämpas korrekt via administratörsgränssnittet.
feature: Price Rules, Admin Workspace
role: Admin, Developer
source-git-commit: ef17f2f75eae16e3efada4ea08ee0f068fd60702
workflow-type: tm+mt
source-wordcount: '371'
ht-degree: 0%

---


# ACSD-63992: [!UICONTROL Cart Price Rule] med villkorsfel för kupong och leveransmetod i Admin UI

Korrigeringen ACSD-63992 åtgärdar ett problem där [!UICONTROL Cart Price Rule] med en kupong och ett villkor som baseras på en leveransmetod inte kan tillämpas korrekt via administratörsgränssnittet. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.60 har installerats. Korrigerings-ID är ACSD-63992. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När en kundvagnsregel innehåller ett villkor för leveransmetoden i avsnittet **[!UICONTROL Conditions]**, gäller inte den associerade kupongkoden när en order skapas via Admin Panel. I stället visas följande fel:

_Kupongkoden &lt;> är inte giltig. Verifiera koden och försök igen._

<u>Steg som ska återskapas</u>:

1. Skapa en kundvagnsprisregel och beskriv villkoren:
   * Under *[!UICONTROL Conditions]*: Lägg till ett villkor som inkluderar leveransmetoden (till exempel *[!UICONTROL Flat Rate]*).
   * Under *[!UICONTROL Rule Information]*: Ange **[!UICONTROL Coupon]** till *[!UICONTROL Specific Coupon]* och ange sedan **[!UICONTROL Coupon Code]** som *TEST*.
1. Skapa en ny order från Admin Panel och ange kupongkoden *TEST* i fältet **[!UICONTROL Apply Coupon]**.

<u>Förväntade resultat</u>:

Kupongen har tillämpats.

<u>Faktiska resultat</u>:

Följande felmeddelande visas:

```
"The "TEST" coupon code isn't valid. Verify the code and try again."
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
