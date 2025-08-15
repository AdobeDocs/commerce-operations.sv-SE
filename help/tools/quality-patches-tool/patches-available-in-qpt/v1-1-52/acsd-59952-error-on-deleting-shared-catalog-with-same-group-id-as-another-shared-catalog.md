---
title: 'ACSD-59952: Fel vid borttagning av delad katalog med samma grupp-ID som en annan delad katalog'
description: Använd patchen ACSD-59952 för att åtgärda Adobe Commerce-problemet där ett fel inträffar när en delad katalog tas bort med samma "customer_group_id" som en annan delad katalog.
feature: B2B, REST
role: Admin, Developer
exl-id: 11cba2e6-dd62-4063-a38c-b98ea70a72e9
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '428'
ht-degree: 0%

---

# ACSD-59952: Fel vid borttagning av delad katalog med samma grupp-ID som en annan delad katalog

ACSD-59952-korrigeringen åtgärdar felet som uppstod när delade kataloger med samma `customer_group_id` som en annan delad katalog togs bort. Dessutom förhindras användare från att skapa sådana delade kataloger. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.52 är installerad. Korrigerings-ID är ACSD-59952. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En ny delad katalog med samma `customer_group_id` som en annan delad katalog kan inte skapas. Om du däremot försöker ta bort den delade katalogen med samma `customer_group_id` genereras ett fel.

<u>Förutsättningar</u>:

Installera Adobe Commerce B2B-modulerna.

<u>Steg som ska återskapas</u>:

1. Skapa flera delade kataloger som tilldelats samma `customer_group_id` med följande REST API-anrop:

   ```REST
   {
       "sharedCatalog": {
           "name": "test1",
           "description": "test",
           "customer_group_id": 1,
           "type": 0,
           "created_at": "03:11:00",
           "created_by": 1,
           "store_id": 0,
           "tax_class_id": 3
       }
   }
   ```

1. Försök att ta bort någon av de delade katalogerna med följande REST API-anrop:

   ```REST
   /rest/default/V1/sharedCatalog/4
   ```

<u>Förväntade resultat</u>:

* Det går inte att skapa flera delade kataloger som tilldelats samma `customer_group_id`.
* Den delade katalogen i ovanstående fall har tagits bort.

<u>Faktiska resultat</u>:

* Det går att skapa flera delade kataloger som tilldelats samma `customer_group_id`.
* Följande fel returneras när du försöker ta bort den delade katalogen med samma `customer_group_id`: *Det går inte att ta bort den delade katalogen*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i vår kunskapsbas för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i vår kunskapsbas för support.

Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
