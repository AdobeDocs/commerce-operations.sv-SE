---
title: 'ACSD-49389: Redo för hämtning av e-post som skickas av API när den inte är klar för hämtning'
description: Använd patchen ACSD-49389 för att åtgärda Adobe Commerce-problemet där ett e-postmeddelande som är klart för hämtning skickas av API:t när beställningen inte är klar för hämtning.
feature: REST, Communications
role: Admin
exl-id: d1bc430a-3021-40d1-9091-db8ed9125619
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-49389: Redo för hämtning av e-post som skickas av API när den inte är klar för hämtning

Korrigeringen ACSD-49389 åtgärdar ett problem där ett e-postmeddelande som är klart för hämtning skickas av API:t när beställningen inte är klar för hämtning. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.29 är installerad. Korrigerings-ID är ACSD-49389. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.0 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du paketet `magento/quality-patches` till den senaste versionen och kontrollerar kompatibiliteten på [QPT-startsidan](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett e-postmeddelande som är klart för hämtning skickas av API:t när beställningen inte är klar för hämtning.

<u>Steg som ska återskapas</u>:

1. Aktivera metoden *[!UICONTROL In-Store Delivery]*.
1. Skapa en Stock-källa med hämtningsplats aktiverad.
1. Skapa ett nytt arkiv med huvudwebbplatsen med källan som skapas ovan.
1. Skapa en produkt som tilldelar samma källa.
1. Ange lagerkvantitet = 1.
1. Ta en titt på produkten som skapats i steg 4 med metoden *[!UICONTROL In-Store Delivery]* från butiken.
1. Skapa en faktura för ordern.
1. Ställ in produktkvantiteten på *0* och skapa den ur lager.
1. Bokför följande API-begäran:

```
{
    "orderIds": [
        1
    ]
}
```

<u>Förväntade resultat</u>:

Redo för att hämta e-post har inte skickats.

<u>Faktiska resultat</u>:

API returnerar *Beställningen är inte klar för hämtning*, men e-postmeddelandet skickas nu för hämtning.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [Patchar i QPT](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i handboken för [!DNL Quality Patches Tool].
