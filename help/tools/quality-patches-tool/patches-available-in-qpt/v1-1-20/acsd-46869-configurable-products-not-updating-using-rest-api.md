---
title: 'ACSD-46869: Konfigurerbara produkter som inte uppdateras med REST API vid utcheckning'
description: Korrigeringen ACSD-46869 åtgärdar ett problem där konfigurerbara produkter inte uppdateras med REST API vid utcheckningen. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 är installerat. Korrigerings-ID är ACSD-46869. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
feature: REST, Checkout, Configuration, Orders, Products
role: Admin
exl-id: f03d4b24-ac95-406e-8e9d-908149b9207c
source-git-commit: 470cee19ced38fb90a9565c8bb23e2f9fa97595a
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# ACSD-46869: Konfigurerbara produkter som inte uppdateras med REST API vid utcheckning

Korrigeringen ACSD-46869 åtgärdar ett problem där konfigurerbara produkter inte uppdateras med REST API vid utcheckning. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.20 har installerats. Korrigerings-ID är ACSD-46869. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.5

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du paketet `magento/quality-patches` till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL QPT] landningssidan](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Konfigurerbara produkter uppdateras inte med REST API under utcheckningen.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt med färg- och storleksattribut.
1. Välj **[!UICONTROL Options]** och lägg till produkten i kundvagnen.
1. Gå till **[!UICONTROL Checkout]**, uppdatera storleken flera gånger förutom för kvantitet, och kontrollera begäran och svar.
1. Du får följande svar när du uppdaterar storleken.

```REST API
{"extension_attributes":{"configurable_item_options":[
{"option_id":"960","option_value":25083},
{"option_id":"801","option_value":177}
]}}
```

<u>Förväntade resultat</u>:

Värdet uppdateras enligt ändringarna.

<u>Faktiska resultat</u>:

`option_value` uppdateras inte, så när ordningen placeras har den det gamla storleksvärdet.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tools] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden för kvalitetspatchar.
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
