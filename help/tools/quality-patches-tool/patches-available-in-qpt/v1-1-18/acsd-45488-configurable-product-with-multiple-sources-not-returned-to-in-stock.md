---
title: 'ACSD-45488: Konfigurerbar produkt med flera källor som inte returneras till i lager automatiskt'
description: Korrigeringen ACSD-45488 löser problemet där en konfigurerbar produkt med flera källor inte returneras till i lager automatiskt. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18 är installerat. Korrigerings-ID är ACSD-45488. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.
feature: Configuration, Orders, Products, Returns
role: Admin
exl-id: 53f34e8e-00bd-4386-bebf-b15882e36da1
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 0%

---

# ACSD-45488: Konfigurerbar produkt med flera källor som inte returneras till i lager automatiskt

Korrigeringen ACSD-45488 löser problemet där en konfigurerbar produkt med flera källor inte returneras till i lager automatiskt. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.18 är installerat. Korrigerings-ID är ACSD-45488. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.5

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En konfigurerbar produkt med flera källor returneras inte automatiskt till i lager.

<u>Steg som ska återskapas</u>:

1. Skapa en sekundär Stock-källa.
1. Skapa en konfigurerbar produkt med två associerade virtuella produkter.
1. Tilldela de associerade produkterna till standardlagerkällan och ange kvantiteten till en.
1. Kontrollera `stock_status` från `cataloginventory_stock_status`.
1. Ange att båda de associerade produkterna ska vara *utanför lagret*.
1. Kontrollera `stock_status` från `cataloginventory_stock_status`.
1. Ange att båda associerade produkter ska vara *i lager*.
1. Kontrollera `stock_status` från `cataloginventory_stock_status`.

<u>Förväntade resultat</u>:

Lagerstatusen för den konfigurerbara produkten uppdateras till *i lager* när de associerade produkterna är i lager.

<u>Faktiska resultat</u>:

Lagerstatusen för den konfigurerbara produkten uppdateras inte till *i lager* när de associerade produkterna är i lager.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
