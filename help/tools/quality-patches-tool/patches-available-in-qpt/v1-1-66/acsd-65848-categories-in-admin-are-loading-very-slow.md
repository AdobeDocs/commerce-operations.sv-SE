---
title: 'ACSD-65848: Kategorier i administratören läses in mycket långsamt'
description: Använd patchen ACSD-65848 för att åtgärda Adobe Commerce-problemet där det totala antalet produkter i en kategori beräknades med hjälp av ett delval, som försenade inläsningstiden i kategorin.
feature: Admin Workspace
role: Admin, Developer
type: Troubleshooting
exl-id: 0233db9b-86b1-4320-a566-7e7e207dab84
source-git-commit: 1ccb4c1dda5141934e04509b27fdafbfdc436a15
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# ACSD-65848: Kategorier i administratören läses in mycket långsamt

Korrigeringsfilen ACSD-65848 åtgärdar ett problem där det totala antalet produkter i en kategori beräknades med hjälp av ett delval, vilket försenade inläsningstiden i kategorin. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 har installerats. Korrigerings-ID är ACSD-65848. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Vyn/redigeringssidan för kategorin Administratör tar avsevärt lång tid att läsa in. Fördröjningen orsakas av metoden som används för att beräkna det totala antalet produkter i en kategori, som är beroende av en underurvalsfråga. Om du omfaktoriserar den här logiken så att den använder en koppling i stället förbättras prestanda och inläsningstiden minskar.

<u>Steg som ska återskapas</u>:

1. Skapa en ny Adobe Commerce Cloud-instans med version 2.4.8.
1. Skapa 2 500 kategorier och minst 10 000 produkter:
   1. Kopiera katalogen `setup/performance-toolkit` till `./var` så att du kan redigera profilerna.
   1. Öppna profilen `small.xml` och uppdatera den så att den omfattar 2 500 kategorier och 250 000 produkter (för att matcha handlarens inställningar).
   1. Kör följande kommando för att generera korrigeringarna:

      ```bash
      bin/magento 
      setup:performance:generate-fixtures var/setup/performance-toolkit/profiles/ce/small.xml
      ```

1. När produkterna och kategorierna har skapats kontrollerar du att alla kategorier har angetts som ankarpunkter. Kör den här SQL-frågan:

   ```sql
   UPDATE catalog_category_entity_int 
   SET value = 1 
   WHERE attribute_id = (
   SELECT attribute_id 
   FROM eav_attribute 
   WHERE attribute_code = 'is_anchor'
   );
   ```

1. Skapa en djupare kategoristruktur på Admin-panelen:
   * Flytta kategori 2 under kategori 1 för att kapsla den djupare i trädet.
1. Försök att öppna en kategorisida på Admin-panelen med en URL som:
   ```/admin/catalog/category/edit/id/xx/```

<u>Förväntade resultat</u>:

Varje kategorisida öppnas vid första försöket inom några sekunder.

<u>Faktiska resultat</u>:

Det tar mer än en minut att öppna kategorisidor.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
