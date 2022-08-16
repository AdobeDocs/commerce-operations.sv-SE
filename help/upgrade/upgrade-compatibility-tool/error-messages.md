---
title: '"[!DNL Upgrade Compatibility Tool] Felmeddelanden"'
description: Läs mer om felmeddelanden du får när du använder [!DNL Upgrade Compatibility Tool] i ditt Adobe Commerce-projekt.
source-git-commit: 038cb256cb19c253ae9c0375258a555601428847
workflow-type: tm+mt
source-wordcount: '4140'
ht-degree: 4%

---


# [!DNL Upgrade Compatibility Tool] felmeddelanden

{{commerce-only}}

Den här felmeddelandereferensen innehåller information om fel som kan uppstå när [!DNL Upgrade Compatibility Tool].

Felmeddelanden kategoriseras efter nivå (kritiska problem, fel och varningar) och typ (huvudkod, anpassad kod och GraphQL-scheman). Varje typ innehåller följande information:

- **Felkod**: Adobe Commerce-identifierare för felmeddelandet.
- **Felbeskrivning**: En beskrivning som sammanfattar orsaken till felet.
- **Fel: Föreslagen åtgärd**: Om det är tillämpligt, ger vägledning för felsökning och lösning.

## Kritiska problem

### Kärnkod

Dessa fel rapporteras när vissa av kärnfilerna saknas eller inte matchar originalet.

| Felkod | Felbeskrivning | Föreslagen åtgärd |
| --- | --- | --- |
| 2001 | Kärnfilen hittades inte | Kör `composer install` från projektets rotkatalog. |
| 2002 | Kärnfilen har ändrats | Kör `composer install` från projektets rotkatalog. |
| 2003 | Composer-beroendet har inte installerats | Kompositörens beroende saknas, vilket kan leda till problem. Återställ beroende genom att köra `composer require package_name`. |
| 2005 | Kärnmappen hittades inte | Kör `composer install` från projektets rotkatalog. |

{style=&quot;table-layout:auto&quot;}

### Egen kod

Allvarliga fel uppstår när den anpassade koden refererar till entiteter som inte finns i Adobe Commerce-målversionen. Dessa fel rapporteras också när viktiga kodningsstandarder har brutits.

| Felkod | Felbeskrivning | Föreslagen åtgärd |
| --- | --- | --- |
| 1110 | Instansierar obefintlig Adobe Commerce-klass/gränssnitt | Uppdatera koden så att den använder en klass som är markerad som `@api`. Instansierar obefintliga Adobe Commerce-klasser/gränssnitt. |
| 1111 | Utöka från en obefintlig Adobe Commerce-klass | Den utökade klassen finns inte längre i kodbasen. Arv rekommenderas inte för att utöka Adobe Commerce-funktioner. Uppdatera koden så att den använder en klass som är markerad som `@api`. |
| 1112 | Importerar en Adobe Commerce-klass som inte finns | Uppdatera koden så att den använder en klass som är markerad som `@api`. |
| 1113 | Läser in en Adobe Commerce-klass som inte finns | Uppdatera koden så att den använder en klass som är markerad som `@api`. |
| 1114 | Använda en Adobe Commerce-klass som inte finns | Uppdatera koden så att den använder en klass som är markerad som `@api`. |
| 1214 | Använda en obefintlig Adobe Commerce-konstant | Överväg att införa och använda en privat konstant av det värde som krävs i den anpassade koden i stället. |
| 1215 | Åsidosätter en obefintlig Adobe Commerce-konstant | Överväg att införa och använda en privat konstant av det värde som krävs i den anpassade koden i stället. |
| 1216 | Tilldelning av obefintlig Adobe Commerce-konstant | Överväg att införa och använda en privat konstant av det värde som krävs i den anpassade koden i stället. |
| 1312 | Ett Adobe Commerce-gränssnitt som inte finns har importerats | Ta bort arvet eller ersätt det med gränssnittet som introducerades i anpassningens omfång. |
| 1314 | Använt icke-existerande Adobe Commerce-gränssnitt | Ta bort arvet eller ersätt det med gränssnittet som introducerades i anpassningens omfång. |
| 1317 | Ärvt obefintligt Adobe Commerce-gränssnitt | Ta bort arvet eller ersätt det med gränssnittet som introducerades i anpassningens omfång. |
| 1318 | Ett Adobe Commerce-gränssnitt som inte finns har implementerats | Ta bort arvet eller ersätt det med gränssnittet som introducerades i anpassningens omfång. |
| 1410 | Anropa en Adobe Commerce-metod som inte finns | Uppdatera koden så att den använder en klass som är markerad som `@api`. |
| 1514 | Använda en obefintlig Adobe Commerce-egenskap | Uppdatera koden så att den använder en klass som är markerad som `@api`. |
| 1515 | Åsidosätter en Adobe Commerce-egenskap som inte finns | Uppdatera koden så att den använder en klass som är markerad som `@api`. |
| 1516 | Tilldelning av en Adobe Commerce-egenskap som inte finns | Uppdatera koden så att den använder en klass som är markerad som `@api`. Uppdatera åtkomstnivån för egenskapen till private om den bara kan användas i en enda klass. |
| 5002 | Den inledande PHP-taggen måste vara det första innehållet i filen | Kontrollera att det inte finns något innehåll i filen före PHP-öppningstaggen. |
| 5003 | Funktionen har tagits bort | Använd en ersättning som föreslås i felmeddelandet. Om meddelandet inte föreslår någon ersättning behövs en noggrann granskning för att välja en alternativ funktion eller implementering. |
| 5005 | PHP-syntaxfel | Koden måste uppdateras för att uppfylla PHP-syntaxstandarderna. |
| 5072 | Möjlig överträdelse av designen Magento 2. Identifierade en typisk Magento 1.x-konstruktion | Uppdatera konstruktionen enligt Magento 2-standarden. |
| 5076 | Det går inte att använda i namnutrymmet eftersom det är reserverat sedan PHP 7 | Ersätt det reserverade ordet i namnutrymmet med ett icke-reserverat nyckelord. |
| 5077 | Det går inte att använda som klassnamn eftersom det är reserverat sedan PHP 7 | Ersätt det reserverade klassnamnet med ett icke-reserverat namn. |

{style=&quot;table-layout:auto&quot;}

### DB-schema

Allvarliga problem med databasscheman rapporteras om borttagna huvudtabeller eller kolumner refereras av anpassade begränsningar.

| Felkod | Felbeskrivning | Föreslagen åtgärd |
| --- | --- | --- |
| 7009 | Den anpassade begränsningen refererar till en huvudtabell som har tagits bort i målversionen | Ta bort begränsningen eller uppdatera attributen referenceTable och referenceColumn |
| 7010 | Den anpassade begränsningen refererar till en huvudkolumn som har tagits bort i målversionen | Ta bort begränsningen eller uppdatera attributet referenceColumn |

{style=&quot;table-layout:auto&quot;}

### GraphQL-schema

Allvarliga problem med GraphQL-schema uppstår om schemaobjekten inte finns i målversionen.

| Felkod | Felbeskrivning | Föreslagen åtgärd |
| --- | --- | --- |
| 3101 | Typen har tagits bort | Visa alla frågor som refererar till det här fältet. Kontrollera om de här frågorna används av anpassningsimplementeringen. Uppdatera klientkoden för att hantera det ändrade frågegränssnittet. |
| 3102 | Text borttagen från union | Om unionstypen används i GraphQL-begäran om att konstruera eller bearbeta svar kan det behöva uppdateras. |
| 3103 | Fältet har tagits bort | Kontrollera om det finns referenser till fältet i anpassningskodbasen. Justera implementeringen för att hantera den nya fälttypen korrekt. |
| 3105 | Implementerat gränssnitt har tagits bort | Kontrollera om den typ som implementerar det borttagna gränssnittet används i anpassningen. Implementeringen kan behöva uppdateras om den förlitar sig på det borttagna gränssnittet. |
| 3106 | Värde borttaget från enum | Om det borttagna uppräkningsvärdet används i GraphQL-begäran som konstruerar eller svarar på bearbetningen kan det behöva uppdateras. |
| 3107 | Argumentet har tagits bort | Kontrollera om fältet används i anpassningsdatabasen. Ta bort argumentet för det här fältet. |
| 3109 | Direktivet borttaget | Kontrollera om direktivet används i anpassningskodbasen. Justera implementeringen för att ta bort referensen till direktivet. |
| 3110 | Argumentet direktiv har tagits bort | Kontrollera om direktivet används i anpassningskodbasen. Ta bort argumentet för direktivet. |
| 3111 | Upprepningsbart direktiv borttaget | Kontrollera om direktivet används i anpassningskodbasen. Justera implementeringen för att hantera gränssnittsändringar. |
| 3112 | Direktiv-platsen har tagits bort | Kontrollera om direktivet används i anpassningskodbasen. Justera implementeringen för att hantera gränssnittsändringar. |
| 3201 | Typ ändrad | Visa alla frågor som refererar till det här fältet. Kontrollera om de här frågorna används av anpassningsimplementeringen. Uppdatera klientkoden för att hantera det ändrade frågegränssnittet. |
| 3203 | Fältet har ändrats | Kontrollera om det finns referenser till fältet i anpassningskodbasen. Justera implementeringen för att hantera den nya fälttypen korrekt. |
| 3207 | Argumentet har ändrats | Kontrollera om fältet används i anpassningsdatabasen. Uppdatera argumenttypen för det här fältet. |
| 3303 | Obligatoriskt indatafält har lagts till | Fältet ska läggas till i begäran om frågan med det här fältet används för anpassningen. |
| 3307 | Ett obligatoriskt argument har lagts till | Kontrollera om fältet används i anpassningsdatabasen. Det nya obligatoriska argumentet ska anges när fältet används. |
| 3310 | Argumentet för obligatoriskt direktiv har lagts till | Kontrollera om direktivet används i anpassningskodbasen. Lägg till argumentet för direktivet. |

{style=&quot;table-layout:auto&quot;}

## Fel

### Egen kod

Anpassade kodfel uppstår när anpassad kod använder Adobe Commerce-startpunkter som inte betraktas/markeras som `@api`. Beteendet för sådana ingångspunkter garanteras inte. Anpassningen bör vara beroende av `@api` startpunkter i stället. Den funktionalitet som baseras på Adobe Commerce-kod som inte är API bör testas efter uppgraderingen. Dessa fel rapporteras också när större kodningsstandarder har brutits.

| Felkod | Felbeskrivning | Föreslagen åtgärd |
| --- | --- | --- |
| 1104 | Använda en icke-API-klass som ärver API-gränssnittet | Klasser som inte har markerats som `@api` kan ändras. Överväg att uppdatera koden så att den är beroende av gränssnittet som markerats som `@api` i stället. I annat fall bör funktionaliteten som är beroende av den här implementeringen testas efter uppgraderingen. |
| 1121 | Utöka från API-klass som inte är Adobe Commerce | Den utökade klassen finns inte längre i kodbasen. Arv rekommenderas inte för att utöka Adobe Commerce-funktioner. Uppdatera koden så att den använder en klass som är markerad som `@api`. |
| 1122 | Importera API-klass som inte är Adobe Commerce | Den utökade klassen finns inte längre i kodbasen. Uppdatera koden så att den använder en klass som är markerad som `@api`. I annat fall bör funktionaliteten som är beroende av den här implementeringen testas efter uppgraderingen. |
| 1123 | Läser in API-klass som inte är Adobe Commerce | Den utökade klassen finns inte längre i kodbasen. Uppdatera koden så att den använder en klass som är markerad som `@api`. I annat fall bör funktionaliteten som är beroende av den här implementeringen testas efter uppgraderingen. |
| 1124 | Använda API-klass som inte är Adobe Commerce | Den utökade klassen finns inte längre i kodbasen. Uppdatera koden så att den använder en klass som är markerad som `@api`. I annat fall bör funktionaliteten som är beroende av den här implementeringen testas efter uppgraderingen. |
| 1224 | Använda icke-Adobe Commerce API-konstant | Konstanter som inte är markerade som `@api` kan ändras. Överväg att införa och använda en privat konstant av det värde som krävs i den anpassade koden i stället. |
| 1225 | Åsidosätta icke-Adobe Commerce API-konstant | Konstanter som inte är markerade som `@api` kan ändras. Överväg att införa och använda en privat konstant av det värde som krävs i den anpassade koden i stället. |
| 1226 | Tilldelning av icke-Adobe Commerce API-konstant | Konstanter som inte är markerade som `@api` kan ändras. Överväg att införa och använda en privat konstant av det värde som krävs i den anpassade koden i stället. |
| 1322 | Importerat icke-Adobe Commerce API-gränssnitt | Gränssnitt har inte markerats som `@api` kan ändras. Ta bort det här arvet eller ersätt det med arv från Adobe Commerce-gränssnittet som är markerat som `@api` eller ett gränssnitt som introducerats i omfattningen av anpassningskoden. |
| 1324 | Använt API-gränssnitt som inte är Adobe Commerce | Gränssnitt har inte markerats som `@api` kan ändras. Ta bort det här arvet eller ersätt det med arv från Adobe Commerce-gränssnittet som är markerat som `@api` eller ett gränssnitt som introducerats i omfattningen av anpassningskoden. |
| 1327 | Ärvt API-gränssnitt som inte är Adobe Commerce | Konstanter som inte är markerade som `@api` kan ändras. Överväg att införa och använda en privat konstant av det värde som krävs i den anpassade koden i stället. |
| 1328 | Implementerat API-gränssnitt som inte är Adobe Commerce | Gränssnitt har inte markerats som `@api` kan ändras. Ta bort det här arvet eller ersätt det med arv från Adobe Commerce-gränssnittet som är markerat som `@api` eller ett gränssnitt som introducerats i omfattningen av anpassningskoden. |
| 1420 | Instansierar icke-Adobe Commerce API-klass/gränssnitt | Klasser som inte har markerats som `@api` kan ändras. Överväg att uppdatera koden så att den är beroende av gränssnittet som markerats som `@api` i stället. I annat fall bör funktionaliteten som är beroende av den här implementeringen testas efter uppgraderingen. Det rekommenderade sättet att hämta en instans av klassen är också att använda DI. Använd en fabrik om en ny instans av klassen krävs. |
| 1428 | Möjligt beroende på implementeringsinformation. | Klasser som inte har markerats som `@api` kan ändras. Överväg att uppdatera koden så att den är beroende av gränssnittet som markerats som `@api` i stället. I annat fall bör funktionaliteten som är beroende av den här implementeringen testas efter uppgraderingen. |
| 1429 | Anropa API-metoder som inte är Adobe Commerce | Metoder som inte har markerats som `@api` eller som inte har deklarerats inom API-klassen/gränssnittet kan ändras. Även om metodens gränssnitt inte uppdateras i den nya versionen kan dess beteende eller utdata vara annorlunda. Överväg att förlita dig på en gränssnittsmetod. I annat fall bör funktionaliteten som är beroende av den här implementeringen testas efter uppgraderingen. |
| 1449 | Anrop till icke-gränssnittsmetod (som finns i implementeringen) | Metoder som inte har deklarerats i gränssnittet kan ändras. Överväg att förlita dig på en gränssnittsmetod. I annat fall bör funktionaliteten som är beroende av den här implementeringen testas efter uppgraderingen. |
| 1524 | Använda API-egenskap som inte är Adobe Commerce | Värden för de egenskaper som inte är markerade som `@api` kan ändras. Överväg att förlita dig på API-gränssnittsmetoden i stället. |
| 1525 | Åsidosätta icke-Adobe Commerce API-egenskap | Värden för de egenskaper som inte är markerade som `@api` kan ändras. Överväg att förlita dig på API-gränssnittsmetoden i stället. |
| 1526 | Tilldelning av icke-Adobe Commerce API-egenskap | Värden för de egenskaper som inte är markerade som `@api` kan ändras. Överväg att förlita dig på API-gränssnittsmetoden i stället. |
| 5004 | Funktionen utan argument har tagits bort | Skicka indata som ska valideras som funktionens första argument. |
| 5007 | Användningen av vissa funktioner bör inte användas | Undvik att använda dessa funktioner. |
| 5009 | Malldirektiv får inte anropa metoder. Endast åtkomst till skalära matriser tillåts | Ta bort metodanrop från mallen. |
| 5010 | Mall `@vars` kommentarsblocket innehåller ogiltig JSON | Åtgärda ogiltig JSON. |
| 5011 | Mall `@vars` kommentarsblocket innehåller en ogiltig etikett | Korrigera ogiltig etikett. |
| 5012 | Mall `@vars` kommentarsblocket saknar en variabel som används i mallen | Lägg till en saknad variabel i @vars kommentarblock. |
| 5013 | Undvik att använda självstängande tagg med icke-void html-element | Använd close-taggen i stället. |
| 5014 | The `"active"` attributet är föråldrat | Listan med aktiva moduler definieras i distributionskonfigurationen. |
| 5015 | The `<param>` noden är föråldrad | Använd `<argument name="..." xsi:type="...">` i stället. |
| 5016 | The `<instance>` noden är föråldrad | Använd `<argument name="..." xsi:type="object">` i stället. |
| 5017 | The `<array>` noden är föråldrad | Använd `<argument name="..." xsi:type="array">` i stället. |
| 5018 | The `<item key="...">` noden är föråldrad | Använd `<item name="..." xsi:type="...">` i stället. |
| 5019 | The `<value>` noden är föråldrad | Ange i stället det faktiska värdet som en textlitteral. |
| 5020 | Föråldrad nod: `<supported_blocks>` | Ersätts med `<supported_containers>`. |
| 5021 | Föråldrad nod: `<block_name>` | Ersätts med `<container_name>`. |
| 5022 | Fabriksnamn har identifierats | Widgettypen ska inte börja med /. |
| 5023 | En föråldrad ACL-struktur har identifierats | Kontrollera lib/internal/Magento/Framework/Acl/etc/acl.xsd. |
| 5024 | Föråldrad menystruktur upptäcktes på raden | Kontrollera app/code/Magento/Backend/etc/menu.xsd. |
| 5025 | En föråldrad systemkonfigurationsstruktur upptäcktes i filen | Kontrollera app/code/Magento/Config/etc/system_file.xsd. |
| 5026 | Använd inte `"text/javascript"` type-attribut | Använd bara publika medlemmar. |
| 5028 | Tillgång till skyddade och privata medlemmar i `Block` klassen är föråldrad i FTML-mallar | Använd bara publika medlemmar. |
| 5031 | Innehåller föråldrad metod | Använd `getConnection()` i stället. |
| 5042 | Felaktigt format för PHP-klassreferens | Kontrollera att klassen bara refereras med cameraCased-bokstäver, siffror och inget inledande snedstreck. |
| 5043 | Felaktigt format för modulreferens | Kontrollera att modulen bara har bokstäver, siffror, understreck och inget inledande snedstreck som referens. |
| 5044 | Klass `Zend_Db_Select` är begränsad | Föreslagen ersättning: `\Magento\Framework\DB\Select`. |
| 5045 | Klass `Zend_Db_Adapter_Pdo_Mysql` är begränsad | Föreslagen ersättning: `\Magento\Framework\DB\Adapter\Pdo\Mysql`. |
| 5046 | Klass `Magento\Framework\Serialize\Serializer\Serialize` är begränsad | Föreslagen ersättning: `Magento\Framework\Serialize\SerializerInterface`. |
| 5047 | Klass `ArrayObject` är begränsad | Föreslagen ersättning: anpassad klass, utökad från `ArrayObject` med överskriven serialisering/avserialisering-metod. |
| 5048 | Klass `Magento\Framework\View\Element\UiComponent\ArrayObjectFactory` är begränsad | Föreslagen ersättning: Fabrik som skapar en anpassad klass, utökad från `ArrayObject` med överskriven serialisering/avserialisering-metod. |
| 5050 | Blocket som refereras tas bort | Ta bort referens till block. |
| 5051 | `output="toHtml"` är föråldrad | Använd `output="1"`. |
| 5052 | Klassen `\Magento\Framework\View\Element\Text\ListText` ska inte längre användas i layouten | Ta bort klass `\Magento\Framework\View\Element\Text\ListText` från layout. |
| 5053 | Anrop av metod via layoutinstruktion `<action>` tillåts inte | Undvik att använda felaktig metod i `<action>`. |
| 5054 | `helper` attributet innehåller `/` | Ta bort `/` från hjälpattribut. |
| 5055 | `helper` attributet innehåller inte `::` | Lägg till `::` till hjälpattribut. |
| 5056 | Installationsskript är föråldrade | Använd deklarativ schemainställning i modulens etc/db_schema.xml. |
| 5057 | InstallSchema-skript är föråldrade | Använd deklarativ schemainställning i modulens etc/db_schema.xml. |
| 5058 | InstallData-skript är föråldrade | Använd datapatchar i modulens Setup/Patch/Data dir. |
| 5059 | Installationsskript är föråldrade | Skapa en klass för InstallData i modulens inställningsmapp. |
| 5060 | Uppgraderingsskript är föråldrade | Använd deklarativ schemainställning i modulens etc/db_schema.xml. |
| 5061 | UpgradeSchema-skript är föråldrade | Använd deklarativ schemainställning i modulens etc/db_schema.xml. |
| 5062 | UpgradeData-skript är föråldrade | Använd datapatchar i modulens Setup/Patch/Data dir. |
| 5063 | Uppgraderingsskript är föråldrade | Använd datapatchar i modulens Setup/Patch/Data dir. |
| 5064 | Återkommande skript är föråldrade | Skapa klassen Recurring i modulens inställningsmapp. |
| 5065 | data finns i en ogiltig katalog | Skapa en datakorrigering i modulens inställnings-/korrigerings-/datamapp för datauppgraderingar eller använd den deklarativa schemametoden i modulens etc/db_schema.xml-fil för schemaändringar. |
| 5066 | sql finns i en ogiltig katalog | Skapa en datakorrigering i modulens inställnings-/korrigerings-/datamapp för datauppgraderingar eller använd den deklarativa schemametoden i modulens etc/db_schema.xml-fil för schemaändringar. |
| 5067 | Noder som identifieras av XPath är föråldrade | Föråldrad XML som anges i felet bör uppdateras. Följ förslagen från felmeddelandet. |
| 5068 | Direktiv `{{htmlescape}}` är föråldrad | Använd `{{var}}` i stället. |
| 5069 | Direktiv `{{escapehtml}}` är föråldrad | Använd `{{var}}` i stället. |
| 5070 | Den tredje parametern behövs inte längre för `getChildHtml()` | Ta bort den tredje parametern från anropet till `getChildHtml()`. |
| 5071 | Den fjärde parametern behövs inte längre för `getChildHtml()` | Ta bort den fjärde parametern från anropet till `getChildHtml()`. |
| 5073 | Äldre tabellnamn med snedstreck måste vara fasta på direkta tabellnamn | Använd direkt tabellnamn i stället. |
| 5075 | Programmoduler bör inte använda klasser från testmoduler | Ta bort användning av klasser från testmoduler. |
| 5078 | Klassen måste begäras i konstruktorn, annars kan kompilatorn inte hitta och generera dessa klasser | Lägg till klass i konstruktorn. |
| 5079 | Användning av variabler för var-klassen rekommenderas inte | Undvik att använda var för att deklarera klassvariabel. |
| 5080 | Möjlig SQL-sats för råformat har identifierats | Använd databaser eller datapatchar i stället. |
| 5081 | Hjälpmedel i mallar bör inte användas | Använd ViewModel i stället. |
| 5082 | Användningen av $this i mallar är föråldrad | Använd $block i stället. |
| 5083 | Konstanter tillåts inte som det första argumentet i översättningsfunktionen | Använd stränglitteral i stället. |
| 5085 | Användningen av vissa funktioner bör inte användas | Använd i stället den alternativa funktionen som finns i meddelandet. |
| 5087 | PHP-kompatibilitetsproblem för olika versioner | Följ förslagen från meddelandet och kontrollera [migreringsguide](https://www.php.net/manual/en/migration81.php). |
| 5088 | Valfria parametrar hittades efter obligatoriska | Flytta obligatoriska parametrar efter valfria parametrar. |
| 5089 | Metodsynlighet `final private` hittad | Ändra metodsynlighet från `final private` endast `private`. |
| 5090 | Magisk metod `__set_state` är inte definierad som `static` | Magisk metod `__set_state` måste definieras som `static`. |
| 5091 | Klass med `__toString()` ärver inte från `Stringable` gränssnitt | Lägg till `Stringable` gränssnitt till klass med `__toString()` -metod. |
| 5092 | `is_resource()` metod som används för funktioner som nu returnerar Object | Ändra `is_resource()` till `instanceof` Objekt. |
| 6001 | `jQuery.andSelf()` borttagen | Använd `jQuery.addBack()`. |
| 6002 | jQuery `$.bind` och `$.unbind` är föråldrade | Använd `$.on` och `$.off` i stället. |
| 6003 | jQuery-metoden för att prenumerera på en händelse är föråldrad och bör inte användas | Använd `.on("event name", fn)` i stället för att prenumerera på den händelsen. |
| 6003 | jQuery-metoden för att utlösa en händelse är föråldrad och bör inte användas | Använd `.trigger("event name")` i stället för att utlösa den händelsen. |
| 6004 | jQuery `$.delegate` och `$.undelegate` är föråldrade | Använd `$.on` och `$.off` i stället. |
| 6005 | (`jQuery.load()` / `jQuery.unload()` / `jQuery.error()`) togs bort | Använd (`.on("load", fn)` / `.on("unload", fn)` / `.on("error", fn)`) istället. |
| 6006 | `jQuery.size()` borttagen | Använd `jQuery.length`. |
| 6007 | `jQuery.trim` är föråldrad | Använd `String.prototype.trim`. |
| 6008 | (`addButton`, `addContextToolbar`, `addMenuItem`, `addSidebar`, `file_browser_callback`, `insert_button_items`, inlite-tema, mobiltema, modernt tema) har tagits bort | Uppdatera koden så att den är kompatibel med tinymce5. |
| 6009 | `jQuery.isFunction()` är föråldrad | I de flesta fall kan den ersättas med [typeof x === &quot;function&quot;]. |
| 6009 | `jQuery.type()` är föråldrad | Ersätt med lämplig typkontroll som [typeof x === &quot;function&quot;]. |
| 6009 | `jQuery.isArray()` är föråldrad | Använd metoden Array.isArray i stället. |
| 6009 | `jQuery.parseJSON()` är föråldrad | Om du vill analysera JSON-strängar använder du den systemspecifika JSON.parse-metoden i stället. |
| 6010 | (`jQuery.expr[":"]`, `jQuery.expr.filters`) är föråldrat | Använd jQuery.expr.pseudos i stället. |

{style=&quot;table-layout:auto&quot;}

### DB-schema

Databasschemafel uppstår om databastabeller, kolumner, index eller begränsningar, som har lagts till eller tagits bort i Adobe Commerce-målversionen, kan orsaka konflikter med det anpassade databasschemat.

| Felkod | Felbeskrivning | Föreslagen åtgärd |
| --- | --- | --- |
| 7001 | Målkärnversionen innehåller en tabell med samma namn som en tabell som deklarerats av en anpassad modul | Använd den nya huvudtabellen (om den är lämplig) eller byt namn på den anpassade tabellen |
| 7002 | Kärntabellen som utökats av en anpassad modul togs bort i målversionen | Alla borttagna huvudtabellreferenser ska tas bort från kodbasen |
| 7003 | Målkärnversionen innehåller en kolumn med samma namn som en kolumn som deklarerats av en anpassad modul | Använd den nya kärnkolumnen (om det är lämpligt) eller byt namn på den anpassade kolumnen |
| 7004 | Kärnkolumnen som utökas av en anpassad modul togs bort i målversionen | Alla borttagna kärnkolumnreferenser ska tas bort från kodbasen |
| 7005 | Målkärnversionen introducerar ett index med samma referenceId som ett index som deklarerats av en anpassad modul | Ta bort (om det är duplicerat till det nya kärnindexet) eller byt namn på det anpassade indexet |
| 7006 | Det huvudindex som utökas av en anpassad modul togs bort i målversionen | Alla borttagna kärnindexreferenser ska tas bort från kodbasen |
| 7007 | Målkärnversionen introducerar en begränsning med samma namn som en begränsning som deklarerats av en anpassad modul | Ta bort (om det är en dubblett till den nya grundbegränsningen) eller byt namn på den anpassade begränsningen |
| 7008 | Kärnbegränsningen som utökas av en anpassad modul togs bort i målversionen | Använd den nya grundbegränsningen (om den är lämplig) eller byt namn på den anpassade begränsningen |

{style=&quot;table-layout:auto&quot;}

## Varningar

### Kärnkod

Dessa varningar rapporteras när det finns mindre inkonsekvenser i kärnkodbasen.

| Felkod | Felbeskrivning | Föreslagen åtgärd |
| --- | --- | --- |
| 2004 | Versionsmatchningsfel för Composer-beroenden | Problemet anger att Composer-beroendeversionen i detaljerat och faktiskt projekt är annorlunda. Uppdatera beroende genom att köra `composer update <package_name>`. |

{style=&quot;table-layout:auto&quot;}

### Egen kod

Anpassade kodvarningar visas när referenser till inaktuell kod identifieras. Sådana referenser bör ersättas med de tilläggspunkter som stöds. Var uppmärksam på `@see` anteckning av borttaget objekt för rekommendationer. Dessa fel rapporteras också när mindre kodningsstandarder har brutits.

| Felkod | Felbeskrivning | Föreslagen åtgärd |
| --- | --- | --- |
| 1131 | Utöka från Adobe Commerce ``@deprecated`` class | Den utökade klassen tas bort i kommande versioner. Arv rekommenderas inte för att utöka Adobe Commerce-funktioner. Uppdatera koden så att den använder en klass som är markerad som `@api`. |
| 1132 | Importera Adobe Commerce `@deprecated` class | Den utökade klassen tas bort i kommande versioner. Överväg att använda klassen Adobe Commerce som är markerad som `@api` i stället. |
| 1133 | Läser in Adobe Commerce `@deprecated` class | Den utökade klassen tas bort i kommande versioner. Överväg att använda klassen Adobe Commerce som är markerad som `@api` i stället. |
| 1134 | Använda Adobe Commerce `@deprecated` class | Den utökade klassen tas bort i kommande versioner. Överväg att använda klassen Adobe Commerce som är markerad som `@api` i stället. |
| 1234 | Använda Adobe Commerce `@deprecated` konstant | Den borttagna konstanten tas bort i kommande versioner. Överväg att använda en konstant som markerats som `@api` eller en privat konstant i implementeringen i stället. |
| 1235 | Åsidosätta Adobe Commerce `@deprecated` konstant | Den borttagna konstanten tas bort i kommande versioner. Överväg att använda en konstant som markerats som `@api` eller en privat konstant i implementeringen i stället. |
| 1236 | Tilldelning av Adobe Commerce `@deprecated` konstant | Den borttagna konstanten tas bort i kommande versioner. Överväg att använda en konstant som markerats som `@api` eller en privat konstant i implementeringen i stället. |
| 1332 | Importerad Adobe Commerce `@deprecated` gränssnitt | Det borttagna gränssnittet tas bort i kommande versioner. Överväg att använda ett gränssnitt eller en klass som markerats som `@api` i stället. |
| 1334 | Använt Adobe Commerce `@deprecated` gränssnitt | Det borttagna gränssnittet tas bort i kommande versioner. Överväg att använda ett gränssnitt eller en klass som markerats som `@api` i stället. |
| 1337 | Ärvs från Adobe Commerce `@deprecated` gränssnitt | Det borttagna gränssnittet tas bort i kommande versioner. Överväg att ta bort gränssnittsarvet med ett gränssnitt som är markerat som `@api` eller ett gränssnitt som introducerats i implementeringen istället. |
| 1338 | Implementerad Adobe Commerce `@deprecated` gränssnitt | Det borttagna gränssnittet tas bort i kommande versioner. Överväg att ta bort gränssnittsarvet med ett gränssnitt som är markerat som `@api` eller ett gränssnitt som introducerats i implementeringen istället. |
| 1430 | Anropet har inte deklarerats som dataobjektmetod | De magiska metoder som inte har deklarerats kan ändras. Överväg att förlita dig på gränssnittsmetoder i stället. |
| 1439 | Ring Adobe Commerce `@deprecated` method | Den borttagna metoden tas bort i kommande versioner. Överväg att förlita dig på metoder som deklarerats i API-gränssnitt i stället. |
| 1440 | Felmatchad metodsignatur | Ett anrop eller åsidosättning av huvudmetoden upptäcks med parametrar, argument eller returtyp som inte matchar metodsignaturen. |
| 1534 | Använda Adobe Commerce `@deprecated` property | Den borttagna metoden tas bort i kommande versioner. Överväg att förlita dig på metoder som deklarerats i API-gränssnitt i stället. |
| 1535 | Åsidosätta Adobe Commerce `@deprecated` property | Den borttagna egenskapen tas bort i kommande versioner. Du bör i stället förlita dig på metoder som deklarerats i API-gränssnitt eller använda en privat egenskap i implementeringen. |
| 1536 | Tilldelning av Adobe Commerce `@deprecated` property | Den borttagna metoden tas bort i kommande versioner. Överväg att förlita dig på metoder som deklarerats i API-gränssnitt i stället. |
| 5006 | Proxies och spärrar MÅSTE aldrig uttryckligen begäras i konstruktorer | Den ursprungliga klassen ska deklareras som en typ av konstruktorparametern. Klassen Interceptor/Proxy skickas av implementeringen av ramverkets beroendeinjicering. |
| 5074 | Användning av borttagen metod `getResource()` data för (spara/läsa in/ta bort) har identifierats. | Använd en databas i stället. |
| 5086 | Synligheten har inte deklarerats för en konstant | Deklarera synligheten för alla konstanter. |

{style=&quot;table-layout:auto&quot;}

### GraphQL-schema

Varningar för GraphQL-schema visas när ytterligare objekt läggs till i schemat i den nya versionen. Vi rekommenderar att du granskar implementeringen för att se om de bör användas för begäranden.

| Felkod | Felbeskrivning | Föreslagen åtgärd |
| --- | --- | --- |
| 3206 | Argumentstandardvärdet har ändrats | Om frågan används i anpassningen kan argumentvärdet behöva anges explicit. |
| 3302 | Typ tillagd i union | Typen lades till i unionen. Kontrollera implementeringen som bearbetar resultatet av frågan som returnerar den här unionstypen och se till att den kan hantera den tillagda typen. |
| 3304 | Ytterligare inmatningsfält har lagts till | Valfritt inmatningsfält har lagts till. Kontrollera implementeringen för att säkerställa. |
| 3305 | Implementerat gränssnitt har lagts till | Fältet kan acceptera/tillhandahålla mer information som kan beaktas vid implementeringen. |
| 3306 | Värde tillagt i enum | Ett värde lades till i en uppräkning. Om klienterna innehåller en switch-programsats i uppräkningens värde och inte innehåller något standardfall, kan den här ändringen orsaka oväntat beteende. |
| 3308 | Valfritt argument har lagts till | Om frågan använder ett nytt argument i anpassningen kan den behöva läggas till i begäran. |

{style=&quot;table-layout:auto&quot;}
