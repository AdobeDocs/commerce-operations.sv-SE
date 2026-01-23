---
title: Översättningsordlistor och språkpaket
description: Lär dig hur du genererar översättningsordlistor och bygger språkpaket för Adobe Commerce. Upptäck lokalisering och flerspråkig lagringskonfiguration.
exl-id: dd27ccdd-158d-40a6-a2e2-563857820ae9
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '1414'
ht-degree: 0%

---

# Lokalisering

{{file-system-owner}}

Med Commerce-översättningar kan ni anpassa och lokalisera er butik för flera regioner och marknader genom att generera:

- **Översättningsordlistor**, som är ett praktiskt sätt att anpassa eller översätta _vissa_ ord och fraser, till exempel för en anpassad modul eller ett anpassat tema.
- **Språkpaket** som gör att du kan översätta _några eller alla_ ord och fraser i Commerce-programmet.

Se [Översättningar - översikt](https://developer.adobe.com/commerce/frontend-core/guide/translations/).

## Generera en översättningsordlista

Du kan generera en [översättningsordlista](https://developer.adobe.com/commerce/frontend-core/guide/translations/#translation-dictionaries) om du vill anpassa befintliga strängar, översätta ord och fraser i en anpassad modul, lokalisera ett tema eller skapa språkpaket.

Om du vill börja översätta använder du ett kommando för att generera en CSV-ordlistefil med en insamlad lista över alla befintliga fraser och ord.

Så här genererar du ordlistan och börjar översättningen:

1. Extrahera översättningsbara ord och fraser från aktiverade komponenter med kommandot för översättningssamling. Innehållet extraheras till en CSV-fil.
1. Översätt befintliga ord och fraser. Du kan lägga till ytterligare anpassade termer efter behov.

   Det finns alternativ för att använda den översatta ordlistan:

1. Du kan paketera översättningsordlistorna i ett språkpaket och skicka paketet till Commerce Store-administratören.

1. I Admin konfigurerar lagringsadministratören [översättningarna](https://experienceleague.adobe.com/en/docs/commerce-admin/stores-sales/site-store/store-localize).

Kommandoalternativ:

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

I följande tabell förklaras parametrar och värden:

| Parameter | Värde | Obligatoriskt? |
|--- |--- |--- |
| `<path to directory to translate>` | Sökväg till en katalog som har översättningsbar kod, dvs. PHP-, PHTML- eller XML-filer som har fraser att översätta.<br><br>Verktyget börjar söka på den sökväg som du anger och söker i alla filer och underkataloger som det innehåller.<br><br>Använd inte den här parametern om du använder `-m --magento`. | Ja (ordlistor), nej (paket). |
| `-m --magento` | Krävs för att skapa ett språkpaket från den här översättningsordlistan. Om det används söker igenom katalogerna som innehåller bin/magento. Med det här alternativet läggs teman eller moduler till på varje rad i ordlistan.<br><br>Ett exempel följer:<br><br>&quot;Inga objekt hittades&quot;,&quot;Inga objekt hittades&quot;, modul, Magento_önskelista | Nej |
| `-o --output="<path>"` | Anger den absoluta filsystemsökvägen och filnamnet för den CSV-fil för översättningsordlista som ska skapas. Värdet som du anger är skiftlägeskänsligt. CSV-filens namn måste exakt matcha språknamnet, inklusive tecknens skiftläge.<br><br>Om du utelämnar den här parametern dirigeras utdata till stdout. | Nej |

>[!INFO]
>
>Om du vill skapa ett språkpaket från en översättningsordlista _måste_ använda alternativet `-m|--magento`.

### Riktlinjer för översättning

Använd följande riktlinjer när du översätter ord och fraser:

- Ändra bara innehållet i den andra kolumnen. Översätt fraserna från engelska (`US`) till önskat språk.
- När du skapar ordlistor för språkområden ska du använda Commerce standardsträngar.
- Var uppmärksam på platshållare vid översättning: `%1`, `%2`

Commerce använder platshållarna för att infoga kontextvärden. De används _inte_ för översättningar. Exempel:

```text
Product '%1' has been added to shopping cart.
```

Fyller med ett värde:

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

Den resulterande frasen måste innehålla minst en platshållare. Anta till exempel att det finns platshållare från `%1` till `%3` i den ursprungliga frasen. Översättningen kan ha så många av dessa platshållare i vilken ordning som helst, men det måste finnas minst en förekomst av `%1`, `%2` och `%3`. Översättningen får inte innehålla platshållarvärden som inte finns i det ursprungliga värdet (till exempel `%4`, `%5` och så vidare).

Ett exempel på översättning av en fras:

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## Skapa ett språkpaket

I motsats till en översättningsordlista kan du översätta några eller alla ord och fraser i Commerce-programmet med hjälp av ett språkpaket. Du kan översätta en viss komponent - som en modul eller ett tema - med hjälp av ett översättningslexikon. [Läs mer om språkpaket](https://developer.adobe.com/commerce/frontend-core/guide/translations/#language-packages).

I det här avsnittet beskrivs hur du skapar ett språkpaket som skriver CSV-filer till moduler och teman. Om du vill skapa ett språkpaket måste du utföra de uppgifter som beskrivs i följande avsnitt:

1. [Samla in och översätta ord och fraser](#generate-a-translation-dictionary). (Parametern `--magento` krävs.)
1. [Kör språkpaketkommandot](#run-the-language-package-command).
1. [Skapa kataloger och filer](#create-directories-and-files).
1. (Valfritt.) [Konfigurera flera paket för ett språk &#x200B;](#configure-multiple-packages-for-a-language).

### Kör språkpaketkommandot

Kommandoanvändning:

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

I följande tabell förklaras parametrarna och värdena för språkpaketkommandot:

| Parameter | Värde | Obligatoriskt? |
|--- |--- |--- |
| `<source>` | Absolut filsystemsökväg och filnamn för en CSV-fil som innehåller den kombinerade översättningsordlistan och metainformation som krävs för att brytas ned till ett språkpaket.<br><br>Använd [`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict) för att skapa CSV-filen och skapa sedan språkpaketet enligt beskrivningen i [Skapa kataloger och filer](#m2devgde-xlate-files). | Ja |
| `<locale>` | [ISO 639-1](https://www.iso.org/iso-639-language-codes.html) (språk) och [ISO 3166](https://www.iso.org/iso-3166-country-codes.html) (land)-identifierare för språk som används som filnamn för alla resulterande CSV-filer. Exempel: `de_DE`, `pt_PT`, `pt_BR`. | Ja |
| `-m --mode` | Om det finns en målfil anger om det befintliga språkpaketet ska ersättas eller om det ska sammanfogas med det nya språkpaketet. Sammanfogning åsidosätter befintliga fraser och lägger till nya.<br><br>Värden: sammanfoga eller ersätt (standard). | Nej |
| `-d --allow-duplicates` | Inkludera det här alternativet om du vill tillåta dubbletter i språkpaketet. Annars misslyckas kommandot med ett fel om samma fras påträffas i flera poster med olika översättningar. | Nej |

### Skapa kataloger och filer

Språkpaket finns i en katalog under `app/i18n/<VendorName>` i Commerce-filsystemet med följande innehåll:

- Nödvändiga licensfiler
- `composer.json`
- `registration.php` som [registrerar](https://developer.adobe.com/commerce/php/development/build/component-registration/) språkpaketet
- [`language.xml`](#language-package-languagexml) metainformationsfil

>[!INFO]
>
>Du måste gemena hela banan. Se till exempel [`de_de`](https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php).

Så här skapar du dessa filer:

1. Skapa en katalog under `app/i18n`.

   Commerce språkpaket finns till exempel i `app/i18n/magento`

1. Lägg till nödvändiga licensfiler.
1. Lägg till [`composer.json`](https://developer.adobe.com/commerce/php/development/build/composer-integration/) som anger beroenden för ditt språkpaket.
1. Registrera språkpaketet med [`registration.php`](https://developer.adobe.com/commerce/php/development/build/component-registration/)
1. Lägg till `language.xml` metainformationsfil enligt beskrivningen i nästa avsnitt.

#### Språk.xml

När du deklarerar ett språkpaket i konfigurationsfilen `language.xml` måste du ange språkarvssekvensen för det här paketet.

Med språkarv kan du skapa en översättning som kallas _underordnad_ baserat på en befintlig översättning som kallas _överordnad_. De underordnade översättningarna åsidosätter den överordnade. Om den underordnade översättningen inte kan överföras eller visas, eller om en fras eller ett ord saknas, använder Commerce den överordnade språkinställningen. [Exempel på arv av språkpaket](#example-of-language-inheritance).

Om du vill deklarera ett paket anger du följande information:

```xml
<?xml version="1.0"?>
<language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
    <code>en_GB</code>
    <vendor>magento</vendor>
    <package>en_gb</package>
    <sort_order>100</sort_order>
    <use vendor="oxford-university" package="en_us"/>
</language>
```

Var:

- `code` - Språkpaketets nationella inställningar (krävs)
- `vendor` - Modulens leverantörsnamn (obligatoriskt)
- `package` - Namn på språkpaket (obligatoriskt)
- `sort_order` - Prioritet för att överföra ett paket när det finns flera språkpaket tillgängliga för en butik
- `use` - Språkpaket för överordnat språk som ordlistor ska ärvas från

Om det behövs kan du ange flera överordnade paket. De överordnade paketen tillämpas på den första listade, först använda basen.

#### Exempel på språkarv

Anta att ett språkpaket ärver från två andra paket och att dessa paket också har överordnade och &quot;indirekt överordnade&quot; paket.

Om ett språkpaket ärver från två paket kan dess `language.xml` se ut så här:

```xml
<language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
    <code>en_GB</code>
    <vendor>magento</vendor>
    <package>language_pack</package>
    <sort_order>100</sort_order>
    <use vendor="parent-package-one" package="language_package_one"/>
    <use vendor= "parent-package-two" package="language_package_two"/>
</language>
```

I föregående exempel:

- `language_package_one` ärver från `en_au_package` och `en_au_package` ärver från `en_ie_package`
- `language_package_two` ärver från `en_ca_package` och `en_ca_package` ärver från `en_us_package`

Om Commerce-programmet inte kan hitta ord eller fras i paketet `en_GB` söker det i andra paket i följande sekvens:

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

Om du anger alla arv mellan språkpaketen kan det leda till att cirkulära arvskedjor skapas. Använd [Magento\Test\Integrity\App\Language\CircularDependencyTest](https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php) för att hitta och åtgärda sådana kedjor.

### Konfigurera flera paket för ett språk

Du kan göra din butik mer flexibel genom att ladda upp flera språkpaket för samma språk i butiken. Du kan alltså använda olika anpassade paket för olika delar av din butik eftersom systemet kompilerar ett paket från alla paket som är tillgängliga för ett språk.

Om du vill aktivera ytterligare ett paket för ett befintligt språk namnger du det nya paketet vilket namn som helst, förutom ett befintligt språkkodsnamn (för att undvika missförstånd). Ange konfigurationer för ett paket i språkpaketets `language.xml`-metainformationsfil, vilket beskrivs i nästa avsnitt.

## Exempel på hur du använder översättningskommandon

I följande avsnitt ges kompletta exempel på hur du använder de kommandon som beskrivs i det här avsnittet för att skapa översättningsordlistor och översättningspaket:

### Exempel: Skapa en översättningsordlista för en modul eller ett tema

Så här lägger du till en tysk översättning till en modul eller ett tema som du vill distribuera till andra handlare:

1. Samla in fraser från modulen:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n/xx_YY.csv" /var/www/html/magento2/app/code/ExampleCorp/SampleModule
   ```

   >[!INFO]
   >
   >CSV-filnamnet måste _exakt matcha_ språkinställningen, inklusive tecknens skiftläge.

1. Översätt ord och fraser med [dessa riktlinjer](#translation-guidelines).
1. Om det behövs kopierar du `xx_YY.csv` till `/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n` eller till modulens temakatalog (beroende på om översättningsordlistan är för en modul eller ett tema).

### Exempel: Skapa ett språkpaket

Generera en CSV-fil på ungefär samma sätt som i föregående exempel, men i stället för att ange en modul eller temakatalog anger du hela Commerce programrotkatalog. Den resulterande CSV-filen innehåller fraser som kommandot kan hitta i koden.

1. Samla in fraser från modulen:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >CSV-filnamnet måste _exakt matcha_ språkinställningen, inklusive tecknens skiftläge.

1. Översätt ord och fraser med [dessa riktlinjer](#translation-guidelines).
1. Skapa språkpaketet.

   ```bash
   bin/magento i18n:pack /var/www/html/magento2/xx_YY.csv -d xx_YY
   ```

1. Skapa en katalog för språkpaketet.

   Exempel: `/var/www/html/magento2/app/i18n/ExampleCorp/xx_yy`

1. Lägg till följande i den katalogen:

   - En licens, om det behövs
   - `composer.json` (exemplet nedan)
   - `registration.php` (exemplet nedan)
   - `language.xml` (exemplet nedan)

   **Exempel`composer.json`**:

   ```json
   {
       "name": "examplecorp/language-xx_yy",
       "description": "Sample language",
       "version": "100.0.2",
       "license": [
           "OSL-3.0",
           "AFL-3.0"
       ],
       "require": {
           "magento/framework": "100.0.*"
       },
       "type": "magento2-language",
       "autoload": {
           "files": [
               "registration.php"
           ]
       }
   }
   ```

   **Exempel`registration.php`**:

   ```php
   <?php
   /**
    * Copyright [first year code created] Adobe
    * All Rights Reserved.
    */
   
   use Magento\Framework\Component\ComponentRegistrar;
   
   ComponentRegistrar::register(
       ComponentRegistrar::LANGUAGE,
       'magento_xx_yy',
       __DIR__
   );
   ```

   **Exempel`language.xml`**:

   ```xml
   <?xml version="1.0"?>
   <!--
   Copyright [first year code created] Adobe
   All Rights Reserved.
   -->
   <language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
       <code>xx_YY</code>
       <vendor>examplecorp</vendor>
       <package>xx_yy</package>
   </language>
   ```

