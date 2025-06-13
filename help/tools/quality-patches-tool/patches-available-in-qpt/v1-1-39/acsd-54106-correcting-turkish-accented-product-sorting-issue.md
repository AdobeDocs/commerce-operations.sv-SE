---
title: 'ACSD-54106: Rektifiera turkiska teckensorteringar med accenttecken i produktkategorin'
description: Använd patchen ACSD-54106 för att åtgärda Adobe Commerce-problemet där produktsortering efter namn för turkiska accenttecken är felaktig.
feature: Categories, Products, Search
role: Admin
exl-id: 45c8efbb-85d0-4d25-9d7e-9c41a97e80fa
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '402'
ht-degree: 0%

---

# ACSD-54106: Rektifiera turkiska teckensorteringar med accenttecken i produktkategorin

Korrigeringen ACSD-54106 åtgärdar ett problem där produktsortering efter namn för turkiska accenttecken är felaktig. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.39 är installerad. Korrigerings-ID är ACSD-54106. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.1 - 2.4.4-p5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Sorteringen av produkter i kategorier efter namn är felaktig för turkiska accenttecken.

<u>Steg som ska återskapas</u>:

1. Logga in på adminpanelen.
1. Skapa enkla produkter med följande namn och tilldela dem till valfri kategori:

* Namn A
* Namn
* Namn D
* Ğ
* Namn M
* Namn Ö
* Namn Ü
* Namn Y
* Namn Z

1. Navigera till butiken och öppna kategorin som innehåller produkterna.
1. Ändra sorteringsordningen till *[!UICONTROL By Name]*.

<u>Förväntade resultat</u>:

Produkterna sorteras korrekt i följande ordning:

* Namn A
* Namn
* Namn D
* Ğ
* Namn M
* Namn Ö
* Namn Ü
* Namn Y
* Namn Z

<u>Faktiska resultat</u>:

Produkterna sorteras felaktigt i följande ordning:

* Namn A
* Namn D
* Namn M
* Namn Y
* Namn Z
* Namn
* Namn Ö
* Namn Ü
* Ğ

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
