---
title: Hantera indexerarna
description: Se exempel på hur du visar och hanterar Commerce-indexerare.
exl-id: d2cd1399-231e-4c42-aa0c-c2ed5d7557a0
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 0%

---

# Hantera indexerarna

{{file-system-owner}}

Så här visar du en lista över alla indexerare:

```bash
bin/magento indexer:info
```

Listan visas på följande sätt:

```
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
> Adobe Commerce-handlare som använder Live Search, Catalog Service eller Product Recommendations har möjlighet att använda [SaaS-baserad prisindexering](https://experienceleague.adobe.com/docs/commerce/price-indexer/index.html).

## Visa indexeringsstatus

Med det här kommandot kan du visa status för alla indexerare eller specifika indexerare. Ta till exempel reda på om en indexerare behöver indexeras om.

Kommandoalternativ:

```bash
bin/magento indexer:status [indexer]
```

Där `[indexer]` är en blankstegsavgränsad lista med indexerare. Uteslut `[indexer]` om du vill visa status för alla indexerare.

Exempelresultat:

```
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
>Detta kommando indexerar bara en gång. Om du vill hålla indexerare uppdaterade måste du konfigurera ett [cron-jobb](../cli/configure-cron-jobs.md).

Kommandoalternativ:

```bash
bin/magento indexer:reindex [indexer]
```

Där `[indexer]` är en blankstegsavgränsad lista med indexerare. Uteslut `[indexer]` om du vill indexera om alla indexerare.

Exempelresultat:

```
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

I det här sammanhanget är `dimension` omindexeringens omfång, till exempel `website` eller bara en specifik `customer_group`.

Indexparallelliseringen påverkar bara omfångsindexerare, vilket innebär att Commerce delar upp data i flera tabeller med indexeraren som omfång i stället för att lagra alla data i en tabell.

Du kan köra följande index i parallellt läge:

- `Catalog Search Fulltext` kan jämföras med butiksvyer.
- `Category Product` kan jämföras med butiksvyer.
- `Catalog Price` kan kombineras av webbplats- och kundgrupper.
- `Catalog Permissions` kan jämföras med kundgrupper.

>[!INFO]
>
>Parallellisering för katalogsökning, fulltext och kategoriprodukt är aktiverat som standard.

Om du vill använda parallellisering anger du ett av de tillgängliga dimensionslägena för produktprisindexeraren:

- `none` (standard)
- `website`
- `customer_group`
- `website_and_customer_group`

Om du till exempel vill ställa in läget per webbplats:

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

Om du vill indexera om i parallellt läge kör du kommandot reindex med hjälp av miljövariabeln `MAGE_INDEXER_THREADS_COUNT`eller lägger till en miljövariabel i `env.php` filen. Den här variabeln anger antalet trådar för omindexeringsbearbetningen.

Följande kommando kör till exempel indexeraren över `Catalog Search Fulltext` tre trådar:

```bash
MAGE_INDEXER_THREADS_COUNT=3 php -f bin/magento indexer:reindex catalogsearch_fulltext
```

## Återställa indexerare

Använd det här kommandot för att ogiltigförklara statusen för alla indexerare eller specifika indexerare.

Alternativ för kommandon:

```bash
bin/magento indexer:reset [indexer]
```

Var ```[indexer]``` finns en blankstegsavgränsad lista över indexerare. Utelämna `[indexer]` om du vill ogiltigförklara alla indexerare.

Exempel på resultat:

```
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

Använd det här kommandot för att ange följande indexeraralternativ:

- **Uppdatering när du sparar (`realtime`)**: Indexerad data uppdateras när en ändring görs i Admin. (Index för kategoriprodukter indexeras till exempel om efter att produkter har lagts till i en kategori i Admin.)
- **Uppdatera enligt schema (`schedule`)**: Data indexeras enligt det schema som ställts in av ditt cron-jobb.

[Läs mer om indexering](https://developer.adobe.com/commerce/php/development/components/indexing/).

### Visa den aktuella konfigurationen

Så här visar du den aktuella indexerarkonfigurationen:

```bash
bin/magento indexer:show-mode [indexer]
```

Var `[indexer]` finns en blankstegsavgränsad lista över indexerare. Utelämna `[indexer]` om du vill visa alla indexerares lägen. Om du till exempel vill visa läget för alla indexerare:

Exempelresultat:

```
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

### Ange indexerarläge

>[!IMPORTANT]
>
>Se till att ställa in med `realtime` i stället `schedule`för [!DNL Customer Grid] . Den [!DNL Customer Grid] kan endast indexeras om med hjälp av [!UICONTROL Update on Save] alternativet. Det här indexet stöder inte alternativet `Update by Schedule` . Använd följande kommandorad för att ställa in den här indexeraren så att den uppdateras när den sparas: `php bin/magento indexer:set-mode realtime customer_grid`
>
>Se [Metodtips för indexerarkonfiguration](https://experienceleague.adobe.com/docs/commerce-operations/implementation-playbook/best-practices/maintenance/indexer-configuration.html?lang=sv-SE) i implementeringsboken __.

>[!INFO]
>
>Innan du byter indexerarläge, ställ in din webbplats i [underhållsläge](../../installation/tutorials/maintenance-mode.md) och [inaktivera cron-jobb](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/properties/crons-property.html?lang=sv-SE#disable-cron-jobs). Detta säkerställer att du inte drabbas av databaslås.

Så här anger du indexerarkonfigurationen:

```bash
bin/magento indexer:set-mode {realtime|schedule} [indexer]
```

Var:

- `realtime`– Ställer in de valda indexerarna som ska uppdateras när de sparas.
- `schedule`– Ställer in de angivna indexerarna så att de sparas enligt cron-schemat.
- `indexer`– Är en blankstegsavgränsad lista över indexerare. Utelämna `indexer` om du vill konfigurera alla indexerare på samma sätt.

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

**Omindexering hoppades över**: Automatisk omindexering ignoreras för `suspended` indexerare och alla indexerare som delar samma `shared_index`. Detta garanterar att systemresurserna bevaras genom att inte omindexera data som hör till avbrutna processer.

**Uppdateringar av materialiserad vy som hoppats över**: Uppdateringar av materialiserade vyer som är relaterade till `suspended`-indexerare eller deras delade index pausas också, ungefär som omindexering. Den här åtgärden minskar systembelastningen ytterligare under uppehållsperioder.

>[!INFO]
>
>Kommandot `indexer:reindex` indexerar om alla indexerare, inklusive de som markerats som `suspended`, vilket gör det användbart för manuella uppdateringar när automatiska uppdateringar pausas.

>[!IMPORTANT]
>
>Om du ändrar en indexerares status till `valid` från `suspended` eller `invalid` måste du vara försiktig. Den här åtgärden kan leda till prestandaförsämring om det finns ackumulerade oindexerade data.
>
>Det är viktigt att se till att alla data indexeras korrekt innan du manuellt uppdaterar statusen för att `valid` upprätthålla systemets prestanda och dataintegritet.
