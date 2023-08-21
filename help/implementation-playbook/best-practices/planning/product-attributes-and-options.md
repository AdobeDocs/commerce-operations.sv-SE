---
title: Bästa praxis för konfiguration av produktattribut
description: Lär dig optimera Adobe Commerce prestanda genom att begränsa antalet produktattribut, attributalternativ och attributuppsättningar
role: User, Admin
feature: Best Practices, Catalog Management
exl-id: 81783a4c-bc82-4733-bee3-0154cf03079a
source-git-commit: df8878a3fea19b8f1780b5037273e18b5a3f1373
workflow-type: tm+mt
source-wordcount: '564'
ht-degree: 0%

---

# Bästa tillvägagångssätt för konfiguration av produktattribut

- För bästa prestanda bör du inte konfigurera fler än det högsta rekommenderade antalet produktattribut eller produktattributsalternativ.

- **Produktattribut**—
   - För Adobe Commerce version 2.3.x och 2.4.0 till 2.4.1-p1 får du inte konfigurera fler än 500 attribut
   - Konfigurera upp till 1 500 produktattribut för Adobe Commerce version 2.4.2 och senare
- **Produktattributsalternativ**-Konfigurera upp till 100 attributalternativ för varje attribut
- **Produktattributuppsättningar**-Konfigurera högst 1 000 attributuppsättningar _
>[!NOTE]
>
>Produktattributen anger funktioner som gäller globalt för alla produkter. Produktattributsalternativen är anpassningar för att specificera funktioner som gäller för specifika produkter.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Minska antalet produktattribut

För bästa prestanda när du hanterar produkter från Admin och hämtar produktdata i butiken:

- Använd olika produktmallar (attributuppsättningar) för olika produkter.
- Utnyttja anpassade alternativ och komplexa produkter för hantering av variationer
- Minimera antalet sökbara attribut.
- Ta bort produktegenskaper som inte används.
- Lagra och hantera icke-handelsrelaterade attribut i externa produkthanteringssystem (PMS).

## Minska antalet produktattribut

För bästa prestanda när du hanterar produkter från Admin och hämtar produktdata i butiken:

- Använd olika variationsmekanismer för att skapa produkter: komplexa produkter, anpassade alternativ som en källa till produktvariationer.
- Skapa specifika produktmallar med riktade attribut och alternativ för att undvika generaliserade produktmallar och alternativbehållare.
- Underhåll en lista över faktiska attributalternativ.
- Hantera produktinformation via ett externt produkthanteringssystem (PMS).

## Minska antalet produktattributuppsättningar

Ta bort oanvända produktattributuppsättningar med MySQL.

### Granska konfigurationen av attributuppsättning

1. [Anslut till platsdatabasen](https://devdocs.magento.com/cloud/project/services-mysql.html#connect-to-the-database).

1. Hitta antalet attributuppsättningar med MySQL

   ```sql
   SELECT COUNT(*) AS 'attribute_set' FROM *${TABLE_PREFIX}*eav_attribute_set;
   ```

1. Ta bort alla oanvända attributuppsättningar.

## Potentiella resultateffekter

Konfigurera många **produktattribut** ökar mallstorleken för varje produkt (EAV-struktur) och mängden data som måste hämtas. Ökningen påverkar åtgärder på följande sätt:

- Ökning i SQL-frågor, trafik som är relaterad till EAV-datahämtning och mängden data som bearbetas, vilket ger minskat databasflöde
- Betydande ökning av storleken på Adobe Commerce-index och fulltextsökningsindex
- Hårda MySQL-gränser när ett FLAT-index skapas för stora produktmallar och det inte går att använda det

Ökning av produktdata och indexstorlekar kan påverka webbplatsens prestanda på följande sätt:

- Ökad svarstid för de flesta butiksscenarier som rör katalogbläddring, sökning (snabb och avancerad) och lagerstyrd navigering.
- Produkthanteringsåtgärder i Admin tar lång tid, vilket kan leda till timeout.
- Funktionen för produktmassåtgärder kan blockeras.
- Indexåterskapningstiden för medelstora och stora kataloger kan inte utföras dagligen på grund av långa körningstider.

Konfigurera många **attributalternativ** kan påverka webbplatsens prestanda på följande sätt:

- Långa efterfrågnings- och renderingstider för produktinformation (PDP) och kategorisidor som innehåller komplexa produkter.
- Admin - produkt sparar Åtgärdens svarstid ökar över optimala prestandamål.
- Öka tiden för formuläråtergivning i produktredigering.
- Långsam utcheckning.

## Ytterligare information

- [Produktattribut - översikt](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/product-attributes.html)
- [Attributuppsättningar](https://experienceleague.adobe.com/docs/commerce-admin/catalog/product-attributes/create/attribute-sets.html)
- [Skapa en produkt](https://experienceleague.adobe.com/docs/commerce-admin/catalog/products/product-create.html)
- [Självstudiekurser för anpassning > Anpassa formulär för att skapa produkter](https://developer.adobe.com/commerce/php/tutorials/admin/custom-product-creation-form/)
