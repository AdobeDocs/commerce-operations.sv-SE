---
title: Versionsinformation om säkerhetsuppdateringar för Adobe Commerce 2.4.3
description: Läs mer om säkerhetsfelkorrigeringar, säkerhetsförbättringar och andra säkerhetsrelaterade uppdateringar som ingår i säkerhetsuppdateringarna för Adobe Commerce version 2.4.3.
exl-id: 72d343cd-83d7-48ce-976a-e26ba1b8db27
source-git-commit: 1eaf2329c16e6dbe3e93cb7fff3a6920b4b8379d
workflow-type: tm+mt
source-wordcount: '938'
ht-degree: 0%

---

# Adobe Commerce 2.4.3 Security Patch Release Notes

{{$include /help/_includes/security-patch-release-notes-intro.md}}

## Adobe Commerce 2.4.3-p3

Säkerhetsutgåvan av Adobe Commerce 2.4.3-p3 innehåller säkerhetsfixar för säkerhetsluckor som upptäcktes i den tidigare versionen (Adobe Commerce 2.4.3 och Magento Open Source 2.4.3). Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin APSB22-38](https://helpx.adobe.com/security/products/magento/apsb22-38.html).


### Använd `AC-3022.patch` fortsätta erbjuda DHL som fraktfirma

DHL har introducerat schemaversion 6.2 och kommer inom kort att föråldra schemaversion 6.0. Adobe Commerce 2.4.4 och tidigare versioner som stöder DHL-integration stöder endast version 6.0. Handlare som distribuerar dessa versioner bör tillämpa `AC-3022.patch` så snart det går att fortsätta erbjuda DHL som fraktfirma. Se [Använd en patch för att fortsätta erbjuda DHL som fraktfirma](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Kunskapsbasartikeln innehåller information om hur du hämtar och installerar korrigeringen.

### Viktiga säkerhetsfunktioner

* ACL-resurser har lagts till i inventeringen.
* Säkerheten för lagermallar har förbättrats.

## Adobe Commerce 2.4.3-p2

Säkerhetsutgåvan av Adobe Commerce 2.4.3-p2 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner. Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin APSB22-13](https://helpx.adobe.com/security/products/magento/apsb22-13.html).  Patchen åtgärdar också sårbarheten som åtgärdas av `MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch.zip`, `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch.zip`,`MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch`och `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch`.


### Använd `AC-3022.patch` fortsätta erbjuda DHL som fraktfirma

DHL har introducerat schemaversion 6.2 och kommer inom kort att föråldra schemaversion 6.0. Adobe Commerce 2.4.4 och tidigare versioner som stöder DHL-integration stöder endast version 6.0. Handlare som distribuerar dessa versioner bör tillämpa `AC-3022.patch` så snart det går att fortsätta erbjuda DHL som fraktfirma. Se [Använd en patch för att fortsätta erbjuda DHL som fraktfirma](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Kunskapsbasartikeln innehåller information om hur du hämtar och installerar korrigeringen.


### Viktiga säkerhetsfunktioner

* Användning av variabla e-postmeddelanden har ersatts i 2.3.4 som en del av en säkerhetsriskreducering till förmån för en mer strikt variabelsyntax. Detta beteende har i den här versionen helt tagits bort som en fortsättning på den riskreduceringen.

  Det innebär att e-post- och nyhetsbrevmallar som fungerade i tidigare versioner kanske inte fungerar som de ska när du uppgraderar till Adobe Commerce 2.4.3-p2. De mallar som påverkas är bland annat adminåsidosättningar, teman, underordnade teman och mallar från anpassade moduler eller tillägg från tredje part. Distributionen kan fortfarande påverkas även efter att du har använt [Kompatibilitetsverktyg för uppgradering](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html?lang=en) för att korrigera inaktuella användningar. Se [Migrera anpassade e-postmallar](https://developer.adobe.com/commerce/frontend-core/guide/templates/email-migration/) om du vill ha information om potentiella effekter och riktlinjer för migrering av berörda mallar.

* OAuth-åtkomsttokens och token för lösenordsåterställning krypteras nu när de lagras i databasen. <!-- AC-520 1323-->

* Valideringen har stärkts för att förhindra överföring av icke-alfanumeriska filtillägg. <!-- AC-479-->

* Swagger är nu inaktiverat som standard när Adobe Commerce är i produktionsläge. <!-- AC-1450-->

* Utvecklare kan nu konfigurera storleksgränsen för matriser som accepteras av Adobe Commerce RESTful-slutpunkter per slutpunkt. Se [API-säkerhet](https://developer.adobe.com/commerce/webapi/get-started/api-security/). <!-- AC-465-->

* Mekanismer har lagts till för att begränsa storleken och antalet resurser som en användare kan begära via ett webb-API på systemnivå och för att åsidosätta standardvärdena för enskilda moduler. Den här förbättringen åtgärdar problemet som åtgärdas i `MC-43048__set_rate_limits__2.4.3.patch`. Se [API-säkerhet](https://developer.adobe.com/commerce/webapi/get-started/api-security/). <!-- AC-1120-->


## 2.4.3-p1

Säkerhetsutgåvan av Adobe Commerce 2.4.3-p1 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i den tidigare utgåvan (Adobe Commerce 2.4.3 och Magento Open Source 2.4.3). Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.


Den senaste informationen om säkerhetsfelkorrigeringarna finns på [Adobe säkerhetsbulletin APSB21-86](https://helpx.adobe.com/security/products/magento/apsb21-86.html). Korrigeringsversionen innehåller även felkorrigeringar för [Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/braintree.html), [Klarna](https://marketplace.magento.com/klarna-m2-klarna.html)och [Hörn](https://marketplace.magento.com/vertexinc-vertex-tax-module.html) leverantörsutvecklade tillägg.


### Använd `AC-3022.patch` fortsätta erbjuda DHL som fraktfirma

DHL har introducerat schemaversion 6.2 och kommer inom kort att föråldra schemaversion 6.0. Adobe Commerce 2.4.4 och tidigare versioner som stöder DHL-integration stöder endast version 6.0. Handlare som distribuerar dessa versioner bör tillämpa `AC-3022.patch` så snart det går att fortsätta erbjuda DHL som fraktfirma. Se [Använd en patch för att fortsätta erbjuda DHL som fraktfirma](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier) Kunskapsbasartikeln innehåller information om hur du hämtar och installerar korrigeringen.

### Programfixar

Den här versionen innehåller följande snabbkorrigering och alla snabbkorrigeringar som har släppts för den föregående korrigeringsversionen.

* Lappa `AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch to address PHP fatal error on upgrade`. Se [Adobe Commerce upgrade 2.4.3, 2.3.7-p1 PHP Fatal error Hotfix](https://support.magento.com/hc/en-us/articles/4408021533069-Adobe-Commerce-upgrade-2-4-3-2-3-7-p1-PHP-Fatal-error-Hotfix) Kunskapsbasartikeln innehåller information om både korrigering och problem.

### Viktiga säkerhetsfunktioner

**Sessions-ID har tagits bort från databasen**. Den här kodändringen kan leda till att ändringar bryts om handlarna har anpassningar eller installerade tillägg som använder de rå sessions-ID:n som lagras i databasen. <!-- MC-40976-->

**Åtkomst till mediegalleriets mappar begränsas av administratörer**. Standardbehörigheter i Mediegalleriet tillåter nu endast katalogåtgärder (visa, ladda upp, ta bort och skapa) som tillåts uttryckligen av konfigurationen. Administratörsanvändare har inte längre åtkomst till medieresurser via mediegalleriet som har överförts utanför `catalog/category` eller `wysiwyg` kataloger. Administratörer som vill komma åt medieresurser måste flytta dem till en uttryckligen tillåten mapp eller justera sina konfigurationsinställningar. Se [Ändra behörigheter för Media Library-mappar](https://developer.adobe.com/commerce/php/tutorials/backend/modify-image-library-permissions/). <!-- B2B-1897-->

**Lägre gränser för komplexiteten i GraphQL-frågor**. GraphQL största tillåtna komplexitet för frågor har sänkts för att förhindra DOS-attacker. Se [GraphQL säkerhetskonfiguration](https://devdocs.magento.com/guides/v2.4/graphql/security-configuration.html). <!-- PWA-1700-->

**Säkerhetsluckor vid senaste penetrationstest** har korrigerats i den här versionen. <!-- MC-42431-->

Källuttrycket stöds inte `unsafe-inline` har tagits bort från skyddsprofilen för innehåll `frame-ancestors` -direktivet. [GitHub-33101](https://github.com/magento/magento2/issues/33101)<!-- MC-42632-->

