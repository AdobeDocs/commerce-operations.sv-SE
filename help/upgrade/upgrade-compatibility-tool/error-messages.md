---
title: '[!DNL Upgrade Compatibility Tool] felmeddelanden'
description: Läs mer om felmeddelanden du får när du använder  [!DNL Upgrade Compatibility Tool]  i ditt Adobe Commerce-projekt.
exl-id: fe4a17a9-a807-4315-b3cd-e35f34e39f6d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '4105'
ht-degree: 4%

---

# [!DNL Upgrade Compatibility Tool] felmeddelanden

{{commerce-only}}

Den här felmeddelandereferensen innehåller information om fel som kan inträffa när [!DNL Upgrade Compatibility Tool] körs.

Felmeddelanden kategoriseras efter nivå (kritiska problem, fel och varningar) och typ (huvudkod, anpassad kod och GraphQL-scheman). Varje typ innehåller följande information:

- **Felkod**: Den Adobe Commerce-tilldelade identifieraren för felmeddelandet.
- **Felbeskrivning**: En beskrivning som sammanfattar orsaken till felet.
- **Felföreslagen åtgärd**: Tillhandahåller vägledning för felsökning och lösning av felet om det är tillämpligt.

## Kritiska problem

### Kärnkod

Dessa fel rapporteras när vissa av kärnfilerna saknas eller inte matchar originalet.

| Felkod | Felbeskrivning | Föreslagen åtgärd |
| --- | --- | --- |
| 2001 | Kärnfilen hittades inte | Kör kommandot `composer install` från projektets rotkatalog. |
| 2002 | Kärnfilen har ändrats | Kör kommandot `composer install` från projektets rotkatalog. |
| 2003 | Composer-beroendet har inte installerats | Kompositörens beroende saknas, vilket kan leda till problem. Återställ beroendet genom att köra `composer require package_name`. |
| 2005 | Kärnmappen hittades inte | Kör kommandot `composer install` från projektets rotkatalog. |

{style="table-layout:auto"}

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
| 1216 | Tilldelning av en obefintlig Adobe Commerce-konstant | Överväg att införa och använda en privat konstant av det värde som krävs i den anpassade koden i stället. |
| 1312 | Ett Adobe Commerce-gränssnitt som inte finns har importerats | Överväg att ta bort arvet eller ersätta det med det gränssnitt som introducerades i anpassningens omfång. |
| 1314 | Använt icke-existerande Adobe Commerce-gränssnitt | Överväg att ta bort arvet eller ersätta det med det gränssnitt som introducerades i anpassningens omfång. |
| 1317 | Ärvt obefintligt Adobe Commerce-gränssnitt | Överväg att ta bort arvet eller ersätta det med det gränssnitt som introducerades i anpassningens omfång. |
| 1318 | Ett Adobe Commerce-gränssnitt som inte finns implementerat | Överväg att ta bort arvet eller ersätta det med det gränssnitt som introducerades i anpassningens omfång. |
| 1410 | Anropa en Adobe Commerce-metod som inte finns | Uppdatera koden så att den använder en klass som är markerad som `@api`. |
| 1514 | Använda en obefintlig Adobe Commerce-egenskap | Uppdatera koden så att den använder en klass som är markerad som `@api`. |
| 1515 | Åsidosätter en Adobe Commerce-egenskap som inte finns | Uppdatera koden så att den använder en klass som är markerad som `@api`. |
| 1516 | Tilldelning av en Adobe Commerce-egenskap som inte finns | Uppdatera koden så att den använder en klass som är markerad som `@api`. Uppdatera åtkomstnivån för egenskapen till private om den bara kan användas i en enda klass. |
| 5002 | Den inledande PHP-taggen måste vara det första innehållet i filen | Kontrollera att filen inte innehåller något innehåll före PHP-öppningstaggen. |
| 5003 | Funktionen har tagits bort | Använd en ersättning som föreslås i felmeddelandet. Om meddelandet inte föreslår någon ersättning behövs en noggrann granskning för att välja en alternativ funktion eller implementering. |
| 5005 | PHP-syntaxfel | Koden måste uppdateras för att uppfylla PHP-syntaxstandarderna. |
| 5072 | Möjlig överträdelse av designen Magento 2. Identifierade en typisk Magento 1.x-konstruktion | Uppdatera konstruktionen enligt Magento 2-standarden. |
| 5076 | Det går inte att använda i namnutrymmet eftersom det är reserverat sedan PHP 7 | Ersätt det reserverade ordet i namnutrymmet med ett icke-reserverat nyckelord. |
| 5077 | Det går inte att använda som klassnamn eftersom det är reserverat sedan PHP 7 | Ersätt det reserverade klassnamnet med ett icke-reserverat namn. |

{style="table-layout:auto"}

### DB-schema

Allvarliga problem med databasscheman rapporteras om borttagna huvudtabeller eller kolumner refereras av anpassade begränsningar.

| Felkod | Felbeskrivning | Föreslagen åtgärd |
| --- | --- | --- |
| 7009 | Den anpassade begränsningen refererar till en huvudtabell som har tagits bort i målversionen | Ta bort begränsningen eller uppdatera attributen referenceTable och referenceColumn |
| 7010 | Den anpassade begränsningen refererar till en huvudkolumn som har tagits bort i målversionen | Ta bort begränsningen eller uppdatera attributet referenceColumn |

{style="table-layout:auto"}

### GraphQL Schema

Allvarliga problem med GraphQL Schema uppstår om schemaobjekten inte finns i målversionen.

| Felkod | Felbeskrivning | Föreslagen åtgärd |
| --- | --- | --- |
| 3101 | Typen har tagits bort | Visa alla frågor som refererar till det här fältet. Kontrollera om de här frågorna används av anpassningsimplementeringen. Uppdatera klientkoden för att hantera det ändrade frågegränssnittet. |
| 3102 | Text borttagen från union | Om unionstypen används i GraphQL-begärankonstruktionen eller svarsimplementeringen kan den behöva uppdateras. |
| 3103 | Fältet har tagits bort | Kontrollera om det finns referenser till fältet i anpassningskodbasen. Justera implementeringen för att hantera den nya fälttypen korrekt. |
| 3105 | Implementerat gränssnitt har tagits bort | Kontrollera om den typ som implementerar det borttagna gränssnittet används i anpassningen. Implementeringen kan behöva uppdateras om den förlitar sig på det borttagna gränssnittet. |
| 3106 | Värde borttaget från enum | Om det borttagna uppräkningsvärdet används i implementeringen av GraphQL-begäran för konstruering eller svarsbearbetning kan det behöva uppdateras. |
| 3107 | Argumentet har tagits bort | Kontrollera om fältet används i anpassningsdatabasen. Ta bort argumentet för fältet. |
| 3109 | Direktivet borttaget | Kontrollera om direktivet används i anpassningskodbasen. Justera implementeringen för att ta bort referensen till direktivet. |
| 3110 | Argumentet direktiv har tagits bort | Kontrollera om direktivet används i anpassningskodbasen. Ta bort argumentet för direktivet. |
| 3111 | Upprepningsbart direktiv borttaget | Kontrollera om direktivet används i anpassningskodbasen. Justera implementeringen för att hantera gränssnittsändringarna. |
| 3112 | Direktiv-platsen har tagits bort | Kontrollera om direktivet används i anpassningskodbasen. Justera implementeringen för att hantera gränssnittsändringarna. |
| 3201 | Typ ändrad | Visa alla frågor som refererar till det här fältet. Kontrollera om de här frågorna används av anpassningsimplementeringen. Uppdatera klientkoden för att hantera det ändrade frågegränssnittet. |
| 3203 | Fältet har ändrats | Kontrollera om det finns referenser till fältet i anpassningskodbasen. Justera implementeringen för att hantera den nya fälttypen korrekt. |
| 3207 | Argumentet har ändrats | Kontrollera om fältet används i anpassningsdatabasen. Uppdatera argumenttypen för fältet. |
| 3303 | Obligatoriskt indatafält har lagts till | Fältet ska läggas till i begäran om frågan med det här fältet används för anpassningen. |
| 3307 | Ett obligatoriskt argument har lagts till | Kontrollera om fältet används i anpassningsdatabasen. Det nya obligatoriska argumentet ska anges när fältet används. |
| 3310 | Argumentet för obligatoriskt direktiv har lagts till | Kontrollera om direktivet används i anpassningskodbasen. Lägg till argumentet för direktivet. |

{style="table-layout:auto"}

## Fel

### Egen kod

Anpassade kodfel uppstår när anpassad kod använder Adobe Commerce-startpunkter som inte betraktas/markeras som `@api`. Beteendet för sådana ingångspunkter garanteras inte. Anpassningen bör förlita sig på `@api` startpunkter i stället. Den funktionalitet som baseras på Adobe Commerce-kod som inte är API bör testas efter uppgraderingen. Dessa fel rapporteras också när större kodningsstandarder har brutits.

| Felkod | Felbeskrivning | Föreslagen åtgärd |
| --- | --- | --- |
| 1104 | Använda en icke-API-klass som ärver API-gränssnittet | Klasser som inte har markerats som `@api` kan ändras. Överväg att uppdatera koden så att den förlitar sig på gränssnittet som markerats som `@api` i stället. I annat fall bör funktionaliteten som är beroende av den här implementeringen testas efter uppgraderingen. |
| 1121 | Utöka från API-klass som inte är Adobe Commerce | Den utökade klassen finns inte längre i kodbasen. Arv rekommenderas inte för att utöka Adobe Commerce-funktioner. Uppdatera koden så att den använder en klass som är markerad som `@api`. |
| 1122 | Importera API-klass som inte är Adobe Commerce | Den utökade klassen finns inte längre i kodbasen. Uppdatera koden så att den använder en klass som är markerad som `@api`. I annat fall bör funktionaliteten som är beroende av den här implementeringen testas efter uppgraderingen. |
| 1123 | Läser in API-klass som inte är Adobe Commerce | Den utökade klassen finns inte längre i kodbasen. Uppdatera koden så att den använder en klass som är markerad som `@api`. I annat fall bör funktionaliteten som är beroende av den här implementeringen testas efter uppgraderingen. |
| 1124 | Använda API-klass som inte är Adobe Commerce | Den utökade klassen finns inte längre i kodbasen. Uppdatera koden så att den använder en klass som är markerad som `@api`. I annat fall bör funktionaliteten som är beroende av den här implementeringen testas efter uppgraderingen. |
| 1224 | Använda icke-Adobe Commerce API-konstant | Konstanter som inte har markerats som `@api` kan ändras. Överväg att införa och använda en privat konstant av det värde som krävs i den anpassade koden i stället. |
| 1225 | Åsidosätta icke-Adobe Commerce API-konstant | Konstanter som inte har markerats som `@api` kan ändras. Överväg att införa och använda en privat konstant av det värde som krävs i den anpassade koden i stället. |
| 1226 | Tilldelning av icke-Adobe Commerce API-konstant | Konstanter som inte har markerats som `@api` kan ändras. Överväg att införa och använda en privat konstant av det värde som krävs i den anpassade koden i stället. |
| 1322 | Importerat icke-Adobe Commerce API-gränssnitt | Gränssnitt som inte har markerats som `@api` kan ändras. Överväg att ta bort det här arvet eller att ersätta det med arv från Adobe Commerce-gränssnittet som är markerat som `@api` eller ett gränssnitt som introducerats i omfattningen av anpassningskoden. |
| 1324 | Använt API-gränssnitt som inte är Adobe Commerce | Gränssnitt som inte har markerats som `@api` kan ändras. Överväg att ta bort det här arvet eller att ersätta det med arv från Adobe Commerce-gränssnittet som är markerat som `@api` eller ett gränssnitt som introducerats i omfattningen av anpassningskoden. |
| 1327 | Ärvt API-gränssnitt som inte är Adobe Commerce | Konstanter som inte har markerats som `@api` kan ändras. Överväg att införa och använda en privat konstant av det värde som krävs i den anpassade koden i stället. |
| 1328 | Implementerat API-gränssnitt som inte är Adobe Commerce | Gränssnitt som inte har markerats som `@api` kan ändras. Överväg att ta bort det här arvet eller att ersätta det med arv från Adobe Commerce-gränssnittet som är markerat som `@api` eller ett gränssnitt som introducerats i omfattningen av anpassningskoden. |
| 1420 | Instansierar icke-Adobe Commerce API-klass/gränssnitt | Klasser som inte har markerats som `@api` kan ändras. Överväg att uppdatera koden så att den förlitar sig på gränssnittet som markerats som `@api` i stället. I annat fall bör funktionaliteten som är beroende av den här implementeringen testas efter uppgraderingen. Det rekommenderade sättet att hämta en instans av klassen är också att använda DI. Använd en fabrik om en ny instans av klassen krävs. |
| 1428 | Möjligt beroende på implementeringsinformation. | Klasser som inte har markerats som `@api` kan ändras. Överväg att uppdatera koden så att den förlitar sig på gränssnittet som markerats som `@api` i stället. I annat fall bör funktionaliteten som är beroende av den här implementeringen testas efter uppgraderingen. |
| 1429 | Anropa API-metoder som inte är Adobe Commerce | Metoder som inte har markerats som `@api` eller som inte har deklarerats inom API-klassen/gränssnittet kan ändras. Även om metodens gränssnitt inte uppdateras i den nya versionen kan dess beteende eller utdata vara annorlunda. Överväg att förlita dig på en gränssnittsmetod. I annat fall bör funktionaliteten som är beroende av den här implementeringen testas efter uppgraderingen. |
| 1449 | Anrop till icke-gränssnittsmetod (som finns i implementeringen) | Metoder som inte har deklarerats i gränssnittet kan ändras. Överväg att förlita dig på en gränssnittsmetod. I annat fall bör funktionaliteten som är beroende av den här implementeringen testas efter uppgraderingen. |
| 1524 | Använda API-egenskap som inte är Adobe Commerce | Värden för egenskaper som inte har markerats som `@api` kan ändras. Överväg att förlita dig på API-gränssnittsmetoden i stället. |
| 1525 | Åsidosätta icke-Adobe Commerce API-egenskap | Värden för egenskaper som inte har markerats som `@api` kan ändras. Överväg att förlita dig på API-gränssnittsmetoden i stället. |
| 1526 | Tilldelning av icke-Adobe Commerce API-egenskap | Värden för egenskaper som inte har markerats som `@api` kan ändras. Överväg att förlita dig på API-gränssnittsmetoden i stället. |
| 5004 | Funktionen utan argument har tagits bort | Skicka indata som ska valideras som funktionens första argument. |
| 5007 | Användningen av vissa funktioner bör inte användas | Undvik dessa funktioner. |
| 5009 | Malldirektiv får inte anropa metoder. Endast åtkomst till skalära matriser tillåts | Ta bort metodanrop från mallen. |
| 5010 | Mallens `@vars`-kommentarblock innehåller ogiltig JSON | Åtgärda ogiltig JSON. |
| 5011 | Mallens kommentarblock `@vars` innehåller en ogiltig etikett | Korrigera ogiltig etikett. |
| 5012 | Mallen `@vars` kommentarsblock saknar en variabel som används i mallen | Lägg till en saknad variabel i @vars kommentarblock. |
| 5013 | Undvik att använda självstängande tagg med icke-void html-element | Använd close-taggen i stället. |
| 5014 | Attributet `"active"` är föråldrat | Listan med aktiva moduler definieras i distributionskonfigurationen. |
| 5015 | Noden `<param>` är inaktuell | Använd `<argument name="..." xsi:type="...">` i stället. |
| 5016 | Noden `<instance>` är inaktuell | Använd `<argument name="..." xsi:type="object">` i stället. |
| 5017 | Noden `<array>` är inaktuell | Använd `<argument name="..." xsi:type="array">` i stället. |
| 5018 | Noden `<item key="...">` är inaktuell | Använd `<item name="..." xsi:type="...">` i stället. |
| 5019 | Noden `<value>` är inaktuell | Ange i stället det faktiska värdet som en textlitteral. |
| 5020 | Föråldrad nod: `<supported_blocks>` | Ska ersättas med `<supported_containers>`. |
| 5021 | Föråldrad nod: `<block_name>` | Ska ersättas med `<container_name>`. |
| 5022 | Fabriksnamn har identifierats | Widgettypen ska inte börja med /. |
| 5023 | En föråldrad ACL-struktur har identifierats | Kontrollera lib/internal/Magento/Framework/Acl/etc/acl.xsd. |
| 5024 | Föråldrad menystruktur upptäcktes på raden | Kontrollera app/code/Magento/Backend/etc/menu.xsd. |
| 5025 | En föråldrad systemkonfigurationsstruktur upptäcktes i filen | Kontrollera app/code/Magento/Config/etc/system_file.xsd. |
| 5026 | Använd inte typattributet `"text/javascript"` | Använd bara publika medlemmar. |
| 5028 | Åtkomst till skyddade och privata medlemmar i klassen `Block` är föråldrad i FTML-mallar | Använd bara publika medlemmar. |
| 5031 | Innehåller föråldrad metod | Använd metoden `getConnection()` i stället. |
| 5042 | Felaktigt format för PHP-klassreferens | Kontrollera att klassen bara refereras med cameraCased-bokstäver, siffror och inget inledande snedstreck. |
| 5043 | Felaktigt format för modulreferens | Kontrollera att modulen bara har bokstäver, siffror, understreck och inget inledande snedstreck som referens. |
| 5044 | Klassen `Zend_Db_Select` är begränsad | Föreslagen ersättning: `\Magento\Framework\DB\Select`. |
| 5045 | Klassen `Zend_Db_Adapter_Pdo_Mysql` är begränsad | Föreslagen ersättning: `\Magento\Framework\DB\Adapter\Pdo\Mysql`. |
| 5046 | Klassen `Magento\Framework\Serialize\Serializer\Serialize` är begränsad | Föreslagen ersättning: `Magento\Framework\Serialize\SerializerInterface`. |
| 5047 | Klassen `ArrayObject` är begränsad | Föreslagen ersättning: Anpassad klass, utökad från `ArrayObject` med överskrivna serialiserings-/avserialiseringsmetoder. |
| 5048 | Klassen `Magento\Framework\View\Element\UiComponent\ArrayObjectFactory` är begränsad | Föreslagen ersättning: Factory som skapar en anpassad klass, utökad från `ArrayObject` med överskrivna serialiserings-/avserialiseringsmetoder. |
| 5050 | Blocket som refereras tas bort | Ta bort referens till block. |
| 5051 | `output="toHtml"` är föråldrad | Använd `output="1"`. |
| 5052 | Klassen `\Magento\Framework\View\Element\Text\ListText` ska inte längre användas i layout | Ta bort klass `\Magento\Framework\View\Element\Text\ListText` från layout. |
| 5053 | Det är inte tillåtet att anropa metoden via layoutinstruktionen `<action>` | Undvik att använda en felaktig metod i `<action>`. |
| 5054 | Attributet `helper` innehåller `/` | Ta bort `/` från hjälpattributet. |
| 5055 | Attributet `helper` innehåller inte `::` | Lägg till `::` i hjälpattributet. |
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
| 5068 | Direktiv `{{htmlescape}}` är föråldrat | Använd `{{var}}` i stället. |
| 5069 | Direktiv `{{escapehtml}}` är föråldrat | Använd `{{var}}` i stället. |
| 5070 | Den tredje parametern behövs inte längre för `getChildHtml()` | Ta bort den tredje parametern från anropet till `getChildHtml()`. |
| 5071 | Den fjärde parametern behövs inte längre för `getChildHtml()` | Ta bort den fjärde parametern från anropet till `getChildHtml()`. |
| 5073 | Äldre tabellnamn med snedstreck måste vara fasta på direkta tabellnamn | Använd direkt tabellnamn i stället. |
| 5075 | Programmoduler bör inte använda klasser från testmoduler | Ta bort användning av klasser från testmoduler. |
| 5078 | Klassen måste begäras i konstruktorn, annars kan kompilatorn inte hitta och generera dessa klasser | Lägg till klass i konstruktorn. |
| 5079 | Användning av variabler för var-klassen rekommenderas inte | Undvik att använda var för att deklarera klassvariabel. |
| 5080 | Möjlig SQL-sats för råformat har identifierats | Använd databaser eller datapatchar i stället. |
| 5081 | Hjälpmedel i mallar bör inte användas | Använd ViewModel i stället. |
| 5082 | Användningen av $this i mallar är inaktuell | Använd $block i stället. |
| 5083 | Konstanter tillåts inte som det första argumentet i översättningsfunktionen | Använd stränglitteral i stället. |
| 5085 | Användningen av vissa funktioner bör inte användas | Använd i stället den alternativa funktionen som finns i meddelandet. |
| 5087 | PHP-kompatibilitetsproblem mellan versioner | Följ förslagen från meddelandet och kontrollera [migreringsguiden](https://www.php.net/manual/en/migration81.php). |
| 5088 | Valfria parametrar hittades efter obligatoriska | Flytta obligatoriska parametrar efter valfria parametrar. |
| 5089 | Metodsynlighet `final private` hittades | Ändra metodsynlighet från `final private` till endast `private`. |
| 5090 | Magisk metod `__set_state` är inte definierad som `static` | Den magiska metoden `__set_state` måste definieras som `static`. |
| 5091 | Klassen med metoden `__toString()` ärver inte från gränssnittet `Stringable` | Lägg till gränssnittet `Stringable` i klassen med metoden `__toString()`. |
| 5092 | Metoden `is_resource()` används för funktioner som nu returnerar Object | Ändra `is_resource()` till `instanceof`-objekt. |
| 6001 | `jQuery.andSelf()` har tagits bort | Använd `jQuery.addBack()`. |
| 6002 | jQuery `$.bind` och `$.unbind` är föråldrade | Använd `$.on` och `$.off` i stället. |
| 6003 | jQuery-metoden för att prenumerera på en händelse är föråldrad och bör inte användas | Använd metoden `.on("event name", fn)` i stället för att prenumerera på den händelsen. |
| 6003 | jQuery-metoden för att utlösa en händelse är föråldrad och bör inte användas | Använd metoden `.trigger("event name")` i stället för att utlösa händelsen. |
| 6004 | jQuery `$.delegate` och `$.undelegate` är föråldrade | Använd `$.on` och `$.off` i stället. |
| 6005 | (`jQuery.load()` / `jQuery.unload()` / `jQuery.error()`) togs bort | Använd (`.on("load", fn)` / `.on("unload", fn)` / `.on("error", fn)`) i stället. |
| 6006 | `jQuery.size()` har tagits bort | Använd `jQuery.length`. |
| 6007 | `jQuery.trim` är inaktuell | Använd `String.prototype.trim`. |
| 6008 | (`addButton`, `addContextToolbar`, `addMenuItem`, `addSidebar`, `file_browser_callback`, `insert_button_items`, inlite-tema, mobiltema, modernt tema) har tagits bort | Uppdatera koden så att den är kompatibel med tinymce5. |
| 6009 | `jQuery.isFunction()` är inaktuell | I de flesta fall kan den ersättas med [typeof x ===&quot;function&quot;]. |
| 6009 | `jQuery.type()` är inaktuell | Ersätt med en lämplig typkontroll som [typeof x ===&quot;function&quot;]. |
| 6009 | `jQuery.isArray()` är inaktuell | Använd metoden Array.isArray i stället. |
| 6009 | `jQuery.parseJSON()` är inaktuell | Om du vill analysera JSON-strängar använder du den systemspecifika JSON.parse-metoden i stället. |
| 6010 | (`jQuery.expr[":"]`, `jQuery.expr.filters`) är föråldrad | Använd jQuery.expr.pseudos i stället. |

{style="table-layout:auto"}

### DB-schema

Databasschemafel uppstår om databastabeller, kolumner, index eller begränsningar, som har lagts till eller tagits bort i Adobe Commerce-målversionen, kan orsaka konflikter med det anpassade databasschemat.

| Felkod | Felbeskrivning | Föreslagen åtgärd |
| --- | --- | --- |
| 7001 | Målkärnversionen innehåller en tabell med samma namn som en tabell som deklarerats av en anpassad modul | Använd den nya huvudtabellen (om den är lämplig) eller byt namn på den anpassade tabellen |
| 7002 | Kärntabellen som utökats av en anpassad modul togs bort i målversionen | Alla borttagna huvudtabellreferenser ska tas bort från kodbasen |
| 7003 | Målkärnversionen innehåller en kolumn med samma namn som en kolumn som deklarerats av en anpassad modul | Använd den nya kärnkolumnen (om det är lämpligt) eller byt namn på den anpassade kolumnen |
| 7004 | Kärnkolumnen som utökas av en anpassad modul togs bort i målversionen | Alla borttagna kärnkolumnreferenser ska tas bort från kodbasen |
| 7005 | Målkärnversionen innehåller ett index med samma referenceId som ett index som deklarerats av en anpassad modul | Ta bort (om det är en dubblett till det nya kärnindexet) eller byt namn på det anpassade indexet |
| 7006 | Det huvudindex som utökas av en anpassad modul togs bort i målversionen | Alla borttagna kärnindexreferenser ska tas bort från kodbasen |
| 7007 | Målkärnversionen innehåller en begränsning med samma namn som en begränsning som deklarerats av en anpassad modul | Ta bort (om det är en dubblett till den nya grundbegränsningen) eller byt namn på den anpassade begränsningen |
| 7008 | Kärnbegränsningen som utökas av en anpassad modul togs bort i målversionen | Använd den nya grundbegränsningen (om den är lämplig) eller byt namn på den anpassade begränsningen |

{style="table-layout:auto"}

## Varningar

### Kärnkod

Dessa varningar rapporteras när det finns mindre inkonsekvenser i kärnkodbasen.

| Felkod | Felbeskrivning | Föreslagen åtgärd |
| --- | --- | --- |
| 2004 | Versionsmatchningsfel för Composer-beroenden | Problemet anger att Composer-beroendeversionen i detaljerat och faktiskt projekt är annorlunda. Uppdatera beroende genom att köra `composer update <package_name>`. |

{style="table-layout:auto"}

### Egen kod

Anpassade kodvarningar visas när referenser till inaktuell kod identifieras. Sådana referenser bör ersättas med de tilläggspunkter som stöds. Var uppmärksam på `@see`-anteckningen för det borttagna objektet för rekommendationer. Dessa fel rapporteras också när mindre kodningsstandarder har brutits.

| Felkod | Felbeskrivning | Föreslagen åtgärd |
| --- | --- | --- |
| 1131 | Utöka från Adobe Commerce ``@deprecated``-klass | Den utökade klassen tas bort i kommande versioner. Arv rekommenderas inte för att utöka Adobe Commerce-funktioner. Uppdatera koden så att den använder en klass som är markerad som `@api`. |
| 1132 | Importerar Adobe Commerce-klassen `@deprecated` | Den utökade klassen tas bort i kommande versioner. Överväg att använda Adobe Commerce-klass som markerats som `@api` i stället. |
| 1133 | Läser in Adobe Commerce `@deprecated`-klass | Den utökade klassen tas bort i kommande versioner. Överväg att använda Adobe Commerce-klass som markerats som `@api` i stället. |
| 1134 | Använda Adobe Commerce `@deprecated`-klassen | Den utökade klassen tas bort i kommande versioner. Överväg att använda Adobe Commerce-klass som markerats som `@api` i stället. |
| 1234 | Använda Adobe Commerce `@deprecated`-konstanten | Den borttagna konstanten tas bort i kommande versioner. Använd en konstant som är markerad som `@api` eller en privat konstant i implementeringen i stället. |
| 1235 | Åsidosätter Adobe Commerce `@deprecated`-konstanten | Den borttagna konstanten tas bort i kommande versioner. Använd en konstant som är markerad som `@api` eller en privat konstant i implementeringen i stället. |
| 1236 | Tilldelning av Adobe Commerce `@deprecated`-konstanten | Den borttagna konstanten tas bort i kommande versioner. Använd en konstant som är markerad som `@api` eller en privat konstant i implementeringen i stället. |
| 1332 | Adobe Commerce `@deprecated`-gränssnittet har importerats | Det borttagna gränssnittet tas bort i kommande versioner. Använd ett gränssnitt eller en klass som är markerad som `@api` i stället. |
| 1334 | Använt Adobe Commerce `@deprecated`-gränssnitt | Det borttagna gränssnittet tas bort i kommande versioner. Använd ett gränssnitt eller en klass som är markerad som `@api` i stället. |
| 1337 | Ärvs från Adobe Commerce `@deprecated`-gränssnittet | Det borttagna gränssnittet tas bort i kommande versioner. Överväg att ta bort gränssnittsarvet genom att använda ett gränssnitt som markerats som `@api` eller ett gränssnitt som introducerats i implementeringen i stället. |
| 1338 | Adobe Commerce `@deprecated`-gränssnittet har implementerats | Det borttagna gränssnittet tas bort i kommande versioner. Överväg att ta bort gränssnittsarvet genom att använda ett gränssnitt som markerats som `@api` eller ett gränssnitt som introducerats i implementeringen i stället. |
| 1430 | Anropet har inte deklarerats som dataobjektmetod | De magiska metoder som inte har deklarerats kan ändras. Överväg att förlita dig på gränssnittsmetoder i stället. |
| 1439 | Anropa Adobe Commerce `@deprecated`-metoden | Den borttagna metoden kommer att tas bort i kommande versioner. Överväg att förlita dig på metoder som deklarerats i API-gränssnitt i stället. |
| 1440 | Felmatchad metodsignatur | Ett anrop eller åsidosättning av huvudmetoden upptäcks med parametrar, argument eller returtyp som inte matchar metodsignaturen. |
| 1534 | Använda Adobe Commerce-egenskapen `@deprecated` | Den borttagna metoden kommer att tas bort i kommande versioner. Överväg att förlita dig på metoder som deklarerats i API-gränssnitt i stället. |
| 1535 | Åsidosätter Adobe Commerce `@deprecated`-egenskap | Den borttagna egenskapen tas bort i kommande versioner. Du bör i stället förlita dig på metoder som deklarerats i API-gränssnitt eller använda en privat egenskap i implementeringen. |
| 1536 | Tilldelning av Adobe Commerce `@deprecated`-egenskap | Den borttagna metoden kommer att tas bort i kommande versioner. Överväg att förlita dig på metoder som deklarerats i API-gränssnitt i stället. |
| 5006 | Proxies och spärrar MÅSTE aldrig uttryckligen begäras i konstruktorer | Den ursprungliga klassen ska deklareras som en typ av konstruktorparametern. Klassen Interceptor/Proxy skickas av implementeringen av ramverkets beroendeinjicering. |
| 5074 | Användning av den inaktuella metoden `getResource()` för att (spara/läsa in/ta bort) data har identifierats. | Använd en databas i stället. |
| 5086 | Synligheten har inte deklarerats för en konstant | Ange synligheten för alla konstanter. |

{style="table-layout:auto"}

### GraphQL Schema

GraphQL Schema-varningar visas när de ytterligare objekten läggs till i schemat i den nya versionen. Vi rekommenderar att du granskar implementeringen för att se om de bör användas för begäranden.

| Felkod | Felbeskrivning | Föreslagen åtgärd |
| --- | --- | --- |
| 3206 | Argumentets standardvärde har ändrats | Om frågan används i anpassningen kan argumentvärdet behöva anges explicit. |
| 3302 | Typ tillagd i union | Typen lades till i unionen. Kontrollera implementeringen som bearbetar resultatet av frågan som returnerar den här unionstypen och se till att den kan hantera den tillagda typen. |
| 3304 | Ytterligare inmatningsfält har lagts till | Valfritt inmatningsfält har lagts till. Kontrollera implementeringen för att säkerställa. |
| 3305 | Implementerat gränssnitt har lagts till | Fältet kan acceptera/tillhandahålla mer information som kan beaktas vid implementeringen. |
| 3306 | Värde tillagt i enum | Ett värde lades till i en uppräkning. Om klienterna innehåller en switch-programsats i uppräkningens värde och inte innehåller något standardfall, kan den här ändringen orsaka oväntat beteende. |
| 3308 | Valfritt argument har lagts till | Om frågan använder ett nytt argument i anpassningen kan den behöva läggas till i begäran. |

{style="table-layout:auto"}
