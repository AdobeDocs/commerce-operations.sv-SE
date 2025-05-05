---
title: 'ACSD-48866: Fel vid begäran av RSS-feed för kategorier'
description: Använd patchen ACSD-48866 för att åtgärda Adobe Commerce-problemet när ett fel inträffar när RSS-feed begärs för kategorier.
feature: Admin Workspace, Categories
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# ACSD-48866: Fel vid begäran av RSS-feed för kategorier

Korrigeringen ACSD-48866 åtgärdar ett problem där ett fel inträffar när en RSS-feed begärs för kategorier. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.28 har installerats. Korrigerings-ID är ACSD-48866. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett fel inträffar när en RSS-feed begärs för kategorier.

<u>Steg som ska återskapas</u>:

1. Aktivera RSS-feed i **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Catalog]** > **[!UICONTROL RSS Feeds]** > **[!UICONTROL RSS Config]** > **[!UICONTROL Enable RSS]**.
1. Aktivera [!UICONTROL Top Level Category] i **[!UICONTROL Stores]** > **[!UICONTROL Configurations]** > **[!UICONTROL Catalog]** > **[!UICONTROL RSS Feeds]** > **[!UICONTROL Catalog]** > **[!UICONTROL Top Level Category]**.
1. Bläddra bland butikens Kategorisida för RSS-flöden.
1. Kontrollera loggfilerna i `var/log`.

<u>Förväntade resultat</u>:

Inga fel i loggfilen.

<u>Faktiska resultat</u>:

Följande fel visas i loggfilen:

```
Text fields are not optimised for operations that require per-document field data like aggregations and sorting, so these operations are disabled by default. Please use a keyword field instead. Alternatively, set fielddata=true on [updated_at] in order to load field data by uninverting the inverted index.
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
