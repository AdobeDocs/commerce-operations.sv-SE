---
title: Information om uppgraderingskompatibilitetsverktyg för utvecklare
description: Anpassa verktyget för uppgraderingskompatibilitet med API-indexintegrering.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 0%

---


# Utvecklarinformation för verktyget Kompatibilitet för uppgradering

Det här avsnittet innehåller information för utvecklare som arbetar nära med Adobe Commerce-koden och vill veta mer om Upgrade Compatibility Tool. Du kan använda den här kunskapen för att anpassa verktygets komponenter.

## Integrering av Adobe Commerce API-index

Adobe Commerce API-indexintegrering är en intern integrationslösning som omfattar en uppsättning verktyg för att utforska Adobe Commerce-tillägg som utvecklats av Adobe, Adobe Commerce Partners och tredjepartsleverantörer baserat på statisk kodanalys.

Integreringen med Adobe Commerce API-index görs genom:

`sut\Domain\MRay\MRayInterface`

Det genomförs via `config/services.yaml` -fil. Dess värde avgör var metodens respons `api()` och `modules()` kommer från.

Redigera den här filen för att anpassa svaret efter installationen. Ersätt värdet som tilldelats `sut\Domain\MRay\MRayInterface`:

### Exempel på ett anpassat värde

`sut\Domain\MRay\MRayInterface : "@sut_mray_mock"`

I föregående exempel använder verktyget Kompatibilitet för uppgradering `@sut_mray_mock` som `MRayInterface` implementering. Svaren från `api()` och `modules()` -metoder kommer från följande filer:

- `dev/mray_mock_files/api.json`
- `dev/mray_mock_files/modules.json`

>[!NOTE]
>
>När du ändrar `services.yaml` filen, ta bort `var/cache/` för att tillämpa ändringarna korrekt.

## Enhetstestning

Kör något av följande kommandon när du vill köra enhetstester:

- `vendor/bin/phpunit tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist tests/unit`
- `vendor/bin/phpunit -c tests/unit/phpunit.xml.dist --testsuite=unit-tests`

## Integrationstestning

Kör något av följande kommandon när du vill köra integreringstester:

- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist tests/integration`
- `vendor/bin/phpunit -c tests/integration/phpunit.xml.dist --testsuite=integration-tests`

## Acceptanstest

1. Innan du utför accepteringstester måste du ange Adobe Commerce-URL:en i `phpunit` konfigurationsfil.
1. Kopiera standard `tests/acceptance/phpunit.xml` -fil (utan .dist-suffixet).
1. Ändra `TESTS_BASE_URL` värde för att peka på den Adobe Commerce-URL som du vill testa.
1. Kör något av följande kommandon om du vill köra accepttesterna:

   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml tests/acceptance`
   - `vendor/bin/phpunit -c tests/acceptance/phpunit.xml --testsuite=acceptance-tests`

## GraphQL-enhetstestning och ESLint-kodanalys

### Krav

>[!NOTE]
>
>Du måste ha Node.js på datorn, se [Node.js-dokumentation](https://nodejs.dev/learn/how-to-install-nodejs).

Följande instruktioner gäller för MacOS-system:

1. Öppna en terminal och navigera till projektets rotkatalog.
1. Installera projektberoenden:

   ```bash
   npm install
   ```

### GraphQL-enhetstestning

The [Jest](https://jestjs.io/docs/getting-started) ramverket användes för att skapa dessa JS-enhetstester:

Testerna är inne `dev/tests/Js`.

Strängscheman för testning finns i `dev/tests/Acceptance/_files/graphql_schemas`.

Kör enhetstester `jest` enligt följande:

```bash
./node_modules/.bin/jest --verbose --rootDir=dev/tests/Js/
```

### ESLint-kodanalys

[ESLint](https://eslint.org/docs/user-guide/getting-started) är ett statiskt kodanalysverktyg för att identifiera problematiska mönster i JavaScript-kod, med målet att göra koden mer konsekvent och undvika buggar.

Kör `eslint` kodanalys enligt följande:

```bash
./node_modules/.bin/eslint -c dev/tests/Static/.eslintrc --rulesdir vendor/magento/magento-coding-standard/eslint/rules path/to/analyse
```

## Komplexitetspoäng

The **komplexitetspoäng** är en bild som visar hur svårt det kan vara att uppgradera från den aktuella versionen till den nya. Lägre antal innebär enklare uppgraderingar.

>[!NOTE]
>
>Komplexitetspoängen varierar mellan 0 och ∞.

Poängen baseras på resultaten från analysen:

- Antal identifierade problem
- Allvarlighetsgrad för identifierade problem

Upgrade Compatibility Tool beräknar poängen enligt nedanstående formel.

### Formel för komplexitetspoäng

`Complexity Score = (Critical issues * 3) + (Errors *2) + Warnings`

>[!WARNING]
>
>Detta är absoluta värden.
