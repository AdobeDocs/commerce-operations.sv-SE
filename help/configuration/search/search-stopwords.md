---
title: Konfigurera sökstoppord
description: Lär dig hur du hanterar stoppord för Adobe Commerce med CSV-filer.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---


# Konfigurera sökstoppord

I allmänhet _stoppord_ är vanliga ord som sökmotorer filtrerar bort efter att ha bearbetat text. När diskutrymmet och minnet ursprungligen var extremt begränsat innebar varje kilobyte som sparades en avsevärd prestandaförbättring. Därför har sökmotorer fått prestandavinster genom att ignorera vissa ord och hålla indexet litet.

Trots att vi har mer lagringsutrymme idag är prestanda fortfarande viktigt. Elasticsearch och OpenSearch använder, precis som andra sökmotorer, fortfarande stoppord för att förbättra prestandan.

Du måste hantera dina stoppord med CSV-filer som finns i `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` katalogen eller `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/` -katalogen, beroende på hur du har installerat Commerce-programmet.

Mer information om hur Elasticsearch och OpenSearch använder stoppord finns i följande resurser:

- [Stoppord: Prestanda jämfört med precision](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords.html)
- [Pros and Cons of Stopwords](https://www.elastic.co/guide/en/elasticsearch/guide/current/pros-cons-stopwords.html)
- [Använda stoppord](https://www.elastic.co/guide/en/elasticsearch/guide/current/using-stopwords.html)
- [Stoppord och prestanda](https://www.elastic.co/guide/en/elasticsearch/guide/current/stopwords-performance.html)

## Konfigurera stoppord

Stoppord finns i `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` katalog. Adobe Commerce och Magento Open Source levereras med en CSV-fil som innehåller stoppord för standardspråkinställningarna och ytterligare en fil, `stopwords.csv`, som har stoppord för alla språk som inte representeras av en annan CSV-fil.

Standardlivstid för stoppordsfilen [cache](https://glossary.magento.com/cache) är 15 minuter.

### Redigera stoppord för en befintlig språkinställning

**Redigera stoppord**:

1. Logga in på din Commerce-server eller växla till [ägare av filsystem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Använda en textredigerare för att öppna en stoppordsfil i `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` katalog.

   CSV-filer använder namnkonventionen `stopwords_<locale_code>.csv`. Exempel: den tyska stoppordsfilen heter `stopwords_de_DE.csv`.

1. Lägg till ord, ta bort ord eller ändra ord i filen.

   (Varje stoppord i en fil börjar på en ny rad.)

1. Spara ändringarna och avsluta textredigeraren.
1. Rensa konfigurationscachen.

   - Administratör: **System** > Verktyg > **Cachehantering**. Välj **Konfiguration** och klicka på **Uppdatera**. Klicka **Skicka** för att slutföra åtgärden.

   - Kommandorad: Som ägare av filsystemet anger du följande kommando:

      ```bash
      php <magento_root>/bin/magento cache:clean config
      ```

1. Sök efter termer på [storefront](https://glossary.magento.com/storefront).

### Skapa stoppord för en ny språkinställning

**Lägga till stoppord för en språkinställning**:

1. Logga in på din Commerce-server eller växla till [ägare av filsystem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).

1. Använda en textredigerare för att skapa en stoppordsfil med namnet `stopwords_<locale_code>.csv` i `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords` katalog.

   Om du till exempel vill skapa stoppord för den italienska språkinställningen ger du filen ett namn `stopwords_it_IT.csv`.

1. Kontrollera att varje stoppord finns på en separat rad i stoppordsfilen.
1. Spara ändringarna och avsluta textredigeraren.
1. Öppna i samma katalog `esconfig.xml` i en textredigerare.
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

   - Administratör: **System** > Verktyg > **Cachehantering**. Välj **Konfiguration** och klicka på **Uppdatera**. Klicka **Skicka** för att slutföra åtgärden.

   - Kommandorad: Som ägare av filsystemet anger du följande kommando:

      ```bash
      php <magento_root>/bin/magento magento cache:clean config
      ```

1. Kontrollera resultatet genom att söka efter termer i din butik.

## Ändra stoppordskatalogen

I det här avsnittet beskrivs hur du kan ändra standardkatalogen för stoppord från något av följande:

- `<magento_root>/vendor/magento/module-elasticsearch/etc/stopwords`
- `<magento_root>/app/code/Magento/Elasticsearch/etc/stopwords/`

Platsen beror på hur du installerade Commerce-programmet. Om du klonade GitHub-databasen Magento 2 ligger sökvägen under `app/code`. Om du har installerat ett komprimerat arkiv eller ett metapaket är sökvägen under `vendor`.

**Ändra katalogen**:

1. Öppna Elasticsearch som ägare av filsystemet `di.xml` i en textredigerare.

   Om du klonade databasen finns den på `app/code/Magento/Elasticsearch/etc/di.xml`

   Om du har ett arkiv eller metapaketet finns det på `vendor/magento/module-elasticsearch/etc/di.xml`

1. Ändra värdet för `stopwordsDirectory` till den önskade katalogen:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
           <argument name="stopwordsDirectory" xsi:type="string">app/code/Magento/Elasticsearch/etc/stopwords</argument>
       </arguments>
   </type>
   ```

1. Spara ändringarna i `di.xml` och avsluta textredigeraren.

## Ändra katalogen från modulen

1. [Skapa en modul](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/module-file-structure.html)
1. I modulen `etc/di.xml` lägg till instruktioner:

   ```xml
   <type name="Magento\Elasticsearch\SearchAdapter\Query\Preprocessor\Stopwords">
       <arguments>
          <argument name="stopwordsModule" xsi:type="string">Your_Module</argument>
          <argument name="stopwordsDirectory" xsi:type="string">stopwords</argument>
       </arguments>
   </type>
   ```

1. Skapa katalogen i modulen `etc/stopwords`, med motsvarande CSV-fil.

1. Spara ändringarna i `di.xml` och avsluta textredigeraren.
