---
title: 'MDVA-43859: Felet"Ingen sådan entitet med customerId =" loggades när en kund togs bort från loggen'
description: MDVA-43859-korrigeringen åtgärdar ett problem där felet *Ingen sådan enhet med customerId =* loggas när en borttagen kund försöker logga in. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 är installerat. Korrigerings-ID är MDVA-43859. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: Variables
role: Admin
exl-id: b8451b08-978a-44a2-8664-4369e832423b
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---

# MDVA-43859: Felet&quot;Ingen sådan entitet med customerId =&quot; loggades när en kund togs bort från loggen

MDVA-43859-korrigeringen åtgärdar ett problem där felet *Ingen sådan entitet med customerId =* loggas när en borttagen kund försöker logga in. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.14 är installerat. Korrigerings-ID är MDVA-43859. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.4

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Felet *Ingen sådan entitet med customerId =* loggas när en borttagen kund försöker logga in.

<u>Steg som ska återskapas</u>:

1. Skapa ett kundkonto från frontend.
1. Logga ut och logga in på kundkontot som skapades i steg 1.
1. Läs in serverdelen i en annan webbläsare och gå till kundens rutnät.
1. Ta bort kunden som skapades i steg ett.
1. Växla tillbaka till den första webbläsaren och försök logga ut.

<u>Förväntade resultat</u>:

Kunden dirigeras om till inloggningssidan utan fel.

<u>Faktiska resultat</u>:

Kunden får följande fel: *Ingen sådan entitet med customerId =*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
