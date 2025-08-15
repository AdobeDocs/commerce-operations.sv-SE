---
title: Versionsinformation om säkerhetsuppdateringar för Adobe Commerce 2.4.3
description: Läs mer om säkerhetsfelkorrigeringar, säkerhetsförbättringar och andra säkerhetsrelaterade uppdateringar som ingår i säkerhetsuppdateringarna för Adobe Commerce version 2.4.3.
exl-id: 72d343cd-83d7-48ce-976a-e26ba1b8db27
source-git-commit: b63fa9a8b2b59f6e8dfd7003e75c66caf99d5e81
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 0%

---


# Versionsinformation om säkerhetsuppdateringar för Adobe Commerce 2.4.3

{{$include /help/_includes/release-notes/security-patch-intro.md}}

## Adobe Commerce 2.4.3-p3

Säkerhetsutgåvan av Adobe Commerce 2.4.3-p3 innehåller säkerhetsfixar för säkerhetsluckor som har identifierats i tidigare versioner av 2.4.3. Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB22-38](https://helpx.adobe.com/security/products/magento/apsb22-38.html).

### Använd `AC-3022.patch` om du vill fortsätta erbjuda DHL som fraktfirma

DHL har introducerat schemaversion 6.2 och kommer inom kort att föråldra schemaversion 6.0. Adobe Commerce 2.4.4 och tidigare versioner som stöder DHL-integration stöder endast version 6.0. Merchants som distribuerar dessa releaser ska tillämpa `AC-3022.patch` så snart som möjligt för att fortsätta erbjuda DHL som fraktfirma. Information om hur du hämtar och installerar korrigeringsfilen finns i [Använd en korrigeringsfil för att fortsätta erbjuda DHL som fraktfirma](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier).

### Viktiga säkerhetsfunktioner

* ACL-resurser har lagts till i inventeringen.
* Säkerheten för lagermallar har förbättrats.

## Adobe Commerce 2.4.3-p2

Säkerhetsutgåvan av Adobe Commerce 2.4.3-p2 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i tidigare versioner. Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.

Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB22-13](https://helpx.adobe.com/security/products/magento/apsb22-13.html).  Korrigeringsversionen åtgärdar också den säkerhetslucka som åtgärdats av `MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch.zip`, `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch.zip`, `MDVA-43395_EE_2.4.3-p1_COMPOSER_v1.patch` och `MDVA-43443_EE_2.4.3-p1_COMPOSER_v1.patch`.


### Använd `AC-3022.patch` om du vill fortsätta erbjuda DHL som fraktfirma

DHL har introducerat schemaversion 6.2 och kommer inom kort att föråldra schemaversion 6.0. Adobe Commerce 2.4.4 och tidigare versioner som stöder DHL-integration stöder endast version 6.0. Merchants som distribuerar dessa releaser ska tillämpa `AC-3022.patch` så snart som möjligt för att fortsätta erbjuda DHL som fraktfirma. Information om hur du hämtar och installerar korrigeringsfilen finns i [Använd en korrigeringsfil för att fortsätta erbjuda DHL som fraktfirma](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier).

### Viktiga säkerhetsfunktioner

* Användning av variabla e-postmeddelanden har ersatts i 2.3.4 som en del av en säkerhetsriskreducering till förmån för en mer strikt variabelsyntax. Detta beteende har i den här versionen helt tagits bort som en fortsättning på den riskreduceringen.

  Det innebär att e-post- och nyhetsbrevmallar som fungerade i tidigare versioner kanske inte fungerar som de ska när du uppgraderar till Adobe Commerce 2.4.3-p2. De mallar som påverkas är bland annat adminåsidosättningar, teman, underordnade teman och mallar från anpassade moduler eller tillägg från tredje part. Distributionen kan fortfarande påverkas även om du har använt verktyget [Kompatibilitet för uppgradering](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/overview.html?lang=en) för att korrigera inaktuella användningar. Information om möjliga effekter och riktlinjer för migrering av aktuella mallar finns i [Migrera anpassade e-postmallar](https://developer.adobe.com/commerce/frontend-core/guide/templates/email-migration/).

* OAuth-åtkomsttokens och token för lösenordsåterställning krypteras nu när de lagras i databasen. <!-- AC-520 1323-->

* Valideringen har stärkts för att förhindra överföring av icke-alfanumeriska filtillägg. <!-- AC-479-->

* Swagger är nu inaktiverat som standard när Adobe Commerce är i produktionsläge. <!-- AC-1450-->

* Utvecklare kan nu konfigurera storleksgränsen för matriser som accepteras av Adobe Commerce RESTful-slutpunkter per slutpunkt. Se [API-säkerhet](https://developer.adobe.com/commerce/webapi/get-started/api-security/). <!-- AC-465-->

* Mekanismer har lagts till för att begränsa storleken och antalet resurser som en användare kan begära via ett webb-API på systemnivå och för att åsidosätta standardvärdena för enskilda moduler. Den här förbättringen åtgärdar problemet som åtgärdats av `MC-43048__set_rate_limits__2.4.3.patch`. Se [API-säkerhet](https://developer.adobe.com/commerce/webapi/get-started/api-security/). <!-- AC-1120-->


## 2.4.3-p1

Säkerhetsutgåvan av Adobe Commerce 2.4.3-p1 innehåller säkerhetsfelkorrigeringar för säkerhetsluckor som har identifierats i den tidigare utgåvan (Adobe Commerce 2.4.3 och Magento Open Source 2.4.3). Den här versionen innehåller även säkerhetsförbättringar som förbättrar efterlevnaden av de senaste säkerhetsstandarderna.


Den senaste informationen om säkerhetsfelkorrigeringarna finns i [Adobe säkerhetsbulletin APSB21-86](https://helpx.adobe.com/security/products/magento/apsb21-86.html). Korrigeringsversionen innehåller även felkorrigeringar för leverantörsutvecklade tillägg för [Braintree](https://experienceleague.adobe.com/docs/commerce-admin/stores-sales/payments/braintree.html), [Klarna](https://marketplace.magento.com/klarna-m2-klarna.html) och [Vertex](https://marketplace.magento.com/vertexinc-vertex-tax-module.html) .

### Använd `AC-3022.patch` om du vill fortsätta erbjuda DHL som fraktfirma

DHL har introducerat schemaversion 6.2 och kommer inom kort att föråldra schemaversion 6.0. Adobe Commerce 2.4.4 och tidigare versioner som stöder DHL-integration stöder endast version 6.0. Merchants som distribuerar dessa releaser ska tillämpa `AC-3022.patch` så snart som möjligt för att fortsätta erbjuda DHL som fraktfirma. Information om hur du hämtar och installerar korrigeringsfilen finns i [Använd en korrigeringsfil för att fortsätta erbjuda DHL som fraktfirma](https://support.magento.com/hc/en-us/articles/7707818131597-Apply-a-patch-to-continue-offering-DHL-as-shipping-carrier).

### Programfixar

Den här versionen innehåller följande snabbkorrigering och alla snabbkorrigeringar som har släppts för den föregående korrigeringsversionen.

* Lappa `AC-384__Fix_Incompatible_PHP_Method__2.3.7-p1_ce.patch to address PHP fatal error on upgrade`. Läs artikeln [Adobe Commerce upgrade 2.4.3, 2.3.7-p1 PHP Fatal error Hotfix](https://support.magento.com/hc/en-us/articles/4408021533069-Adobe-Commerce-upgrade-2-4-3-2-3-7-p1-PHP-Fatal-error-Hotfix) i kunskapsbasen om du vill ha information om både korrigering och problem.

### Viktiga säkerhetsfunktioner

**Sessions-ID:n har tagits bort från databasen**. Den här kodändringen kan leda till att ändringar bryts om handlarna har anpassningar eller installerade tillägg som använder de rå sessions-ID:n som lagras i databasen. <!-- MC-40976-->

**Begränsad administratörsåtkomst till mediegalleriets mappar**. Standardbehörigheter i Mediegalleriet tillåter nu endast katalogåtgärder (visa, ladda upp, ta bort och skapa) som tillåts uttryckligen av konfigurationen. Administratörsanvändare har inte längre åtkomst till medieresurser via mediegalleriet som har överförts utanför katalogerna `catalog/category` eller `wysiwyg`. Administratörer som vill komma åt medieresurser måste flytta dem till en uttryckligen tillåten mapp eller justera sina konfigurationsinställningar. Se [Ändra behörigheter i mappen Mediebibliotek](https://developer.adobe.com/commerce/php/tutorials/backend/modify-image-library-permissions/). <!-- B2B-1897-->

**Lägre gränser för komplexitet för GraphQL-frågor**. GraphQL största tillåtna komplexitet för frågor har sänkts för att förhindra DOS-attacker. Se [GraphQL säkerhetskonfiguration](https://developer.adobe.com/commerce/webapi/graphql/usage/security-configuration/). <!-- PWA-1700-->

**Senaste penetrationstestsårbarheter** har åtgärdats i den här versionen. <!-- MC-42431-->

Källuttrycket `unsafe-inline` som inte stöds har tagits bort från direktivet Content Security Policy `frame-ancestors`. [GitHub-33101](https://github.com/magento/magento2/issues/33101)<!-- MC-42632-->
