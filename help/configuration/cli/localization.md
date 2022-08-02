---
title: Översättningsordlistor och språkpaket
description: Lär dig hur du genererar översättningsordlistor och bygger språkpaket.
source-git-commit: bda758381d8d1b9209110adb168c36e1d504c4fa
workflow-type: tm+mt
source-wordcount: '1514'
ht-degree: 0%

---


# Lokalisering

{{file-system-owner}}

Med Commerce translations kan ni anpassa och lokalisera er butik för flera regioner och marknader genom att generera:

- **Översättningsordlistor**, som är ett bekvämt sätt att anpassa eller översätta _några_ ord och fraser, t.ex. för en anpassad modul eller ett tema.
- **Språkpaket** som gör att du kan översätta _alla_ ord och fraser i handelsprogrammet.

Se [Översikt över översättningar].

## Generera en översättningsordlista

Du kan generera en [översättningsordlista] om du vill anpassa befintliga strängar, översätta ord och fraser i en anpassad modul, lokalisera ett tema eller skapa [språkpaket](https://glossary.magento.com/language-package).

Om du vill börja översätta använder du ett kommando för att generera en CSV-ordlistefil med en insamlad lista över alla befintliga fraser och ord.

Så här genererar du ordlistan och börjar översättningen:

1. Extrahera översättningsbara ord och fraser från aktiverade komponenter med kommandot för översättningssamling. Innehållet extraheras till en CSV-fil.
1. Översätt befintliga ord och fraser. Du kan lägga till ytterligare anpassade termer efter behov.

   Det finns alternativ för att använda den översatta ordlistan:

1. Du kan paketera översättningsordlistorna i ett språkpaket och ge paketet till Commerce Store-administratören.

1. Butiksadministratören i Admin [konfigurerar översättningarna].

Kommandoalternativ:

```bash
bin/magento i18n:collect-phrases [-o|--output="<csv file path and name>"] [-m|--magento] <path to directory to translate>
```

I följande tabell förklaras parametrar och värden:

| Parameter | Värde | Obligatoriskt? |
|--- |--- |--- |
| `<path to directory to translate>` | Sökväg till en katalog med översättningsbar kod. PHP-, PHTML- eller XML-filer med fraser att översätta.<br><br>Verktyget börjar söka på den sökväg som du anger och söker i alla filer och underkataloger som det innehåller.<br><br>Använd inte den här parametern om du använder `-m --magento`. | Ja (ordlistor), nej (paket). |
| `-m --magento` | Krävs för att skapa ett språkpaket från den här översättningsordlistan. Om det används söker igenom katalogerna som innehåller bin/magento. Med det här alternativet läggs teman eller moduler till på varje rad i ordlistan.<br><br>Ett exempel följer:<br><br>&quot;Inga objekt hittades&quot;,&quot;Inga objekt hittades&quot;, modul, Magento_önskelista | Nej |
| `-o --output="<path>"` | Anger den absoluta filsystemsökvägen och filnamnet för den CSV-fil för översättningsordlista som ska skapas. Värdet som du anger är skiftlägeskänsligt. CSV-filens namn måste exakt matcha språknamnet, inklusive tecknens skiftläge.<br><br>Om du utelämnar den här parametern dirigeras utdata till stdout. | Nej |

>[!INFO]
>
>Om du vill skapa ett språkpaket från en översättningsordlista _måste_ använder `-m|--magento` alternativ.

### Riktlinjer för översättning

Använd följande riktlinjer när du översätter ord och fraser:

- Ändra bara innehållet i den andra kolumnen. Översätt fraserna från engelska (`US`) till önskat språk.
- När du skapar ordlistor för språkområden ska du använda de vanliga Commerce-strängarna.
- Var uppmärksam på platshållare när du översätter: `%1`, `%2`

I Commerce används platshållarna för att infoga kontextvärden. de _not_ används för översättningar. Exempel:

```text
Product '%1' has been added to shopping cart.
```

Fyller med ett värde:

```text
Product 'Multimeter-2000' has been added to shopping cart.
```

Den resulterande frasen måste innehålla minst en av varje platshållare. Anta till exempel att det finns platshållare från `%1` till `%3` i den ursprungliga frasen. Översättningen kan ha så många av dessa platshållare i vilken ordning som helst, men det måste finnas minst en förekomst av `%1`, `%2`och `%3`. Översättningen får inte innehålla platshållarvärden som inte finns i det ursprungliga värdet (till exempel `%4`, `%5`och så vidare).

Ett exempel på översättning av en fras:

```text
"Buy %1 for %2 (%3 incl. tax) each","Compre %1 por %2 (%3 incl. imposto) cada"
```

## Skapa ett språkpaket

I motsats till en översättningsordlista kan du översätta några eller alla ord och fraser i Commerce-programmet med hjälp av ett språkpaket. Du kan översätta en viss komponent - som en modul eller ett tema - med hjälp av ett översättningslexikon. [Läs mer om språkpaket].

I det här avsnittet beskrivs hur du skapar ett språkpaket som skriver CSV-filer till moduler och teman. Om du vill skapa ett språkpaket måste du utföra de uppgifter som beskrivs i följande avsnitt:

1. [Samla in och översätta ord och fraser](#generate-a-translation-dictionary). (Med `--magento` parameter krävs.)
1. [Kör språkpaketkommandot](#run-the-language-package-command).
1. [Skapa kataloger och filer](#create-directories-and-files).
1. (Valfritt.) [Konfigurera flera paket för ett språk](#configure-multiple-packages-for-a-language).

### Kör språkpaketkommandot

Kommandoanvändning:

```bash
bin/magento i18n:pack [-m|--mode={merge|replace}] [-d|--allow-duplicates] <source> <locale>
```

I följande tabell förklaras parametrarna och värdena för språkpaketkommandot:

| Parameter | Värde | Obligatoriskt? |
|--- |--- |--- |
| `<source>` | Absolut filsystemsökväg och filnamn för en CSV-fil som innehåller den kombinerade översättningsordlistan och metainformation som krävs för att brytas ned till ett språkpaket.<br><br>Använd [`bin/magento i18n:collect-phrases`](#config-cli-subcommands-xlate-dict-dict) för att skapa CSV-filen och sedan skapa språkpaketet enligt beskrivningen i [Skapa kataloger och filer](#m2devgde-xlate-files). | Ja |
| `<locale>` | [ISO 639-1] (språk) och [ISO 3166] identifierare för det språk som används som filnamn för alla CSV-filer som skapas. Exempel: `de_DE`, `pt_PT`, `pt_BR`. | Ja |
| `-m --mode` | Om det finns en målfil anger om det befintliga språkpaketet ska ersättas eller om det ska sammanfogas med det nya språkpaketet. Sammanfogning åsidosätter befintliga fraser och lägger till nya.<br><br>Värden: sammanfoga eller ersätta (standard). | Nej |
| `-d --allow-duplicates` | Inkludera det här alternativet om du vill tillåta dubbletter i språkpaketet. Annars misslyckas kommandot med ett fel om samma fras påträffas i flera poster med olika översättningar. | Nej |

### Skapa kataloger och filer

Språkpaketen finns i en katalog under `app/i18n/<VendorName>` i Commerce-filsystemet med följande innehåll:

- Nödvändiga licensfiler
- `composer.json`
- `registration.php` att [register] språkpaketet
- [`language.xml`](#language-package-languagexml) metainformationsfil

>[!INFO]
>
>Du måste gemena hela banan. Se till exempel [`de_de`].

Så här skapar du dessa filer:

1. Skapa en katalog under `app/i18n`.

   Exempelvis finns språkpaket för Commerce i `app/i18n/magento`

1. Lägg till nödvändiga licensfiler.
1. Lägg till [`composer.json`] som anger beroenden för ditt språkpaket.
1. Registrera språkpaketet med [`registration.php`]
1. Lägg till `language.xml` metainformationsfilen som beskrivs i nästa avsnitt.

#### Språk.xml

När ett språkpaket deklareras i `language.xml` konfigurationsfilen måste du ange språkarvssekvensen för det här paketet.

Med språkarv kan du skapa en översättning som kallas _child_ baserat på en befintlig översättning som kallas _parent_. De underordnade översättningarna åsidosätter den överordnade. Men om den underordnade översättningen inte kan överföras eller visas, eller om en fras eller ett ord saknas, används den överordnade [locale](https://glossary.magento.com/locale). [Exempel på arv av språkpaket](#example-of-language-inheritance).

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

- `code`—Språkpaket - nationella inställningar (krävs)
- `vendor`—Modulens leverantörsnamn (obligatoriskt)
- `package`—Språkpaketnamn (obligatoriskt)
- `sort_order`—Prioritet för att överföra ett paket när det finns flera språkpaket tillgängliga för en butik
- `use`—Språkinställning för överordnat språkpaket som ordlistor ska ärvas från

Om det behövs kan du ange flera överordnade paket. De överordnade paketen tillämpas på den första listade, först använda basen.

#### Exempel på språkarv

Anta att ett språkpaket ärver från två andra paket och att dessa paket också har överordnade och &quot;indirekt överordnade&quot; paket.

Om ett språkpaket ärver från två paket är dess `language.xml` kan se ut så här:

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

Om Commerce-programmet inte kan hitta ord eller fras i `en_GB` paketet, det söker i andra paket i följande sekvens:

1. `parent-package-one/language_package_one`
1. `<vendorname>/en_au_package`
1. `<vendorname>/en_ie_package`
1. `parent-package-two/language_package_two`
1. `<vendorname>/en_ca_package`
1. `<vendorname>/en_us_package`

Om du anger alla arv mellan språkpaketen kan det leda till att cirkulära arvskedjor skapas. Använd [Magento\Test\Integrity\App\Language\CircularDependencyTest] testa för att hitta och åtgärda sådana kedjor.

### Konfigurera flera paket för ett språk

Du kan göra din butik mer flexibel genom att ladda upp flera språkpaket för samma språk i butiken. Du kan alltså använda olika anpassade paket för olika delar av din butik eftersom systemet kompilerar ett paket från alla paket som är tillgängliga för ett språk.

Om du vill aktivera ytterligare ett paket för ett befintligt språk namnger du det nya paketet vilket namn som helst, förutom ett befintligt språkkodsnamn (för att undvika missförstånd). Ange konfigurationer för ett paket i språkpaketets `language.xml` metainformationsfilen som beskrivs i nästa avsnitt.

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
   >CSV-filnamnet måste _exakt matchning_ språkinställningen, inklusive tecknens skiftläge.

1. Översätt ord och fraser med [dessa riktlinjer](#translation-guidelines).
1. Kopiera vid behov `xx_YY.csv` till `/var/www/html/magento2/app/code/ExampleCorp/SampleModule/i18n` eller till modulens temakatalog (beroende på om översättningsordlistan är för en modul eller ett tema).

### Exempel: Skapa ett språkpaket

Generera en CSV-fil på ungefär samma sätt som i föregående exempel, men i stället för att ange en modul eller temakatalog anger du hela Commerce-programmets rotkatalog. Den resulterande CSV-filen innehåller fraser som kommandot kan hitta i koden.

1. Samla in fraser från modulen:

   ```bash
   bin/magento i18n:collect-phrases -o "/var/www/html/magento2/xx_YY.csv" -m
   ```

   >[!INFO]
   >
   >CSV-filnamnet måste _exakt matchning_ språkinställningen, inklusive tecknens skiftläge.

1. Översätt ord och fraser med [dessa riktlinjer](#translation-guidelines).
1. Skapa språkpaketet.

   ```bash
   bin/magento i18n:pack /var/www/html/magento2/xx_YY.csv -d xx_YY
   ```

1. Skapa en katalog för språkpaketet.

   Exempel: `/var/www/html/magento2/app/i18n/ExampleCorp/xx_yy`

1. Lägg till följande i den katalogen:

   - En licens, om det behövs
   - `composer.json` (exempel efter)
   - `registration.php` (exempel efter)
   - `language.xml` (exempel efter)

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
    * Copyright © Magento, Inc. All rights reserved.
    * See COPYING.txt for license details.
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
   /**
   * Copyright © Magento, Inc. All rights reserved.
   * See COPYING.txt for license details.
   */
   
   <language xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:App/Language/package.xsd">
       <code>xx_YY</code>
       <vendor>examplecorp</vendor>
       <package>xx_yy</package>
   </language>
   ```

<!-- link definitions -->

[Translate theme strings]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/translate_theory.html
[Översikt över översättningar]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html
[Community Engineering contributions]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html#translations-project
[översättningsordlista]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html#m2devgde-xlate-dictionaries
[konfigurerar översättningarna]: https://docs.magento.com/user-guide/stores/store-language-add.html?Highlight=translation
[Läs mer om språkpaket]: https://devdocs.magento.com/guides/v2.4/frontend-dev-guide/translations/xlate.html#m2devgde-xlate-languagepack
[ISO 639-1]: https://www.iso.org/iso-639-language-codes.html
[ISO 3166]: https://www.iso.org/iso-3166-country-codes.html
[register]: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/component-registration.html
[&quot;de_de&quot;]: https://github.com/magento/magento2/blob/2.4/app/i18n/Magento/de_DE/registration.php
[`Composer.json`]: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/composer-integration.html
[&quot;registration.php&quot;]: https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/component-registration.html
[Magento\Test\Integrity\App\Language\CircularDependencyTest]: https://github.com/magento/magento2/blob/2.4/dev/tests/static/testsuite/Magento/Test/Integrity/App/Language/CircularDependencyTest.php
