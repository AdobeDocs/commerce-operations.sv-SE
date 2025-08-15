---
title: 'BB2B-2598: Lägger till cachelagring för storeConfig, valuta, land, länder, availableStores GraphQl-frågor'
description: Använd korrigeringen BB2B-2598 för att lägga till cachelagring i storeConfig, valuta, land, länder och availableStores GraphQl-frågor.
feature: B2B, GraphQL, Cache
role: Admin
exl-id: b842fab4-d2c0-4ef1-be13-182f09015cd7
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# BB2B-2598: Lägger till cachelagring i `storeConfig`-, `currency`-, `country`-, `countries`- och `availableStores` GraphQl-frågor

Korrigeringen BB2B-2598 lägger till cachelagringsfunktioner i `storeConfig`-, `currency`-, `country`-, `countries`- och `availableStores` GraphQl-frågor. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30 är installerad. Korrigerings-ID är BB2B-2598. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7-beta1.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

`availableStores`, `countries`, `country`, `currency`, `storeConfig` och `customAttributeMetadata` GraphQL-frågor är inte tillgängliga.

<u>Förutsättningar</u>:

* Servern pekar på [!DNL Varnish] som proxar till Adobe Commerce serverdel.
* Konfigurationsinställningen `system/full_page_cache/caching_application` är inställd på ** ([!DNL Varnish]), eller gå till Adobe Commerce Admin > **[!UICONTROL Stores]** > **[!UICONTROL System]** > **[!UICONTROL Full Page Cache]** > **[!UICONTROL Caching Application]** > och ställ in den på [!DNL Varnish].

När korrigeringen har installerats utför du följande steg för att se till att det nu finns möjlighet till cachelagring:

1. Skicka `GET`-begäran till någon av de GraphQL-frågor som listas ovan, med hjälp av valfria fält.
1. Skicka om begäran utan att göra några ändringar. Du kommer att märka att den går mycket snabbare. Observera att begäran inte skickas till serverdelen, men hanteras fullständigt av [!DNL Varnish] som en cacheträff.
1. Om ytterligare korrektur krävs kommenterar du bort det `X-Magento-Debug`-huvud som finns i [VCL](https://github.com/magento/magento2/blob/026e5b29a5edfd619bbdea62d636b3cab2ea03b4/app/code/Magento/PageCache/etc/varnish6.vcl#L227), startar sedan om [!DNL Varnish] och kör stegen ovan igen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
