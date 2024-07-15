---
title: Konfigurera sökstoppord
description: Lär dig hur du hanterar stoppord för Adobe Commerce med CSV-filer.
feature: Configuration, Search
exl-id: 75320868-9939-4a6e-8dbb-73ca68c9f0ee
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# Konfigurera sökstoppord

Vanligtvis är _stoppord_ vanliga ord som sökmotorer filtrerar ut efter att ha bearbetat text. När diskutrymmet och minnet ursprungligen var extremt begränsat innebar varje kilobyte som sparades en avsevärd prestandaförbättring. Därför har sökmotorer fått prestandavinster genom att ignorera vissa ord och hålla indexet litet.

Trots att vi har mer lagringsutrymme idag är prestanda fortfarande viktigt. Elasticsearch och OpenSearch använder, precis som andra sökmotorer, fortfarande stoppord för att förbättra prestandan.

Du måste hantera dina stoppord med hjälp av CSV-filer som finns i katalogen `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` eller `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`, beroende på hur du har installerat Commerce.

Mer information om hur Elasticsearch och OpenSearch använder stoppord finns i följande resurser:

- [Stoppord: Prestanda jämfört med Precision](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [För- och nackdelar med stoppord](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [Använder stoppord](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [Stoppord och prestanda](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## Konfigurera stoppord

Stoppord finns i katalogen `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`. Adobe Commerce levereras med en CSV-fil som innehåller stoppord för standardspråkinställningarna och ytterligare en fil, `stopwords.csv`, som har stoppord för alla språkinställningar som inte representeras av en annan CSV-fil.

Standardlivstiden för stoppordsfilcachen är 15 minuter.

### Redigera stoppord för en befintlig språkinställning

**Så här redigerar du stoppord**:

1. Logga in på din Commerce-server eller växla till [filsystemsägaren](../../installation/prerequisites/file-system/overview.md).
1. Använd en textredigerare för att öppna en stoppordsfil i katalogen `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`.

   CSV-filer använder namnkonventionen `stopwords_<locale_code>.csv`. Exempel: Den tyska stoppordsfilen heter `stopwords_de_DE.csv`.

1. Lägg till ord, ta bort ord eller ändra ord i filen.

   (Varje stoppord i en fil börjar på en ny rad.)

1. Spara ändringarna och avsluta textredigeraren.
1. Rensa konfigurationscachen.

   - Admin: **System** > Verktyg > **Cachehantering**. Markera kryssrutan **Konfiguration** och klicka på **Uppdatera** i listan ovan. Klicka på **Skicka** för att slutföra åtgärden.

   - Kommandorad: Ange följande kommando som ägare av filsystemet:

     ```bash
     php <magento_root>/bin/magento cache:clean config
     ```

1. Kontrollera resultatet genom att söka efter termer i butiken.

### Skapa stoppord för en ny språkinställning

**Så här lägger du till stoppord för en språkinställning**:

1. Logga in på din Commerce-server eller växla till [filsystemsägaren](../../installation/prerequisites/file-system/overview.md).

1. Använd en textredigerare för att skapa en stoppordsfil med namnet `stopwords_<locale_code>.csv` i katalogen `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`.

   Om du till exempel vill skapa stoppord för den italienska språkinställningen ger du filen `stopwords_it_IT.csv` ett namn.

1. Kontrollera att varje stoppord finns på en separat rad i stoppordsfilen.
1. Spara ändringarna och avsluta textredigeraren.
1. Öppna `esconfig.xml` i en textredigerare i samma katalog.
1. Lägg till en rad i `esconfig.xml` enligt följande:

   ```xml
   <LOCALE_CODE>stopwords_LOCALE_CODE.csv</LOCALE_CODE>
   ```

   Om du till exempel vill lägga till en italiensk stoppordsfil lägger du till följande rad:

   ```xml
   <it_IT>stopwords_it_IT.csv</it_IT>
   ```

1. Spara ändringarna i `esconfig.xml` och avsluta textredigeraren.
1. Rensa konfigurationscachen.

   - Admin: **System** > Verktyg > **Cachehantering**. Markera kryssrutan **Konfiguration** och klicka på **Uppdatera** i listan ovan. Klicka på **Skicka** för att slutföra åtgärden.

   - Kommandorad: Ange följande kommando som ägare av filsystemet:

     ```bash
     php <magento_root>/bin/magento magento cache:clean config
     ```

1. Kontrollera resultatet genom att söka efter termer i butiken.

## Ändra stoppordskatalogen

I det här avsnittet beskrivs hur du kan ändra standardkatalogen för stoppord från något av följande:

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

Platsen beror på hur du har installerat Commerce. Om du klonade GitHub-databasen Magento 2 är sökvägen under `app/code`. Om du installerade ett komprimerat arkiv eller ett metapaket är sökvägen under `vendor`.

**Så här ändrar du katalogen**:

1. Som ägare av filsystemet öppnar du Elasticsearch `di.xml` i en textredigerare.

   Om du klonade databasen finns den på `app/code/Magento/Elasticsearch/etc/di.xml`

   Om du har ett arkiv eller metapaketet finns det på `vendor/magento/module-elasticsearch/etc/di.xml`

1. Ändra värdet för `stopwordsDirectory` till önskad katalog:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. Spara ändringarna i `di.xml` och avsluta textredigeraren.

## Ändra katalogen från modulen

1. [Skapa en modul](https://developer.adobe.com/commerce/php/development/build/component-file-structure/)
1. Lägg till instruktioner i modulen `etc/di.xml`:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. Skapa katalogen `etc/stopwords` i modulen med motsvarande CSV-fil.

1. Spara ändringarna i `di.xml` och avsluta textredigeraren.
