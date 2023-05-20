---
title: Distributionsflöde
description: Lär dig mer om de steg som krävs för att distribuera Adobe Commerce eller Magento Open Source i en produktionsmiljö.
exl-id: 88da0b1b-5aa7-4f1c-9d01-ae58324b2754
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 0%

---

# Distributionsflöde

The [!DNL Commerce] produktionsflöde hjälper butiken att uppnå maximala prestanda.

## Installera beroenden

The `composer.json` och `composer.lock` filer hantera [!DNL Commerce] och installera rätt version för varje paket. Du måste installera beroenden innan [anvisningar för förbehandling av beroendeinjicering](#preprocess-dependency-injection-instructions) om du tänker uppdatera [autoloader](#update-the-autoloader).

Installera [!DNL Commerce] beroenden:

```bash
composer install --no-dev
```

## Instruktioner för förprocessberoende injektion

Magento:

* Läser och bearbetar alla aktuella konfigurationer
* Analyserar beroenden mellan klasser
* Skapar automatiskt genererade filer (inklusive utkast, fabriker osv.)
* Lagrar kompilerade data och konfigurationer i ett cacheminne som sparar upp till 25 % av tiden för behandling av begäranden

Så här förbearbetar och kompilerar du DI-instruktioner:

```bash
bin/magento setup:di:compile
```

## Uppdatera den automatiska inläsaren

När kompileringen är klar bekräftar du att [APCu är aktiverat](../performance/software.md#php-settings) och uppdatera den automatiska inläsaren:

Så här uppdaterar du den automatiska inläsaren:

>[!INFO]
>
>The `-o` gör att automatisk inläsning av PSR-0/4 konverteras till klassmappning för att få en snabbare automatisk inläsare. The `--apcu` används APCu för att cachelagra klasser som hittas eller inte hittas.

```bash
composer dump-autoload -o --apcu
```

Om du tänker uppdatera den automatiska inläsaren måste du köra följande kommandon i ordning:

```bash
composer install --no-dev
```

```bash
bin/magento setup:di:compile
```

```bash
composer dump-autoload -o
```

```bash
bin/magento setup:static-content:deploy
```

## Distribuera statiskt innehåll

Distribuera statiskt innehåll orsakar [!DNL Commerce] för att utföra följande åtgärder:

* Analysera alla statiska resurser
* Sammanfoga, minimera och paketera innehåll
* Läsa och bearbeta temadata
* Analysera temaflöde
* Lagra allt bearbetat och materialiserat innehåll i en viss mapp för ytterligare användning

Om ditt statiska innehåll inte distribueras, [!DNL Commerce] utför alla listade åtgärder på direkten, vilket leder till en avsevärd ökning av svarstiden.

Du kan använda en mängd alternativ för att anpassa distributionsåtgärder baserat på butikens storlek och leveransbehov. Den vanligaste är den kompakta distributionsstrategin. Se [Distributionsstrategier för statiska filer](../configuration/cli/static-view-file-strategy.md)

Så här distribuerar du statiskt innehåll:

```bash
bin/magento setup:static-content:deploy
```

Med det här kommandot kan Composer återskapa mappningen till projektfiler så att de läses in snabbare.

## Ange produktionsläge

>[!INFO]
>
>Ställa in läget till produktion körs automatiskt `setup:di:compile` och `setup:static-content:deploy`.

Slutligen måste du placera butiken i produktionsläge. Produktionsläget är specifikt optimerat för att ge butiken maximala prestanda. Den inaktiverar även alla utvecklarspecifika funktioner. Detta kan du göra i `.htaccess` eller `nginx.conf` fil:

`SetEnv MAGE_MODE production`

Du kan också distribuera statiskt innehåll, kompilera innehållet och ställa in läget med ett CLI-kommando:

```bash
bin/magento deploy:mode:set production
```

Kommandot körs i bakgrunden och du kan inte ange ytterligare alternativ för varje steg.

## Ytterligare åtgärder före start

Dessa steg rekommenderas, men är inte obligatoriska. Du kan utföra dem direkt innan du startar butiken i produktionsläge. Listan innehåller:

* Indexera om data för att undvika att det finns inkonsekventa data i indexen.
* Töm cacheminnet för att vara säker på att inga gamla eller felaktiga data finns kvar i cacheminnet.
* Öka cacheminnet, som i förväg anropar de populäraste eller mest kritiska lagringssidorna, så att cacheminnet för dem genereras och lagras. Den här åtgärden kan utföras med alla Internet-crawler eller manuellt om du har en liten butik.
