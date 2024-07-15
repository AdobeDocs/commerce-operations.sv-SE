---
title: Generera data för prestandatestning
description: Lär dig hur du genererar en stor mängd data som ska användas för prestandatestning.
feature: Configuration, Orders
exl-id: 2f54701d-88c4-464a-b4dc-56db14d54160
source-git-commit: d4a6d5cd181c7c4426914bbe481f4d5d1e828b5e
workflow-type: tm+mt
source-wordcount: '762'
ht-degree: 9%

---

# Prestandatestningsdata

## Profiler

Du kan justera mängden data som du skapar med _profiler_ (liten, mellanstor, stor och extra stor). Profilerna finns i katalogen `<magento_root>/setup/performance-toolkit/profiles/<ce|ee>`.

Exempel: `/var/www/html/magento2/setup/performance-toolkit/profiles/ce`

Följande bild visar hur en produkt visas på butiken med profilen _small_:

![Exempelarkiv med genererade data](../../assets/configuration/generate-data.png)

Följande tabell innehåller information om datageneratorprofilerna: small, medium, large och extra large.

| Parameter | Liten profil | Medium | Medium-profil för flera webbplatser | Stor profil | Extra stor profil |
| --- | --- | --- | --- | --- | --- |
| `websites` | 1 | 3 | 25 | 5 | 5 |
| `store_groups` | 1 | 3 | 25 | 5 | 5 |
| `store_views` | 1 | 3 | 50 | 5 | 5 |
| `simple_products` | 800 | 24 000 | 4 000 | 300 000 | 600 000 |
| `configurable_products` | 16 med 24 alternativ | 640 med 24 alternativ | 800 med 24 alternativ och 79 med 200 alternativ | 8 000 med 24 alternativ | 16 000 med 24 alternativ |
| `product_images` | 100 bilder/3 bilder per produkt | 1 000 bilder/3 bilder per produkt | 1 000 bilder/3 bilder per produkt | 2 000 bilder/3 bilder per produkt | 2 000 bilder/3 bilder per produkt |
| `categories` | 30 | 300 | 100 | 3 000 | 6 000 |
| `categories_nesting_level` | 3 | 3 | 3 | 5 | 5 |
| `catalog_price_rules` | 20 | 20 | 20 | 20 | 20 |
| `catalog_target_rules` | 5 | 5 | 5 | 5 | 5 |
| `cart_price_rules` | 20 | 20 | 20 | 20 | 20 |
| `cart_price_rules_floor` | 2 | 2 | 2 | 2 | 2 |
| `customers` | 200 | 2 000 | 2 000 | 5 000 | 10 000 |
| `tax rates` | 130 | 40 000 | 40 000 | 40 000 | 40 000 |
| `orders` | 80 | 50 000 | 50 000 | 100 000 | 150 000 |

### Kör datageneratorn

{{file-system-owner}}

>[!WARNING]
>
>Innan du kör datageneratorn ska du inaktivera alla cron-jobb som körs på servern. Genom att inaktivera cron-jobb förhindrar du att datageneratorn utför åtgärder som hamnar i konflikt med aktiva cron-jobb och undviker onödiga fel.
>
>Om du tänker implementera en händelse med [!DNL Adobe I/O Events for Adobe Commerce] när du testar prestanda kör du det här kommandot innan du prenumererar på [händelser](https://developer.adobe.com/commerce/extensibility/events/). Prenumerationshändelser kan orsaka fel.

Kör kommandot enligt beskrivningen i det här avsnittet. När kommandot har körts måste du [indexera om alla indexerare](../cli/manage-indexers.md).

Kommandoalternativ:

```bash
bin/magento setup:perf:generate-fixtures <path-to-profile>
```

Där `<path-to-profile>` anger den absoluta filsystemsökvägen till och namnet på en profil.

Exempel:

```bash
bin/magento setup:perf:generate-fixtures /var/www/html/magento2/setup/performance-toolkit/profiles/ce/small.xml
```

Exempelutdata för den lilla profilen:

```terminal
Generating profile with following params:
    |- Websites: 1
    |- Store Groups Count: 1
    |- Store Views Count: 1
    |- Categories: 30
    |- Attribute Sets (Default): 3
    |- Attribute Sets (Extra): 10
    |- Simple products: 800
    |- Configurable products: 0
    |--- 5 products for attribute set "Attribute Set 1"
    |--- 5 products for attribute set "Attribute Set 2"
    |--- 5 products for attribute set "Attribute Set 3"
    |--- 40 products for attribute set "Dynamic Attribute Set 1-24"
    |- Product images: 100, 3 per product
    |- Customers: 200
    |- Cart Price Rules: 20
    |- Catalog Price Rules: 20
    |- Catalog Target Rules: 5
    |- Orders: 80
Generating websites, stores and store views...  done in <time>
Generating categories...  done in <time>
Generating attribute sets...  done in <time>
Generating simple products...  done in <time>
... more ...
```

## Prestandakorrigeringar

### Administratörer

Skapar administratörsanvändare. XML-profilnod:

```xml
<!-- Number of admin users -->
<admin_users>{int}</admin_users>
```

### Attributuppsättningar

Genererar attributuppsättningar med angiven konfiguration. XML-profilnod:

```xml
<!-- Number of product attribute sets -->
<product_attribute_sets>{int}</product_attribute_sets>

<!-- Number of attributes per set -->
<product_attribute_sets_attributes>{int}</product_attribute_sets_attributes>

<!-- Number of values per attribute -->
<product_attribute_sets_attributes_values>{int}</product_attribute_sets_attributes_values>
```

### Paketprodukter

Skapar paketprodukter. Genererade paketmarkeringar visas inte individuellt i katalogen. Produkterna är jämnt fördelade per kategori och webbplats. Om `assign_entities_to_all_websites` från profilen är inställd på `1`. Produkterna tilldelas alla webbplatser.

XML-profilnod:

```xml
<!-- Number of products -->
<bundle_products>{int}</bundle_products>

<!-- Number of options per each product -->
<bundle_products_options>{int}</bundle_products_options>

<!-- Number of simple products per each option -->
<bundle_products_variation>{int}</bundle_products_variation>
```

### Kundprisregler

Genererar kundvagnsprisregler. XML-profilnod:

```xml
<!-- Number of cart price rules -->
<cart_price_rules>{int}</cart_price_rules>

<!-- Number of conditions per rule -->
<cart_price_rules_floor>{int}</cart_price_rules_floor>
```

### Katalogprisregler

Skapar katalogprisregler. XML-profilnod:

```xml
<!-- Number of catalog price rules -->
<catalog_price_rules>{int}</catalog_price_rules>
```

### Kategorier

Genererar kategorier. Om `assign_entities_to_all_websites` är inställt på `0` fördelas alla kategorier jämnt per rotkategori, annars tilldelas alla kategorier till en rotkategori.

XML-profilnod:

```xml
<!-- Number of categories to generate -->
<categories>{int}</categories>

<!-- Nesting level of categories -->
<categories_nesting_level>{int}</categories_nesting_level>
```

### Konfigurationer

Anger värden för konfigurationsfält. XML-profilnod:

```xml
<!-- Config variables and values for change -->
<configs>
    <config>
        <path>{string}</path> <!-- e.g. admin/security/use_form_key -->
        <scope>{string}</scope> <!-- e.g. default -->
        <scopeId>{int}</scopeId>
        <value>{int|string}</value>
    </config>

    <!-- ... more entries ... -->
</configs>
```

### Konfigurerbara produkter

Skapar konfigurerbara produkter. Genererade konfigurerbara alternativ visas inte individuellt i katalogen. Produkterna är jämnt fördelade per kategori och webbplats. Om `assign_entities_to_all_websites` är `1` tilldelas produkter till alla webbplatser.

Följande XML-nodformat stöds:

- Distribution per Default och fördefinierade attributuppsättningar:

  ```xml
  <!-- Number of configurable products -->
  <configurable_products>{int}</configurable_products>
  ```

- Generera produkter baserat på en befintlig attributuppsättning:

  ```xml
  <configurable_products>
  
      <config>
              <!-- Existing attribute set name -->
              <attributeSet>{string}</attributeSet>
  
              <!-- Configurable sku pattern with %s -->
              <sku>{string}</sku>
  
              <!-- Number of configurable products -->
              <products>{int}</products>
  
              <!-- Category Name. Optional. By default category name from Categories fixture will be used -->
              <category>[{string}]</category>
  
              <!-- Type of Swatch attribute e.g. color|image -->
              <swatches>{string}</swatches>
      </config>
  
  <!-- ... more entries ... -->
  </configurable_products>
  ```

- Generera produkter baserat på en dynamiskt skapad attributuppsättning med ett angivet antal attribut och alternativ:

  ```xml
  <configurable_products>
  
      <config>
          <!-- Number of attributes in configurable product -->
          <attributes>{int}</attributes>
  
          <!-- Number of options per attribute -->
          <options>{int}</options>
  
          <!-- Configurable sku pattern with %s -->
          <sku>{string}</sku>
  
          <!-- Number of configurable products -->
          <products>{int}</products>
  
          <!-- Category Name. Optional. By default category name from Categories fixture will be used -->
          <category>[{string}]</category>
  
          <!-- Type of Swatch attribute e.g. color|image -->
          <swatches>{string}</swatches>
      </config>
  
      <!-- ... more entries ... -->
  </configurable_products>
  ```

- Generera produkter baserat på en dynamiskt skapad attributuppsättning med en angiven konfiguration för varje attribut:

  ```xml
  <configurable_products>
  
      <config>
          <attributes>
              <!-- Configuration for a first attribute -->
              <attribute>
                  <!-- Amount of options per attribute -->
                  <options>{int}</options>
  
                  <!-- Type of Swatch attribute -->
                  <swatches>{string}</swatches>
              </attribute>
  
              <!-- Configuration for a second attribute -->
              <attribute>
                  <!-- Amount of options per attribute -->
                  <options>{int}</options>
              </attribute>
          </attributes>
  
          <!-- Configurable sku pattern with %s -->
          <sku>{string}</sku>
  
          <!-- Number of configurable products -->
          <products>{int}</products>
  
          <!-- Category Name. Optional. By default, the category name from Categories fixture will be used -->
          <category>[{string}]</category>
      </config>
  
      <!-- ... more entries ... -->
  </configurable_products>
  ```

### Kunder

Skapar kunder. Kunderna distribueras normalt på alla tillgängliga webbplatser. Alla kunder har samma data förutom kundens e-postadress, kundgrupp och kundadresser.

XML-profilnod:

```xml
<!-- Number of customers to generate -->
<customers>{int}</customers>
```

Du kan använda följande XML för att ändra kundkonfigurationen:

```xml
<customer-config>
    <!-- Number of addresses per each customer -->
    <addresses-count>{int}</addresses-count>
</customer-config>
```

### Produktbilder

Genererar produktbilder. Storleksändring ingår inte i genereringen.

XML-profilnod:

```xml
<product-images>
    <!-- Number of images to generate -->
    <images-count>{int}</images-count>

    <!-- Number of images to be assigned per each product -->
    <images-per-product>{int}</images-per-product>
</product-images>
```

### Indexerarläge

Uppdaterar indexerarens tillstånd. XML-profilnod:

```xml
<indexer>
    <!-- Name of indexer (e.g. catalogrule_product) -->
    <id>{string}</id>
    <set_scheduled>{bool}</set_scheduled>
</indexer>
```

### Beställningar

Genererar order med ett konfigurerbart antal olika typer av orderartiklar. Alternativt genereras inaktiva offerter för genererade order.

XML-profilnod:

```xml
<!-- It is necessary to enable quotes for orders -->
<order_quotes_enable>{bool}</order_quotes_enable>

<!-- Min number of simple products per each order -->
<order_simple_product_count_from>{int}</order_simple_product_count_from>

<!-- Max number of simple products per each order -->
<order_simple_product_count_to>{int}</order_simple_product_count_to>

<!-- Min number of configurable products per each order -->
<order_configurable_product_count_from>{int}</order_configurable_product_count_from>

<!-- Max number of configurable products per each order -->
<order_configurable_product_count_to>{int}</order_configurable_product_count_to>

<!-- Min number of big configurable products (with big amount of options) per each order -->
<order_big_configurable_product_count_from>{int}</order_big_configurable_product_count_from>

<!-- Max number of big configurable products (with big amount of options) per each order -->
<order_big_configurable_product_count_to>{int}</order_big_configurable_product_count_to>

<!-- Number of orders to generate -->
<orders>{int}</orders>
```

### Enkla produkter

Genererar enkla produkter. Produkterna distribueras per standard och fördefinierade attributuppsättningar. Om extra attributuppsättningar anges i profilen som: `<product_attribute_sets>{int}</product_attribute_sets>`, fördelas produkterna även per ytterligare attributuppsättningar.

Produkterna är jämnt fördelade per kategori och webbplats. Om `assign_entities_to_all_websites` är `1` tilldelas produkter till alla webbplatser.

XML-profilnod:

```xml
<!-- Number of simple products to generate -->
<simple_products>{int}</simple_products>
```

### Webbplatser

Skapar webbplatser. XML-profilnod:

```xml
<!-- Number of websites to be generated -->
<websites>{int}</websites>
```

### Butiksgrupper

Skapar butiksgrupper (som i administratören kallas _butiker_). Butiksgrupper distribueras normalt mellan webbplatser.

XML-profilnod:

```xml
<!-- Number of store groups to be generated -->
<store_groups>{int}</store_groups>
```

### Butiksvyer

Skapar butiksvyer. Butiksvyer distribueras normalt mellan butiksgrupper. XML-profilnod:

```xml
<!-- Number of store views to be generated -->
<store_views>{int}</store_views>

<!-- 1 means that all stores will have the same root category, 0 means that all stores will have unique root category -->
<assign_entities_to_all_websites>{0|1}<assign_entities_to_all_websites/>
```

### Skattesatser

Genererar momssatser. XML-profilnod:

```xml
<!-- Accepts name of CSV file with tax rates (<path to Commerce folder>/setup/src/Magento/Setup/Fixtures/_files) -->
<tax_rates_file>{CSV file name}</tax_rates_file>
```

## Ytterligare konfigurationsinformation:

- `<Commerce root dir>/setup/performance-toolkit/config/attributeSets.xml` - Standardattributuppsättningar

- `<Commerce root dir>/setup/performance-toolkit/config/customerConfig.xml` - Kundkonfiguration

- `<Commerce root dir>/setup/performance-toolkit/config/description.xml` - Konfiguration av fullständig produktbeskrivning

- `<Commerce root dir>/setup/performance-toolkit/config/shortDescription.xml` - Konfiguration av kort produktbeskrivning

- `<Commerce root dir>/setup/performance-toolkit/config/searchConfig.xml` - Konfiguration för kort och fullständig beskrivning av produkten. Den här äldre implementeringen tillhandahålls för bakåtkompatibilitet.

- `<Commerce root dir>/setup/performance-toolkit/config/searchTerms.xml` - Ett litet antal söktermer i korta och fullständiga beskrivningar

- `<Commerce root dir>/setup/performance-toolkit/config/searchTermsLarge.xml` - Större antal söktermer att använda i kort och fullständig beskrivning.
