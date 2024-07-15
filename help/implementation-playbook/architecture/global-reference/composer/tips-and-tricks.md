---
title: Tips och tricks för disposition
description: Lär dig mer om vanliga utvecklingsåtgärder i Composer och riktlinjer för att snabbt lösa problem.
feature: Best Practices
role: Developer
hide: true
hidefromtoc: true
exl-id: 5ead5fb1-3bb3-4e77-a4f1-8e10c4f91efb
source-git-commit: 80cf4dc2b5c9dd690aee1b224fbe6c766fe8f2ab
workflow-type: tm+mt
source-wordcount: '535'
ht-degree: 0%

---

# Tips och tricks för disposition

Det kan uppstå problem när du utvecklar Adobe Commerce-moduler med Composer. Dessa metodtips beskriver några vanliga uppgifter som underlättar utvecklingen och hjälper dig att snabbt lösa problem.

>[!NOTE]
>
>Dessa riktlinjer gäller främst för [GRA ](../overview.md)-projekt (Global Reference Architecture).

## Snabba upp disposition

Installera [https://github.com/hirak/prestissimo](https://github.com/hirak/prestissimo) om du vill snabba upp Composer med asynkrona pakethämtningar.

```bash
composer global require hirak/prestissimo
```

Om du får problem avinstallerar du `prestissimo`:

```bash
composer global remove hirak/prestissimo
```

## Lös vaga versionsproblem

Composer kan ibland hamna i ett dödläge med paketversioner. Du kan se meddelanden om versioner som är inkompatibla även om de inte är det. Försök att återställa Composer innan du felsöker kompatibilitetsproblem:

1. Rensa cacheminnet för Composer.

   ```bash
   composer clearcache
   ```

1. Ta bort filen `composer.lock` för alla paket.

   ```bash
   rm -rf vendor/* composer.lock
   ```

1. Installera om Composer-paketen.

   ```bash
   composer install
   ```

>[!TIP]
>
>Dessa steg uppdaterar alla paket till den senaste tillgängliga versionen. Återställ filen `composer.lock` från Git om du vill ångra uppgraderingarna.

## Sök efter möjliga uppdateringar i klientpaket

1. Ta reda på vilka paket som kan vara inaktuella.

   ```bash
   composer outdated
   ```

1. Filtrera med jokertecken och/eller alternativet `--minor-only` om du vill hoppa över bakåtkompatibla uppgraderingar:

   ```bash
   composer outdated 'magento/*'
   composer outdated --minor-only 'magento/*'
   ```

## Ta reda på om en modul är installerad

Visa information om alla installerade paket på en Git-gren.

```bash
composer info
```

Kör `composer install` efter Git-växling och innan du kör `composer info`. I annat fall visar Composer information om den föregående grenen som du checkat ut.

>[!TIP]
>
>Använd något av följande kommandon om du vill filtrera eller söka.
>
>```bash
>composer info '*magento*'
>composer info | grep magento
>```

## Ta reda på varför ett (specifik version av ett) paket är installerat

Ibland installerar Composer den senaste tillgängliga versionen av ett paket på grund av ett strikt beroende i ett annat paket.

Ta reda på om det finns ett strikt beroende i ett annat paket.

```bash
composer why client/module-example
```

Om resultatet visar en lista med metapaket eller ett annat paket som inte uttryckligen krävs kör du kommandot på det paketet:

```bash
composer why example/metapackage
```

## Ta reda på varför ett paket inte är installerat

Ibland installerar inte Composer ett paket eftersom det är i konflikt med ett annat paket, ett annat paket ersätter det eller eftersom du inte har definierat det som ett beroende.

Ta reda på varför ett paket inte är installerat.

```bash
composer why-not client/module-example
```

## Använd en privat Composer-databas som värd

Om du behöver en privat Composer-databas använder du [Privat Packagist](https://packagist.com/) eller [JFrog Artifactory](https://jfrog.com/integration/php-composer-repository/). Använd inte [Satis](https://github.com/composer/satis).

- **Privat Packagist** är säker, kostar cirka 600 USD per år med tre administratörsanvändare och är värd för den.

- **JFrog Artifactory** kostar 1 176 USD per år. Det används inte lika ofta som Packagist, men har stöd för fler språk än PHP.

- **Satis** har ingen inbyggd säkerhet, ingen automatisering och kräver ytterligare värdtjänster. Det är bara gratis om din tid också är gratis.

## Versionspaket

Använd [Semantisk version 2.0.0](https://semver.org/spec/v2.0.0.html) enligt beskrivningen i Adobe Commerce [versionshanteringsschema](https://developer.adobe.com/commerce/php/development/versioning/). Uppfinna inte hjulet på nytt.

Om du vill se Adobe Commerce-modulberoenden följer du dokumentationen för [modulens versionsberoenden](https://developer.adobe.com/commerce/php/development/versioning/dependencies/).

Använd inte versionsdefinitionen i filen `composer.json`. Använd i stället Git-taggar för versioner. Se [Dispositionsversioner och -begränsningar](https://getcomposer.org/doc/articles/versions.md#versions-and-constraints).

## Var moduler som kommer in i en arkivfil och inte via Composer ska placeras

Skapa en Git-databas för moduler i ett arkiv och lagra dem själv. Alla Adobe Commerce-moduler har en `composer.json`-fil. När du har lagrat den i Git och synkroniserat den med en privat paketerare kan du installera den med Composer.

När du får en ny version av paketet överför du koden till Git, taggar den och installerar den nya versionen med Composer.
