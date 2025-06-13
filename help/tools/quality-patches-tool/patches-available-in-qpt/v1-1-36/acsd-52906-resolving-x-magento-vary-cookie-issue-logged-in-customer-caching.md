---
title: 'ACSD-52906: Löser X-Magento-Vary-problem med cookie för inloggad kundcache'
description: Använd ACSD-52906-korrigeringen för att åtgärda Adobe Commerce-problemet där X-Magento-Vary-cookien är felaktigt inställd för inloggade kunder.
feature: Cache
role: Admin, Developer
exl-id: 487b7588-7131-4502-b714-05f37520991f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '393'
ht-degree: 0%

---

# ACSD-52906: Löser X-Magento-Vary-cookie-problem för inloggade kunder

Korrigeringen ACSD-52906 åtgärdar ett problem där X-Magento-Vary-cookien inte är korrekt inställd för inloggade kunder. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.36 har installerats. Korrigerings-ID är ACSD-52906. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

X-Magento-Vary-cookie är felaktigt inställd för inloggade kunder som tillhör samma kundsegment, vilket orsakar felaktig cachelagring för vissa sidor.

<u>Förutsättningar</u>:

Adobe Commerce Inventory management-moduler (MSI) är installerade och aktiverade.

<u>Steg som ska återskapas</u>:

1. Konfigurera [!DNL Varnish] eller [!DNL Fastly]-cache.
1. Skapa ett nytt kundsegment och tilldela det till *registrerade*-kunder.
1. Skapa två kunder, till exempel customer1 och customer2.
1. Rensa cachen.
1. Logga in som kund1 och gå till startsidan.
1. Öppna en inkodade sida i webbläsaren.
1. Gå till en annan sida än startsidan.
1. Logga in som kund2.
1. Gå till startsidan.
1. Kontrollera om sidan är cachelagrad i webbläsarens dev-konsol.

<u>Förväntade resultat</u>:

Sidan hämtas från cachen.

<u>Faktiska resultat</u>:

Sidan är inte cachelagrad.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
