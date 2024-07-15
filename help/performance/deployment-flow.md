---
title: Distributionsflöde
description: Lär dig mer om de steg som krävs för att distribuera Adobe Commerce i en produktionsmiljö.
feature: Best Practices, Deploy
exl-id: 88da0b1b-5aa7-4f1c-9d01-ae58324b2754
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# Distributionsflöde

Produktionsdistributionsflödet [!DNL Commerce] hjälper en butik att uppnå maximala prestanda.

## Installera beroenden

Filerna `composer.json` och `composer.lock` hanterar [!DNL Commerce] beroenden och installerar rätt version för varje paket. Du måste installera beroenden innan [förbearbetar beroendeinmatningsinstruktionerna](#preprocess-dependency-injection-instructions) om du tänker uppdatera [autoloader](#update-the-autoloader).

Så här installerar du [!DNL Commerce] beroenden:

```bash
composer install --no-dev
```

## Instruktioner för förprocessberoende injektion

När du förbearbetar och kompilerar instruktioner för beroendeinjicering (DI), Magento:

* Läser och bearbetar alla aktuella konfigurationer
* Analyserar beroenden mellan klasser
* Skapar automatiskt genererade filer (inklusive utkast, fabriker osv.)
* Lagrar kompilerade data och konfigurationer i ett cacheminne som sparar upp till 25 % av tiden för behandling av begäranden

Så här förbearbetar och kompilerar du DI-instruktioner:

```bash
bin/magento setup:di:compile
```

## Uppdatera den automatiska inläsaren

När kompileringen är klar bekräftar du att [APCu är aktiverad](../performance/software.md#php-settings) och uppdaterar den automatiska inläsaren:

Så här uppdaterar du den automatiska inläsaren:

>[!INFO]
>
>Alternativet `-o` konverterar automatisk inläsning av PSR-0/4 till en klassmappning för att få en snabbare automatisk inläsare. Alternativet `--apcu` använder APCu för att cachelagra klasser som hittats eller inte hittats.

```bash
composer dump-autoload -o --apcu
```

Om du planerar att uppdatera den automatiska inläsaren måste du köra följande kommandon i ordning:

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

Distribuering av statiskt innehåll gör att [!DNL Commerce] utför följande åtgärder:

* Analysera alla statiska resurser
* Sammanfoga, minimera och paketera innehåll
* Läsa och bearbeta temadata
* Analysera temaflöde
* Lagra allt bearbetat och materialiserat innehåll i en viss mapp för ytterligare användning

Om ditt statiska innehåll inte distribueras utför [!DNL Commerce] alla listade åtgärder direkt, vilket leder till en avsevärd ökning av svarstiden.

Du kan använda en mängd alternativ för att anpassa distributionsåtgärder baserat på butikens storlek och leveransbehov. Den vanligaste är den kompakta distributionsstrategin. Se [Statiska distributionsstrategier för filer](../configuration/cli/static-view-file-strategy.md)

Så här distribuerar du statiskt innehåll:

```bash
bin/magento setup:static-content:deploy
```

Med det här kommandot kan Composer återskapa mappningen till projektfiler så att de läses in snabbare.

## Ange produktionsläge

>[!INFO]
>
>Om du ställer in läget på produktion körs `setup:di:compile` och `setup:static-content:deploy` automatiskt.

Slutligen måste du placera butiken i produktionsläge. Produktionsläget är specifikt optimerat för att ge butiken maximala prestanda. Den inaktiverar även alla utvecklarspecifika funktioner. Detta kan du göra i din `.htaccess`- eller `nginx.conf`-fil:

`SetEnv MAGE_MODE production`

Du kan också distribuera statiskt innehåll, kompilera innehållet och ställa in läget med ett CLI-kommando:

```bash
bin/magento deploy:mode:set production
```

Kommandot körs i bakgrunden och du kan inte ange ytterligare alternativ för varje steg.

## Ytterligare åtgärder före start

Dessa steg rekommenderas, men är inte obligatoriska. Du kan utföra dem direkt innan du startar butiken i produktionsläge. Listan innehåller:

* Indexera om data för att undvika att det finns inkonsekventa data i indexen.
* Töm cacheminnet så att inga gamla eller felaktiga data finns kvar i cacheminnet.
* Öka cacheminnet, som i förväg anropar de populäraste eller mest kritiska lagringssidorna, så att cacheminnet för dem genereras och lagras. Den här åtgärden kan utföras med alla Internet-crawler eller manuellt om du har en liten butik.
