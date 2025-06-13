---
title: 'MDVA-42657: Det går inte att välja kategorier i villkoren för kundsegmentet'
description: MDVA-42657-korrigeringen löser problemet där administratörsanvändaren inte kan välja kategorier under kundsegmentsvillkoren. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 är installerat. Korrigerings-ID är MDVA-42657. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: Categories, Console, Customer Service
role: Admin
exl-id: 115bad99-a603-4940-897e-034974ed1a6c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 0%

---

# MDVA-42657: Det går inte att välja kategorier i villkoren för kundsegmentet

MDVA-42657-korrigeringen löser problemet där administratörsanvändaren inte kan välja kategorier under kundsegmentsvillkoren. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.9 har installerats. Korrigerings-ID är MDVA-42657. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.3-p1

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratörsanvändaren kan inte välja kategorier i kundsegmentsvillkoren.

<u>Steg som ska återskapas</u>:

1. Gå till **Kunder** > **Segment**.
1. Skapa ett nytt segment.
1. Gå till det nyligen skapade segmentet och klicka på **Villkor** i navigeringen till vänster.
1. Klicka på det gröna plustecknet.
1. Välj Produkthistorik under Produkter.
1. Ändra&quot;visade&quot; till&quot;ordnade&quot;.
1. Ändra&quot;ALL&quot; till&quot;ANY&quot;.
1. Klicka på det kapslade gröna plustecknet och välj Kategori.
1. Klicka på signaturen **..** och klicka sedan på väljarikonen (till vänster om bockmarkeringen).
1. Öppna webbläsarens dev-konsol.
1. Markera kryssrutorna för någon/flera kategorier och notera javascript-felet som genereras i konsolen.
1. Klicka på knappen **Spara**.
1. Navigera tillbaka till villkoret och kontrollera om de valda kategorierna har sparats.

<u>Förväntade resultat</u>:

De valda kategorierna sparas och markeras när segmentvillkoren visas/redigeras.

<u>Faktiska resultat</u>:

De valda kategorierna saknas och sparades inte korrekt. Följande fel visas i konsolen:

```
category-checkbox-tree.js:249 Uncaught TypeError: Cannot set properties of undefined (setting 'value')
    at Ext.tree.TreePanel.Enhanced.<anonymous> (category-checkbox-tree.js:249)
    at Ext.util.Event.fire (ext-tree.js:29)
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
