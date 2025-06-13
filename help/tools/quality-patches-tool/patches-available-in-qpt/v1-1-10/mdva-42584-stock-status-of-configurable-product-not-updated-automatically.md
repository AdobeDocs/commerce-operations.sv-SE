---
title: 'MDVA-42584: Stock-status för konfigurerbar produkt uppdateras inte automatiskt'
description: MDVA-42584-korrigeringen löser problemet där den konfigurerbara produktens Stock-status inte uppdateras automatiskt när den enkla produkten uppdateras. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 är installerat. Patch-ID:t är MDVA-42584. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.
feature: Configuration, Orders, Products
role: Admin
exl-id: 6311f069-f08f-4d58-9f4b-fa1246c02640
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---

# MDVA-42584: Stock-status för konfigurerbar produkt uppdateras inte automatiskt

MDVA-42584-korrigeringen löser problemet där den konfigurerbara produktens Stock-status inte uppdateras automatiskt när den enkla produkten uppdateras. Den här korrigeringen är tillgänglig när [QPT-verktyget (Quality Patches Tool)](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.10 är installerat. Patch-ID:t är MDVA-42584. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.5.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.2-p2

>[!NOTE]
>
>Patchen kan bli tillämplig på andra versioner med nya Quality Patches Tool-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Stock-statusen för den konfigurerbara produkten i backend uppdateras inte automatiskt när dess enkla produkt är inställd på **I Stock** via API eller import.

<u>Förutsättningar</u>:

MSI har installerats.

<u>Steg som ska återskapas</u>:

1. Skapa en konfigurerbar produkt, **InvCheck001**, med två alternativ: **InvCheck001-M** och **InvCheck001-L**.
1. Båda de enkla produkterna ska ha Kvantitet och ska vara **I Stock** så att den konfigurerbara produkten också är **I Stock** i backend-objektet.
1. Uppdatera nu både enkla produkter och ställ in Kvantitet på **0** och Stock-status till **Utanför lager**.
1. Uppdatera den konfigurerbara produkten och verifiera att Stock-statusen har uppdaterats till **Utanför lager**.
1. Använd följande API-slutpunkt och ställ in den enkla produkten **InvCheck001-M** på **I Stock** med Kvantitet > 0.

   ```JSON
   /rest/V1/inventory/source-items
   
   {
     "sourceItems":
     [
       {
         "sku": "InvCheck001-M",
         "source_code": "default",
         "quantity": 10,
         "status": 1
       }
     ]
   }
   ```

1. Gå till backend och verifiera kvantitet och lagerstatus för den enkla produkten **InvCheck001-M**. Den uppdateras till **I lager**.
1. Uppdatera den konfigurerbara produkten och kontrollera lagerstatusen.

<u>Förväntade resultat</u>:

Den konfigurerbara produktens **InvCheck001** i serverdelen uppdateras automatiskt till **I Stock**.

<u>Faktiska resultat</u>:

Den konfigurerbara produktens Stock-status är fortfarande **Utanför Stock**.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om verktyget för kvalitetskorrigeringar finns i:

* [Verktyget för kvalitetskorrigeringar har släppts: ett nytt verktyg för självbetjäning av kvalitetskorrigeringar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med verktyget för kvalitetskorrigeringar ](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i [!DNL Quality Patches Tool]-handboken.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
