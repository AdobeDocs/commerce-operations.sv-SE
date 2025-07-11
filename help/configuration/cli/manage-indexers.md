---
title: Hantera indexerare
description: Se exempel på hur du visar och hanterar Commerce-indexerare.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: ceefb9371dd0a85046cc5bfc0ddc72144d649608
workflow-type: tm+mt
source-wordcount: '964'
ht-degree: 0%

---

# Hantera indexerare

{{file-system-owner}}

Så här visar du en lista över alla indexerare:

```bash
bin/magento indexer:info
```

Listan visas enligt följande:

```text
cataloginventory_stock                   Stock
design_config_grid                       Design Config Grid
customer_grid                            Customer Grid
catalog_category_product                 Category Products
catalog_product_category                 Product Categories
catalogrule_rule                         Catalog Rule Product
catalog_product_attribute                Product EAV
inventory                                Inventory
catalog_product_price                    Product Price
catalogrule_product                      Catalog Product Rule
targetrule_product_rule                  Product/Target Rule
targetrule_rule_product                  Target Rule/Product
catalogsearch_fulltext                   Catalog Search
salesrule_rule                           Sales Rule
sales_order_data_exporter                Sales Order Feed
sales_order_status_data_exporter         Sales Order Statuses Feed
store_data_exporter                      Stores Feed
```

>[!NOTE]
>
> Adobe Commerce-handlare som använder Live Search, Catalog Service eller Produktrekommendationer har möjlighet att använda [SaaS-baserad prisindexering](https://experienceleague.adobe.com/sv/docs/commerce/price-indexer/price-indexing).

## Visa indexeringsstatus

Med det här kommandot kan du visa status för alla indexerare eller specifika indexerare. Ta till exempel reda på om en indexerare behöver indexeras om.

Kommandoalternativ:

```bash
bin/magento indexer:status [indexer]
```

Där `[indexer]` är en blankstegsavgränsad lista med indexerare. Uteslut `[indexer]` om du vill visa status för alla indexerare.

Exempelresultat:

```text
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
| ID                               | Title                     | Status | Update On | Schedule Status     | Schedule Updated    |
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
| catalogrule_product              | Catalog Product Rule      | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:52 |
| catalogrule_rule                 | Catalog Rule Product      | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:52 |
| catalogsearch_fulltext           | Catalog Search            | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:01:02 |
| catalog_category_product         | Category Products         | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:33 |
| customer_grid                    | Customer Grid             | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| design_config_grid               | Design Config Grid        | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| inventory                        | Inventory                 | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:36 |
| catalog_product_category         | Product Categories        | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:33 |
| catalog_product_attribute        | Product EAV               | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:36 |
| catalog_product_price            | Product Price             | Ready  | Schedule  | idle (0 in backlog) | 2025-07-11 08:00:54 |
| targetrule_product_rule          | Product/Target Rule       | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:39 |
| sales_order_data_exporter        | Sales Order Feed          | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| sales_order_status_data_exporter | Sales Order Statuses Feed | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| salesrule_rule                   | Sales Rule                | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:10 |
| cataloginventory_stock           | Stock                     | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:31 |
| store_data_exporter              | Stores Feed               | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:12:11 |
| targetrule_rule_product          | Target Rule/Product       | Ready  | Schedule  | idle (0 in backlog) | 2025-06-03 14:11:39 |
+----------------------------------+---------------------------+--------+-----------+---------------------+---------------------+
```

## Indexera om

Med det här kommandot kan du indexera om alla eller markerade indexerare endast en gång.

>[!INFO]
>
>Detta kommando indexerar bara en gång. Om du vill hålla indexerare uppdaterade måste du konfigurera ett [cron-jobb](../cli/configure-cron-jobs.md).

Kommandoalternativ:

```bash
bin/magento indexer:reindex [indexer]
```

Där `[indexer]` är en blankstegsavgränsad lista med indexerare. Uteslut `[indexer]` om du vill indexera om alla indexerare.

Exempelresultat:

```text
Stock index has been rebuilt successfully in <time>
Design Config Grid index has been rebuilt successfully in <time>
Customer Grid index has been rebuilt successfully in <time>
Category Products index has been rebuilt successfully in <time>
Product Categories index has been rebuilt successfully in <time>
Catalog Rule Product index has been rebuilt successfully in <time>
Product EAV index has been rebuilt successfully in <time>
Inventory index has been rebuilt successfully in <time>
Product Price index has been rebuilt successfully in <time>
Catalog Product Rule index has been rebuilt successfully in <time>
Product/Target Rule index has been rebuilt successfully in <time>
Target Rule/Product index has been rebuilt successfully in <time>
Catalog Search index has been rebuilt successfully in <time>
Sales Rule index has been rebuilt successfully in <time>
Sales Order Feed index has been rebuilt successfully in <time>
Sales Order Statuses Feed index has been rebuilt successfully in <time>
Stores Feed index has been rebuilt successfully in <time>
```

>[!INFO]
>
>Det kan ta lång tid att indexera om alla indexerare för butiker med ett stort antal produkter, kunder, kategorier och kampanjregler.

### Omindexering i parallellt läge

{{php-process-control}}

Indexerare har omfång och flertrådsteknik som stöder omindexering i parallellt läge. Den är parallell med indexerarens dimension och körs över flera trådar, vilket minskar bearbetningstiden.

I det här sammanhanget är `dimension` omindexeringens omfång, till exempel `website` eller bara en specifik `customer_group`.

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

Om du vill indexera om i parallellt läge kör du kommandot reindex med miljövariabeln `MAGE_INDEXER_THREADS_COUNT` eller lägger till en miljövariabel i filen `env.php`. Den här variabeln anger antalet trådar för omindexeringsbearbetningen.

Följande kommando kör indexeraren `Catalog Search Fulltext` över tre trådar:

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## Återställ indexerare

Använd det här kommandot om du vill göra alla indexerare eller specifika indexerare ogiltiga.

Kommandoalternativ:

```bash
bin/magento indexer:reset [indexer]
```

Där ```[indexer]``` är en blankstegsavgränsad lista med indexerare. Uteslut `[indexer]` om du vill göra alla indexerare ogiltiga.

Exempelresultat:

```text
Stock indexer has been invalidated.
Design Config Grid indexer has been invalidated.
Customer Grid indexer has been invalidated.
Category Products indexer has been invalidated.
Product Categories indexer has been invalidated.
Catalog Rule Product indexer has been invalidated.
Product EAV indexer has been invalidated.
Inventory indexer has been invalidated.
Product Price indexer has been invalidated.
Catalog Product Rule indexer has been invalidated.
Product/Target Rule indexer has been invalidated.
Target Rule/Product indexer has been invalidated.
Catalog Search indexer has been invalidated.
Sales Rule indexer has been invalidated.
Sales Order Feed indexer has been invalidated.
Sales Order Statuses Feed indexer has been invalidated.
Stores Feed indexer has been invalidated.
```

## Konfigurera indexerare

Använd det här kommandot för att ange följande indexeringsalternativ:

- **Uppdatera vid sparande (`realtime`)**: Indexerade data uppdateras när en ändring görs i administratören. (Exempel: kategoriproduktindexet indexeras om efter att produkterna har lagts till i en kategori i Admin.)
- **Uppdatera enligt schema (`schedule`)**: Data indexeras enligt det schema som angetts av ditt cron-jobb.

[Läs mer om indexering](https://developer.adobe.com/commerce/php/development/components/indexing/).

### Visa den aktuella konfigurationen

Så här visar du den aktuella indexerarkonfigurationen:

```bash
bin/magento indexer:show-mode [indexer]
```

Där `[indexer]` är en blankstegsavgränsad lista med indexerare. Uteslut `[indexer]` om du vill visa alla indexeringslägen. Om du till exempel vill visa läget för alla indexerare:

Exempelresultat:

```text
Stock:                                             Update by Schedule
Design Config Grid:                                Update by Schedule
Customer Grid:                                     Update by Schedule
Category Products:                                 Update by Schedule
Product Categories:                                Update by Schedule
Catalog Rule Product:                              Update by Schedule
Product EAV:                                       Update by Schedule
Inventory:                                         Update by Schedule
Product Price:                                     Update by Schedule
Catalog Product Rule:                              Update by Schedule
Product/Target Rule:                               Update by Schedule
Target Rule/Product:                               Update by Schedule
Catalog Search:                                    Update by Schedule
Sales Rule:                                        Update by Schedule
Sales Order Feed:                                  Update by Schedule
Sales Order Statuses Feed:                         Update by Schedule
Stores Feed:                                       Update by Schedule
```

### Ange indexeringsläge

>[!IMPORTANT]
>
>Indexerarens [!DNL Customer Grid]-beteende ändrades i 2.4.8:
>
>- **Före 2.4.8**: [!DNL Customer Grid]-indexeraren kan bara indexeras om med alternativet [!UICONTROL Update on Save] och stöder inte alternativet [!UICONTROL Update by Schedule].
>
>   Använd följande kommando för att ställa in den här indexeraren så att den uppdateras när den sparas:
>
>   ```bash
>   bin/magento indexer:set-mode realtime customer_grid
>   ```
>
>- **2.4.8 och senare**: [!DNL Customer Grid]-indexeraren har stöd för både [!UICONTROL Update on Save]- och [!UICONTROL Update by Schedule]-lägen, och standardvärdet är [!UICONTROL Update by Schedule].
>
>Se [Bästa tillvägagångssätt för indexerarkonfiguration](https://experienceleague.adobe.com/sv/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration) i _Implementeringsspelningsboken_.

>[!INFO]
>
>Innan du växlar mellan indexeringslägen anger du att webbplatsen ska vara i [underhållsläge](../../installation/tutorials/maintenance-mode.md) och [inaktivera cron-jobb](https://experienceleague.adobe.com/sv/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property). Detta garanterar att du inte får några databaslås.

Så här anger du indexerarkonfigurationen:

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

Var:

- `realtime` - Anger att de valda indexerarna ska uppdateras när de sparas.
- `schedule` - Anger att angivna indexerare ska sparas enligt cron-schemat.
- `indexer` - Är en blankstegsavgränsad lista med indexerare. Uteslut `indexer` om du vill konfigurera alla indexerare på samma sätt.

Om du till exempel bara vill ändra indexerare för kategoriprodukter och produktkategorier så att de uppdateras enligt schema anger du:

```bash
bin/magento indexer:set-mode schedule catalog_category_product catalog_product_category
```

Exempelresultat:

```
Index mode for Indexer Category Products was changed from 'Update on Save' to 'Update by Schedule'
Index mode for Indexer Product Categories was changed from 'Update on Save' to 'Update by Schedule'
```

De indexerarrelaterade databasutlösarna läggs till när indexeringsläget är inställt på `schedule` och tas bort när indexeringsläget är inställt på `realtime`. Om utlösarna saknas i databasen när indexerarna är inställda på `schedule` ändrar du indexerarna till `realtime` och ändrar dem sedan tillbaka till `schedule`. Detta återställer utlösarna.

### Ange indexeringsstatus

Kommandot `bin/magento indexer:set-status` introducerades i Adobe Commerce 2.4.7. Det gör att administratörer kan ändra driftstatusen för en eller flera indexerare och optimera systemprestanda vid omfattande åtgärder som import, uppdatering eller underhåll av data.

Kommandosyntax:

```bash
bin/magento indexer:set-status {invalid|suspended|valid} [indexer]
```

Var:

- `invalid` - Markerar indexerare som inaktuella och uppmanar till omindexering vid nästa kron-körning om de inte har pausats.
- `suspended` - Avbryter tillfälligt automatiskt kroniskt utlösta uppdateringar för indexerare. Den här statusen gäller för både realtids- och schemalägen, vilket säkerställer att automatiska uppdateringar pausas under intensiva operationer.
- `valid` - Anger att indexeringsdata är aktuella och att ingen omindexering behöver göras.
- `indexer` - Är en blankstegsavgränsad lista med indexerare. Uteslut `indexer` om du vill konfigurera alla indexerare på samma sätt.

Om du till exempel vill göra uppehåll i vissa indexerare anger du:

```bash
bin/magento indexer:set-status suspended catalog_category_product catalog_product_category
```

Exempelresultat:

```
Index status for Indexer 'Category Products' was changed from 'valid' to 'suspended'.
Index status for Indexer 'Product Categories' was changed from 'valid' to 'suspended'.
```

#### Hantera status för pausad indexerare

När en indexerare har statusen `suspended` påverkas i första hand automatisk omindexering och materialiserade vyuppdateringar. Här är en kort översikt:

**Omindexering hoppades över**: Systemet hoppar över automatisk omindexering för `suspended` indexerare och alla indexerare som delar samma `shared_index`. På så sätt sparar du systemresurser genom att undvika omindexering av data som är relaterade till avbrutna processer.

**Uppdateringar av materialiserad vy som hoppats över**: På samma sätt som omindexering pausas även uppdateringar av materialiserade vyer relaterade till `suspended`-indexerare eller deras delade index. Den här pausen minskar systembelastningen ytterligare under uppehållsperioder.

>[!INFO]
>
>Kommandot `indexer:reindex` indexerar om alla indexerare, inklusive indexerare som markerats som `suspended`, vilket gör det användbart för manuella uppdateringar när automatiska uppdateringar pausas.

>[!IMPORTANT]
>
>Om du ändrar en indexerares status till `valid` från `suspended` eller `invalid` måste du vara försiktig. Den här åtgärden kan leda till prestandaförsämring om det finns samlade oindexerade data.
>
>Det är viktigt att se till att alla data indexeras korrekt innan du manuellt uppdaterar statusen till `valid` för att behålla systemprestanda och dataintegritet.
