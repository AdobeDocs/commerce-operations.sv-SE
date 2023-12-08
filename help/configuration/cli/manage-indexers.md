---
title: Hantera indexerare
description: Se exempel på hur du visar och hanterar Commerce-indexerare.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: 8b9e4de2799532e4654fce63d856c2d301025f09
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# Hantera indexerare

{{file-system-owner}}

Så här visar du en lista över alla indexerare:

```bash
bin/magento indexer:info
```

Listan visas enligt följande:

```terminal
design_config_grid                       Design Config Grid
customer_grid                            Customer Grid
catalog_category_product                 Category Products
catalog_product_category                 Product Categories
catalogrule_rule                         Catalog Rule Product
catalog_product_attribute                Product EAV
inventory                                Inventory
catalogrule_product                      Catalog Product Rule
cataloginventory_stock                   Stock
targetrule_product_rule                  Product/Target Rule
targetrule_rule_product                  Target Rule/Product
catalog_product_price                    Product Price
catalogsearch_fulltext                   Catalog Search
salesrule_rule                           Sales Rule
```

>[!NOTE]
> Adobe Commerce handlare som använder Live Search, Catalog Service eller Product Recommendations kan använda [SaaS-baserad prisindexering](https://experienceleague.adobe.com/docs/commerce-merchant-services/price-indexer/index.html).

## Visa indexeringsstatus

Med det här kommandot kan du visa status för alla indexerare eller specifika indexerare. Ta till exempel reda på om en indexerare behöver indexeras om.

Kommandoalternativ:

```bash
bin/magento indexer:status [indexer]
```

Plats `[indexer]` är en blankstegsavgränsad lista med indexerare. Uteslut `[indexer]` för att visa status för alla indexerare.

Exempelresultat:

```terminal
+----------------------+------------------+-----------+---------------------+---------------------+
| Title                | Status           | Update On | Schedule Status     | Schedule Updated    |
+----------------------+------------------+-----------+---------------------+---------------------+
| Catalog Product Rule | Reindex required | Save      |                     |                     |
| Catalog Rule Product | Reindex required | Save      |                     |                     |
| Catalog Search       | Ready            | Save      |                     |                     |
| Category Products    | Reindex required | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:53 |
| Customer Grid        | Ready            | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:52 |
| Design Config Grid   | Ready            | Schedule  | idle (0 in backlog) | 2018-06-28 09:45:52 |
| Inventory            | Ready            | Save      |                     |                     |
| Product Categories   | Reindex required | Schedule  | idle (0 in backlog) | 2021-06-28 09:45:53 |
| Product EAV          | Reindex required | Save      |                     |                     |
| Product Price        | Reindex required | Save      |                     |                     |
| Stock                | Reindex required | Save      |                     |                     |
+----------------------+------------------+-----------+---------------------+---------------------+
```

## Indexera om

Med det här kommandot kan du indexera om alla eller markerade indexerare endast en gång.

>[!INFO]
>
>Detta kommando indexerar bara en gång. Om du vill hålla indexerarna uppdaterade måste du konfigurera en [cron](../cli/configure-cron-jobs.md).

Kommandoalternativ:

```bash
bin/magento indexer:reindex [indexer]
```

Plats `[indexer]` är en blankstegsavgränsad lista med indexerare. Uteslut `[indexer]` om du vill indexera om alla indexerare.

Exempelresultat:

```terminal
Design Config Grid index has been rebuilt successfully in <time>
Customer Grid index has been rebuilt successfully in <time>
Category Products index has been rebuilt successfully in <time>
Product Categories index has been rebuilt successfully in <time>
Catalog Rule Product index has been rebuilt successfully in <time>
Product EAV index has been rebuilt successfully in <time>
Inventory index has been rebuilt successfully in <time>
Catalog Product Rule index has been rebuilt successfully in <time>
Stock index has been rebuilt successfully in <time>
Product Price index has been rebuilt successfully in <time>
Catalog Search index has been rebuilt successfully in <time>
```

>[!INFO]
>
>Det kan ta lång tid att indexera om alla indexerare för butiker med ett stort antal produkter, kunder, kategorier och kampanjregler.

### Omindexering i parallellt läge

{{php-process-control}}

Indexerare har omfång och flertrådsteknik som stöder omindexering i parallellt läge. Den är parallell med indexerarens dimension och körs över flera trådar, vilket minskar bearbetningstiden.

I detta sammanhang `dimension` är omindexeringens omfång, till exempel ett `website` eller bara en specifik `customer_group`.

Indexparallelliseringen påverkar bara omfångsindexerare, vilket innebär att Commerce delar upp data i flera tabeller med indexeraren som omfång i stället för att lagra alla data i en tabell.

Du kan köra följande index i parallellt läge:

- `Catalog Search Fulltext` kan jämföras med butiksvyer.
- `Category Product` kan jämföras med butiksvyer.
- `Catalog Price` kan kombineras av webbplats- och kundgrupper.
- `Catalog Permissions` kan jämföras med kundgrupper.

>[!INFO]
>
>Parallellering för fulltext och kategoriprodukt för katalogsökning är aktiverat som standard.

Om du vill använda parallellisering anger du ett av de tillgängliga dimensionslägena för produktprisindexeraren:

- `none` (standard)
- `website`
- `customer_group`
- `website_and_customer_group`

Så här anger du till exempel läge per webbplats:

```bash
bin/magento indexer:set-dimensions-mode catalog_product_price website
```

Om du vill använda parallellisering för katalogbehörigheter anger du ett av de tillgängliga dimensionslägena för indexeraren för katalogbehörigheter:

- `none` (standard)
- `customer_group`

Eller för att kontrollera det aktuella läget:

```bash
bin/magento indexer:show-dimensions-mode
```

Om du vill indexera om i parallellt läge kör du kommandot reindex med systemvariabeln `MAGE_INDEXER_THREADS_COUNT`eller lägga till en miljövariabel i `env.php` -fil. Den här variabeln anger antalet trådar för omindexeringsbearbetningen.

Följande kommando kör till exempel `Catalog Search Fulltext` indexerare över tre trådar:

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## Återställ indexerare

Använd det här kommandot om du vill göra alla indexerare eller specifika indexerare ogiltiga.

Kommandoalternativ:

```bash
bin/magento indexer:reset [indexer]
```

Plats ```[indexer]``` är en blankstegsavgränsad lista med indexerare. Uteslut `[indexer]` om du vill göra alla indexerare ogiltiga.

Exempelresultat:

```terminal
Design Config Grid indexer has been invalidated.
Customer Grid indexer has been invalidated.
Category Products indexer has been invalidated.
Product Categories indexer has been invalidated.
Catalog Rule Product indexer has been invalidated.
Product EAV indexer has been invalidated.
Inventory indexer has been invalidated.
Catalog Product Rule indexer has been invalidated.
Stock indexer has been invalidated.
Product Price indexer has been invalidated.
Catalog Search indexer has been invalidated.
```

## Konfigurera indexerare

Använd det här kommandot för att ange följande indexeringsalternativ:

- **Uppdatera när du sparar (`realtime`)**: Indexerade data uppdateras när en ändring görs i Admin. (Exempel: kategoriproduktindexet indexeras om efter att produkterna har lagts till i en kategori i Admin.) Det här är standardinställningen.
- **Uppdatera enligt schema (`schedule`)**: Data indexeras enligt det schema som anges av ditt cron-jobb.

[Läs mer om indexering](https://developer.adobe.com/commerce/php/development/components/indexing/).

### Visa den aktuella konfigurationen

Så här visar du den aktuella indexerarkonfigurationen:

```bash
bin/magento indexer:show-mode [indexer]
```

Plats `[indexer]` är en blankstegsavgränsad lista med indexerare. Uteslut `[indexer]` om du vill visa alla indexeringslägen. Om du till exempel vill visa läget för alla indexerare:

Exempelresultat:

```terminal
Design Config Grid:                                Update on Save
Customer Grid:                                     Update on Save
Category Products:                                 Update on Save
Product Categories:                                Update on Save
Catalog Rule Product:                              Update on Save
Product EAV:                                       Update on Save
Inventory:                                         Update on Save
Catalog Product Rule:                              Update on Save
Stock:                                             Update on Save
Product Price:                                     Update on Save
Catalog Search:                                    Update on Save
```

### Konfigurera indexerare

>[!INFO]
>
>Innan du byter indexeringsläge rekommenderar vi att du skickar webbplatsen till [underhåll](../../installation/tutorials/maintenance-mode.md) läge och [inaktivera cron-jobb](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html#disable-cron-jobs). Detta säkerställer att du inte drabbas av databaslås.

Så här anger du indexerarkonfigurationen:

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

Var:

- `realtime`—Anger att de valda indexerarna ska uppdateras när de sparas.
- `schedule`- Anger att angivna indexerare ska sparas enligt cron-schemat.
- `indexer`—Är en blankstegsavgränsad lista med indexerare. Uteslut `indexer` om du vill konfigurera alla indexerare på samma sätt.

Om du till exempel bara vill ändra indexerare för kategoriprodukter och produktkategorier så att de uppdateras enligt schema anger du:

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

Exempelresultat:

```terminal
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

De indexerarrelaterade databasutlösarna läggs till när indexeringsläget är inställt på `schedule` och tas bort när indexerarläget är inställt på `realtime`. Om utlösarna saknas i databasen när indexerarna är inställda på `schedule`, ändra indexerare till `realtime` och sedan ändra tillbaka dem till `schedule`. Detta återställer utlösarna.
