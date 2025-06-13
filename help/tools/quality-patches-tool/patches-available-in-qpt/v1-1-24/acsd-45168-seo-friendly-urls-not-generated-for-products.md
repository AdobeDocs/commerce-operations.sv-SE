---
title: 'ACSD-45168: SEO-vänliga URL:er genereras inte för produkter som har attributen url_key åsidosatt'
description: Använd patchen ACSD-45168 för att åtgärda Adobe Commerce-problemet där SEO-vänliga URL:er inte genereras för produkter som har attributen url_key åsidosatt på butiksvisningsnivå.
feature: Attributes, Cache, Categories, Marketing Tools, Products
role: Admin
exl-id: 7d908307-f60c-4758-ad0f-f108ebb94558
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---

# ACSD-45168: SEO-vänliga URL:er genereras inte för produkter som har attributen url_key åsidosatt

Korrigeringen ACSD-45168 åtgärdar ett problem där SEO-vänliga URL:er inte genereras för produkter som har url_key-attribut åsidosatta på butiksvynivå. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.24 har installerats. Korrigerings-ID är ACSD-45168. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.5-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

SEO-vänliga URL:er genereras inte för produkter som har url_key-attribut åsidosatta på butiksvisningsnivå.

<u>Steg som ska återskapas</u>:

1. Ange konfigurationen enligt följande genom att gå till **[!UICONTROL Commerce Admin]** > **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Search Engine Optimization]**:
   * [!UICONTROL Use Categories Path for Product URLs] = *Ja*
   * [!UICONTROL Generate "category/product" URL Rewrites] = *Ja*
1. Rensa konfigurationscachen.
1. Skapa två kategorier: [!UICONTROL Category 1] och [!UICONTROL Category 2].
1. Skapa två produkter: [!UICONTROL Product 1] i [!UICONTROL Category 1], [!UICONTROL Product 2] i [!UICONTROL Category 1].
1. Ändra omfattningen till [!UICONTROL Default Store View] för [!UICONTROL Product 1].
1. Avmarkera den valfria URL:en [!UICONTROL Key] i [!UICONTROL Search Engine Optimization].
1. Spara produkten.
1. Växla tillbaka till [!UICONTROL All Store Views].
1. Lägg till [!UICONTROL Product 1] i [!UICONTROL Category 2] och lägg till [!UICONTROL Product 2] i [!UICONTROL Category 2].
1. Kontrollera tabellen `url_rewrite` eller [!UICONTROL Marketing] > [!UICONTROL SEO & Search] > [!UICONTROL URL Rewrites].

<u>Förväntade resultat</u>:

Den SEO-anpassade URL:en för [!UICONTROL Category 2] skapas för [!UICONTROL Product 1].

<u>Faktiska resultat</u>:

Den SEO-vänliga URL:en för [!UICONTROL Category 2] saknas för [!UICONTROL Product 1] eftersom URL-nyckelattributet för butiksvyn hade skrivits över.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool]
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i guiden för Commerce om molninfrastruktur

## Relaterad läsning

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool]
* [Metodtips för att ändra databastabeller](https://experienceleague.adobe.com/en/docs/commerce-operations/implementation-playbook/best-practices/development/modifying-core-and-third-party-tables#why-adobe-recommends-avoiding-modifications) i Commerce Implementeringspellbook

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
