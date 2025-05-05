---
title: "ACSD-59930: Förbättrar resultatet för företagets flöden"
description: Använd patchen ACSD-59930 för att lösa problemet med Adobe Commerce där ett *Timeout*-fel visas på adminpanelen när du skapar, sparar eller tar bort ett företag med en administratör som har adressen * 100+* i adressboken.
feature: Customers, B2B
role: Admin, Developer
source-git-commit: bff014ede6ab7e8e72700814bb4edda2e733557a
workflow-type: tm+mt
source-wordcount: '367'
ht-degree: 0%

---

# ACSD-59930: Förbättrar resultatet för företagets flöden

Korrigeringen ACSD-59930 åtgärdar ett problem där ett *Timeout* -fel visas på administratörspanelen när ett företag med en administratör med *100+* -adresser skapas, sparas eller tas bort i adressboken. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.53 är installerad. Korrigerings-ID är ACSD-59930. Observera att problemet är planerat att åtgärdas i Adobe Commerce B2B-1.5.0.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.6-p4

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.6 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Förbättrar prestanda för företagets arbetsflöden för att skapa, spara och ta bort.

<u>Krav:</u>:

Installera och aktivera Adobe Commerce B2B-moduler.

<u>Steg som ska återskapas</u>:

1. Skapa en kund med *1000+* adresser i *[!UICONTROL Address Book]*.
1. Skapa ett företag och använd kunden ovan som administratör.
1. Spara företaget.

<u>Förväntade resultat</u>:

Företaget har skapats utan timeoutfel.

<u>Faktiska resultat</u>:

Ett timeout-fel visas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.