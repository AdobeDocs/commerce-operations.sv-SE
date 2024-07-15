---
title: Bästa praxis för kodgranskning
description: Läs mer om hur man lär sig mer om kodgranskning i utvecklingsfasen av Adobe Commerce-projekt.
feature: Best Practices
role: Developer
exl-id: 1ef78bce-2e69-4c95-a26e-1bf7196ce546
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '1161'
ht-degree: 0%

---

# Code review best practices for Adobe Commerce

Det främsta målet för kodgranskning är att validera att den implementerade funktionen uppfyller kraven på ett optimalt sätt från prestanda-, arkitektur- och säkerhetsperspektiv.

Dessutom är kodgranskningen avsedd att säkerställa att koden uppfyller Adobe Commerce bästa praxis för utveckling, är enkel att förstå och underhålla och följer kodningsstandarder. De flesta kodningsstandarder bör kontrolleras automatiskt med lämpliga verktyg.

## Rekommenderad kodgranskning

På en hög nivå bör kodgranskningsprocessen bestå av följande steg:

1. En funktionsgren för utcheckning i den lokala utvecklingsmiljön.
1. Om det var ett tag sedan koden skickades för granskning sammanfogar du de senaste ändringarna från målgrenen (vanligtvis QA-grenen) och skickar uppdateringar till fjärrfunktionsgrenen (om det finns några).
1. Gör en granskning på hög nivå för att validera att koden uppfyller alla krav. Om det finns större skillnader bör du kontakta utvecklaren för klargöranden.
1. Det är valfritt att köra koden, men om du är tveksam till om koden fungerar som förväntat eller om den underlättar processens effektivitet bör du testa att den implementerade funktionen fungerar som förväntat för de huvudsakliga användningsscenarierna. Om det är några större problem avbryter du granskningsprocessen och öppnar biljetten igen med lämpliga kommentarer.
1. Genomför en grundlig granskning för att validera att koden uppfyller alla krav. Om det uppstår några problem lägger du till lämpliga kommentarer i pull-begäran och öppnar biljetten på nytt.
1. Om allt ser bra ut sammanfogar du pull-begäran (eller skickar den till nästa granskningsnivå för kod om en sådan har upprättats).

Tänk också på följande när du implementerar kodgranskningsprocesser:

- Kodgranskning är ett primärt verktyg för kommunikation och kunskapsöverföring inom ett team. Även om en pull-begäran inte innehåller några större problem och implementerar den nödvändiga affärslogiken, kan du använda den som en möjlighet att föreslå fler förbättringar efter att den har sammanfogats.

- I genomsnitt bör kodgranskning inte ta mer än 10 % till 20 % av utvecklingsinsatserna. Det förutsätter att utvecklingsteamet består av erfarna ingenjörer som arbetar väl tillsammans. Om kodgranskningen tar längre tid kan det påverka projektbudgeten och tidslinjen.

- Åtgärda problem med stora ansträngningar som krävs för kodgranskning genom att identifiera grundorsaken. Vanligtvis beror det på att kraven är dåligt översatta i utvecklingsbiljetter (på grund av kommunikationsproblem, dåliga användarberättelser) eller på att det är ett problem med kodning. I det första fallet rekommenderas att man ser till att biljetterna har tillräckligt med information för att teammedlemmarna ska kunna uppfylla kraven på ett effektivt sätt. I det andra fallet kan du behöva justera teamstrukturen så att fler erfarna ingenjörer inkluderas, eller få godkännande utanför mentorskap och kodning.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Vad du ska leta efter i kodgranskningen

### Stil

Stilen kan testas automatiskt genom att köra PhpStorm-undersökningen (se nedan).

Konfigurera [PHPMD och PHPCS](https://developer.adobe.com/commerce/php/best-practices/phpstorm/code-inspection/) och kör verktyget [Code Standard](https://github.com/magento/magento-coding-standard) från CLI (även nedan). Det finns en viss överlappning, men båda har också unika tester.

### Konvention och struktur

Granskningar av konvention och struktur utförs manuellt.

- Är klassfunktionaliteten begränsad till ett enda ansvar?
- Låter katalogstrukturen bra?
- Är funktionaliteten utförd på rätt nivå (server, klient, CSS, JS, databas, ramverk, infrastruktur).
- Är versionshanteringen korrekt?
- Ser koden okonventionell ut eller som om den försöker komma runt ett problem på fel sätt?
- Används namnkonventionen för modulnamnet, paketnamnet och databasnamnet korrekt?
- Kontrollera att globala CSS-format används noggrant och inte används för mycket.

### Fullständighet

Granskningar för att se om de är fullständiga görs manuellt.

- Kan koden aktiveras eller inaktiveras av konfigurationen och fungerar all nödvändig kod som förväntat?
- Finns alla konfigurationer som nämns i biljetten? Kontrollera omfattning, datatyp, validering, översättning och standardvärden.
- Hämtas konfigurationen alltid på lägsta möjliga nivå (visningsnivå, webbplatsnivå eller global nivå)? Konfigurationshämtningen måste matcha definitionen av omfång i filen `system.xml`.
- Omfattas alla banor i flödesschemat i den tekniska specifikationen? Omfattas alla andra tekniska specifikationer?
- Definieras åtkomstkontrollistor för den nya funktionen?
- Är PhpDocs tydlig? Är bekräftelsemeddelanden tydliga?
- Kommenterar någon kod ut eller ser du felsökningskoden?

### Prestanda

Prestandagranskningar görs manuellt, vilket kan vägledas av exekvering av kod när du är osäker.

- Körs frågor i en slinga? Den här slingan kan ligga utanför de redigerade filerna.
- Kan du hitta några `cachable="false"`-attribut? Används de korrekt?

### Säkerhet

Säkerhetsgranskningar görs manuellt och kan vägledas av textsökning. En del av säkerhetskontrollen hanteras genom automatiska tester.

- Loggas undantag vid behov? Används rätt typer av undantag?
- Kan `around` plugin-program undvikas?
- Returnerar plugin-program rätt typer av data?
- Kan du hitta några SQL-råfrågor som ska byggas med databasens abstraktionslager?
- Är någon ny typ av data exponerad för någon typ av användare, administratör eller frontend? Är den exponeringen en säkerhetsrisk?
- Valideras användargenererade data? Allt som kommer från webbläsaren betraktas som användargenererat, inklusive cookie-värden och serverrubriker.

### Integritet och GDPR

Sekretessgranskningar och [GDPR](../../../security-and-compliance/privacy/gdpr.md) utförs manuellt.

- Hanterar koden kunddata eller e-postmeddelanden? Var särskilt uppmärksam.
- Om den här koden kan köras i en slinga, kan den då läcka kunddata från en slingcykel till en annan?
- Riskindikatorer är import, cron-jobb, transaktionsmejl och batchköhanterare.
- Se till att användardata isoleras i slingor. Adobe rekommenderar att du använder fabriker eller databaser för att skapa modeller i slingcykeln som inte är tillgängliga utanför slingan.

### Mentorsverktyg

Granska för mentorarbete görs manuellt.

- Leta efter platser där du kan dela kunskap med målet att utbilda teamet.
- Om din kommentar är av rent utbildningsskäl, men inte avgörande för att uppfylla standarderna, ska du ange att det inte är obligatoriskt för författaren att lösa den.
- Om du ser något bra ut kan du berätta det för utvecklaren, särskilt när de har svarat på en av dina kommentarer på ett bra sätt. Kodgranskningar fokuserar ofta på misstag, men de bör även uppmuntra och uppskatta god praxis. Ibland är det ännu värdefullare när det gäller mentorskap att berätta för en utvecklare vad de gjorde rätt i än att berätta vad de gjorde fel.

## Automatisering

Utvecklarna kan använda automatisering för att granska ID-kompilering, databasschema, Composer-validering och kompatibilitet med kodningsstandarderna:

- DI-kompilering - Kör följande CLI-kommandon för att se om koden kan kompileras utan problem.

  ```bash
  bin/magento module:disable -n -q --all || exit;
  bin/magento module:enable -n -q --all || exit;
  bin/magento cache:enable -n -q || exit;
  bin/magento cache:flush -n -q || exit;
  rm -rf generated/*
  rm -rf var/view_preprocessed/*
  rm -rf pub/static/*
  rm -rf var/cache/*
  bin/magento deploy:mode:set --skip-compilation production || exit;
  bin/magento setup:di:compile -vv || exit;
  bin/magento setup:static-content:deploy en_US || exit;
  bin/magento deploy:mode:set developer || exit;
  ```

- Databasschema `whitelist.json` - Kör följande CLI-kommando och verifiera att `db_schema_whitelist.json`-filen inte har lagts till eller ändrats.

  ```bash
  bin/magento setup:db-declaration:generate-whitelist --module-name[=MODULE-NAME]
  ```

- Composer validate - Verifiera filen `composer.json` genom att köra följande CLI-kommando i den katalog som innehåller filen `composer.json`.

  ```bash
  composer validate
  ```

- Kodningsstandard - Installera och kör kodningsstandardverktyget och kör det mot din modul. Följande fil visar hur du kan aktivera det för körning var som helst genom att skriva `mcs ./app/code/Vendor/Module/`.

  ```bash
  #!/usr/bin/env bash
  $HOME/web/magento/magento-coding-standard/vendor/bin/phpcs --standard=Magento2 "$@"
  ```

- Phpstan

  ```bash
  ./vendor/bin/phpstan analyze app/code/Vendor/Module
  ```

- PhpStorm-inspektion

- Kopierings-/klistra in-detektor för PHP-storm
