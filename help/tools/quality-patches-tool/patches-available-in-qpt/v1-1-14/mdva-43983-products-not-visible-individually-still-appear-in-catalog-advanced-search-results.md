---
title: 'MDVA-43983: Produkter som angetts som "Inte synliga enskilt" visas i sökresultaten'
description: MDVA-43983-korrigeringen åtgärdar ett problem där produkter som är inställda på"Inte synlig enskilt" fortfarande visas i katalogavancerade sökresultat. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 är installerat. Korrigerings-ID är MDVA-43983. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: Catalog Management, Products, Search
role: Admin
exl-id: d494d263-016b-43fd-aa87-0d74eadc4a6a
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 0%

---

# MDVA-43983: Produkter som angetts som &quot;Inte synliga enskilt&quot; visas i sökresultaten

MDVA-43983-korrigeringen åtgärdar ett problem där produkter som är inställda på&quot;Inte synlig enskilt&quot; fortfarande visas i katalogavancerade sökresultat. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 är installerat. Korrigerings-ID är MDVA-43983. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Produkterna som är inställda på&quot;Inte synlig enskilt&quot; visas fortfarande i katalogavancerade sökresultat.

<u>Steg som ska återskapas</u>:

1. Skapa ett attribut med **katalogindatatypen för butiksägare** som **listruta** eller **visuell färgruta** (till exempel Färg).
1. Ange **Använd i sökning** som **Ja** och **Synligt i avancerad sökning** som **Ja**.
1. Lägg till några attributalternativ.
1. Skapa produkter med **Synlighet** som **Inte synlig enskilt**.
1. Tilldela alternativ för färgattribut.
1. Gå till sidan **Avancerad katalogsökning** i butiken.
1. Välj bara alternativet Färgattribut i fältet Färgattribut och lämna resten av fälten tomma eller som de är.
1. Skicka ett avancerat sökformulär.
1. Observera sökresultaten.

<u>Förväntade resultat</u>:

Produkter som är inställda på&quot;Inte synlig enskilt&quot; visas inte i katalogens avancerade sökresultat.

<u>Faktiska resultat</u>:

Produkter som är inställda på&quot;Inte synlig enskilt&quot; visas i katalogens avancerade sökresultat.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar &#x200B;](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
