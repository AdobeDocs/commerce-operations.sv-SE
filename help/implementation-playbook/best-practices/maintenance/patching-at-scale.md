---
title: Bästa tillvägagångssätt för att distribuera patchar i stor skala
description: Se hur centraliserad patchning för Adobe Commerce kan hjälpa er att hantera företagsprojekt.
role: Developer
feature: Best Practices
badge: label="Medverkad av Anton Evers, Sr. Technical Architect, Adobe" type="Informative" url="https://www.linkedin.com/in/anton-evers/" tooltip="Medverkad av Anton Evers"
source-git-commit: 9cda88a4aeb4cc58d8ec9c4417e3107885a6cdb8
workflow-type: tm+mt
source-wordcount: '1309'
ht-degree: 0%

---


# Bästa tillvägagångssätt för att distribuera Adobe Commerce-patchar i stor skala

Om du hanterar flera Adobe Commerce-installationer [patchning](../../../upgrade/patches/apply.md) kan vara en komplex process. _Centraliserad korrigering_ är en viktig del av [global referensarkitektur](../../architecture/global-reference/overview.md) och en god praxis för företag. Det hjälper er att installera rätt patchar på alla era Adobe Commerce-installationer. I det här avsnittet beskrivs hur du uppnår centraliserad distribution av korrigeringsfiler för alla typer av Adobe Commerce [patchar](../../../upgrade/patches/overview.md).

>[!NOTE]
>
>Följande innehåll publicerades ursprungligen i [Distribuera skalbara Adobe Commerce-korrigeringsfiler](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20) inlägg på Adobe Tech Blog. Den har ändrats så att den fokuserar på steg och kodexempel för implementering av en centraliserad patchningsstrategi. Se det ursprungliga inlägget för mer information om de olika typer av korrigeringar som beskrivs här.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce på plats

## Strategi

Eftersom det finns många olika typer av patchar och många sätt att tillämpa dem, hur vet du vilken korrigering som används först? Ju fler korrigeringar du har, desto större chans att de gäller för samma fil eller för samma kodrad. Patchar tillämpas i följande ordning:

1. **Säkerhetsuppdateringar** ingår i den statiska kodbasen i en Adobe Commerce-release.
1. **Composer-patchar** via `composer install` och `composer update` plugin-program som [cweagans/Composer-patches](https://packagist.org/packages/cweagans/composer-patches).
1. Alla **nödvändiga korrigeringar** som ingår i [Cloud Patches for Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html) paket.
1. Markerad **kvalitetspatchar** som ingår i [!DNL [Quality Patches Tool]](../../../tools/quality-patches-tool/usage.md).
1. **Egna patchar** och Adobe Commerce Support-patchar i `/m2-hotfixes` i alfabetisk ordning efter korrigeringens namn.

   >[!IMPORTANT]
   >
   >Ju fler korrigeringar du använder, desto mer komplex blir koden. Komplex kod kan göra det svårare att uppgradera till en ny version av Adobe och öka den totala ägandekostnaden.

Om du ansvarar för att underhålla flera installationer av Adobe Commerce kan det vara en utmaning att se till att alla instanser har samma uppsättning installerade patchar. Varje installation har en egen Git-databas, `/m2-hotfixes` och `composer.json` -fil. Den enda garanti du har är att **säkerhetspatchar** och **nödvändiga korrigeringar** för molnanvändare installeras som en del av Adobe Commerce huvudversion.

För närvarande finns det ingen centraliserad lösning på det här problemet, men Composer erbjuder ett sätt att överbrygga gapet. The [`cweagans/composer-patches`](https://packagist.org/packages/cweagans/composer-patches) kan du [tillämpa korrigeringar från beroenden](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies). Du kan skapa ett Composer-paket som installerar alla korrigeringsfiler och sedan kräva paketet i alla dina projekt.

Detta omfattar **säkerhetspatchar**, **nödvändiga korrigeringar** och **Composer-patchar** men vad gäller kvalitetspatchar och innehållet i `/m2-hotfixes` katalog?

## Använd patchar och snabbkorrigeringar av hög kvalitet

Du kan installera kvalitetsuppdateringar både i molninfrastrukturen och på lokala installationer med `vendor/bin/magento-patches apply` -kommando. Du måste se till att `vendor/bin/magento-patches apply` kommandot körs efter `composer install` åtgärder.

>[!NOTE]
>
>I molninfrastrukturen kan du även installera kvalitetspatchar genom att ange dem i projektets `.magento.env.yaml` -fil. Exemplet som beskrivs här kräver att du använder `vendor/bin/magento-patches apply` -kommando.

Du kan ange vilka korrigeringsfiler som ska användas i `composer.json` filen för ett anpassat Composer-komponentpaket och skapa sedan ett plugin-paket som kör kommandot efter `composer install` åtgärder.

Sammanfattningsvis kräver det här centraliserade korrigeringsexemplet att du skapar två anpassade Composer-paket:

- **Komponentpaket:** `centralized-patcher`

   - Definierar listan med kvalitetspatchar och `m2-hotfixes` för installation
   - Kräver `centralized-patcher-composer-plugin` paketet, som kör `vendor/bin/magento-patches apply` kommando efter `composer install` operationer

- **Plugin-paket:** `centralized-patcher-composer-plugin`

   - Definierar en `CentralizedPatcher` PHP-klass som läser listan med kvalitetspatchar i `centralized-patcher` package
   - Kör `vendor/bin/magento-patches apply` för att installera listan med kvalitetspatchar efter `composer install` operationer

### `centralized-patcher`

Du kan skapa ett Composer-komponentpaket (`centralized-patcher`) för att centralt hantera alla kvalitetspatchar och `/m2-hotfixes` i alla dina Adobe Commerce-installationer.

Komponentpaketet måste:

- Kopiera innehållet i `/m2-hotfixes` i alla installationer under driftsättningen.
- Definiera listan med kvalitetspatchar som ska installeras.
- Kör `vendor/bin/magento-patches` för att installera samma lista med kvalitetspatchar i alla installationer (med [`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin) plugin-paket som ett beroende).

Skapa `centralized-patcher` komponentpaket:

1. Skapa en `composer.json` fil med följande innehåll:

   >[!NOTE]
   >
   >The `require` i följande exempel visas ett `require` beroende av [plugin-paket](#centralized-patcher-composer-plugin) som du måste skapa senare i exemplet.

   ```json
   {
    "name": "magento-services/centralized-patcher",
    "version": "0.0.1",
    "description": "Centralized patcher for patching multiple web stores from a central place",
    "type": "magento2-component",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "magento-services/centralized-patcher-composer-plugin": "~0.0.1"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "extra": {
        "map": [
        ],
   }
   ```

1. Skapa en `/m2-hotfixes` i paketet och lägg till det i `map` attribut i `composer.json` -fil. The `map` -attributet innehåller filer som ska kopieras från det här paketet till roten för det målprojekt som du vill korrigera.

   ```json
   {
    ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
   }
   ```

   >[!NOTE]
   >
   >The `centralized-patcher` paketet kopierar innehållet i `/m2-hotfixes` katalogen till katalogen m2-hotfixes för målprojektet på `composer install`.  Eftersom molndistributionsskripten tillämpar m2-snabbkorrigeringar efter `composer install`, installeras alla snabbkorrigeringar av distributionsmekanismen.

1. Definiera de kvalitetspatchar som ska installeras i `quality-patches` -attribut.

   ```json
   {
   ...
    "extra": {
        "map": [
            [
                "/m2-hotfixes",
                "/m2-hotfixes"
            ]
        ],
        "quality-patches": [
            "MDVA-30106",
            "MDVA-12304"
        ]
   }
   ```


The `quality-patches` -attributet i föregående kodexempel innehåller två patchar från [fullständig korrigeringslista](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) som ett exempel.  Dessa kvalitetsuppdateringar installeras i alla projekt som kräver `centralized-patcher` paket med `vendor/bin/magento-patches apply` -kommando.

I testsyfte kan du skapa en exempelkorrigering (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`).

>[!NOTE]
>
>Du bör placera dina egna patchar i `m2-hotfixes` tillsammans med patchar som du får direkt från Adobe Commerce Support.

En exempelkorrigeringsfil (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`):

```diff
diff --git a/vendor/magento/framework/Mview/View/Subscription.php b/vendor/magento/framework/Mview/View/Subscription.php
index 03a3bf9..681e0b0 100644
--- a/vendor/magento/framework/Mview/View/Subscription.php
+++ b/vendor/magento/framework/Mview/View/Subscription.php
@@ -16,6 +16,7 @@ use Magento\Framework\Mview\ViewInterface;
 
 /**
  * Mview subscription.
+ * Test Patch File
  */
 class Subscription implements SubscriptionInterface
 {
```

### `centralized-patcher-composer-plugin`

Eftersom det här exemplet använder den lokala metoden för att installera kvalitetspatchar måste du se till att `vendor/bin/magento-patches apply` kommandot körs efter `composer install` åtgärder. Detta plugin-program aktiveras efter `composer install` -åtgärder, som kör `vendor/bin/magento-patches apply` -kommando.

Skapa `centralized-patcher-compose-plugin` komponentpaket:

1. Skapa en `composer.json` fil med följande innehåll:

   ```json
   {
    "name": "magento-services/centralized-patcher-composer-plugin",
    "version": "0.0.1",
    "description": "Centralized patcher composer plugin to apply quality patches from the centralized patcher",
    "type": "composer-plugin",
    "license": [
        "OSL-3.0",
        "AFL-3.0"
    ],
    "require": {
        "symfony/process": "^4.1 || ^5.1",
        "magento/magento-cloud-patches": "~1.0.20",
        "magento/framework": "~103.0.5-p1",
        "composer-plugin-api": "^2.0"
    },
    "require-dev": {
        "composer/composer": "^2.0"
    },
    "suggest": {
        "magento-services/centralized-patcher": "~0.0.1"
    },
    "autoload": {
        "psr-4": {
            "MagentoServices\\CentralizedPatcherComposerPlugin\\": ""
        }
    },
    "extra": {
        "class": "MagentoServices\\CentralizedPatcherComposerPlugin\\Patcher"
    }
   }
   ```

1. Skapa en PHP-fil och definiera en `CentralizedPatcher` för att läsa listan med kvalitetspatchar från [`centralized-patcher`](#centralized-patcher) komponentpaket och installera dem direkt efter varje `composer install` operation.

   ```php
   <?php
   declare(strict_types=1);
   
   namespace MagentoServices\CentralizedPatcherComposerPlugin;
   
   use Composer\Composer;
   use Composer\EventDispatcher\EventSubscriberInterface;
   use Composer\IO\IOInterface;
   use Composer\Plugin\PluginInterface;
   use Composer\Script\ScriptEvents;
   use Symfony\Component\Process\Exception\ProcessFailedException;
   use Symfony\Component\Process\Process;
   
   class Patcher implements PluginInterface, EventSubscriberInterface
   {
    /**
     * @var Composer $composer
     */
    protected $composer;
   
    /**
     * @var IOInterface $io
     */
    protected $io;
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function activate(Composer $composer, IOInterface $io)
    {
        $this->composer = $composer;
        $this->io = $io;
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function deactivate(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @param Composer $composer
     * @param IOInterface $io
     * @return void
     */
    public function uninstall(Composer $composer, IOInterface $io)
    {
        // Method must exist
    }
   
    /**
     * @return string[]
     */
    public static function getSubscribedEvents()
    {
        return [
            ScriptEvents::POST_UPDATE_CMD => 'installPatches',
            ScriptEvents::POST_INSTALL_CMD => 'installPatches',
        ];
    }
   
    /**
     * Apply patches from magento-services/centralized-patcher
     *
     * @param \Composer\Script\Event $event
     * @return void
     */
    public function installPatches(\Composer\Script\Event $event)
    {
        $patches = [];
        $this->io->write('Applying centralized quality patches');
        $packages = $this->composer->getLocker()->getLockData()['packages'];
        foreach ($packages as $package) {
            if ($package['name'] !== 'magento-services/centralized-patcher') {
                continue;
            }
            $patches = $package['extra']['quality-patches'] ?? [];
        }
        if (empty($patches)) {
            $this->io->error("No centralized quality patches to install");
            exit(0);
        }
        $command = array_merge(
            ['php','./vendor/bin/magento-patches','apply','--no-interaction'],
             $patches
        );
        $process = new Process($command);
        try {
            $this->io->debug($process->getCommandLine());
            $process->mustRun();
            $this->io->write(
                str_replace("\n\n", "\n", trim($process->getErrorOutput() ?: $process->getOutput(), "\n"))
            );
        } catch (ProcessFailedException $e) {
            $process = $e->getProcess();
            $error = sprintf(
                'The command "%s" failed. %s',
                $process->getCommandLine(),
                trim($process->getErrorOutput() ?: $process->getOutput(), "\n")
            );
            throw new \RuntimeException($error, $process->getExitCode());
        }
    }
   }
   ```

>[!TIP]
>
>Se [code-examples](#code-examples) för att se hur de två paketen som beskrivs i det här exemplet fungerar.


## Så här gör du med projektspecifika korrigeringsfiler

Du kan ha ett scenario där bara 95 % av patcharna krävs i alla projekt, medan några patchar bara gäller för en viss instans. Det vanliga sättet att använda lappning fungerar fortfarande. Du kan behålla projektspecifika korrigeringar i `/m2-hotfixes` katalog och installera kvalitetsuppdateringar per projekt.

Om du använder den här metoden **inte** implementera korrigeringar i `/m2-hotfixes` katalog som har kopierats till ditt projekt av `centralized-patcher` komponentpaket. Du kan förhindra oavsiktliga implementeringar genom att lägga till `/m2-hotfixes` till `.gitignore` -fil. Efter uppdatering av `.gitignore` filen, kom ihåg att alla projektspecifika `/m2-hotfixes` måste läggas till med `git add –force` -kommando.

## Köra olika Adobe Commerce-versioner

Se till att du anger rätt beroende i dialogrutan `centralized-patcher` komponentpaket. Du kan till exempel behöva Adobe Commerce 2.4.5-p2 för en viss version av ditt paket, som bara innehåller korrigeringsfiler som är kompatibla med Adobe Commerce 2.4.5-p2. Du kan ha en annan version av det här paketet som är kompatibel med Adobe Commerce 2.4.4.

## Förstå resultatet

Precis som med Adobe Commerce om molninfrastruktur förutsätter den här artikeln att din distributionsprocess använder `composer install` kommando och inte `composer update` eller `git pull` för att distribuera ny kod till dina servrar. Flödet för centraliserad korrigeringsinstallation ser då ut så här:

1. Installera Composer

   - Installerar Adobe Commerce, inklusive säkerhetsfunktionerna -p1 eller -p2 och funktionspatchar
   - Kombinerar centraliserade `/m2-hotfixes` och har projektspecifika `/m2-hotfixes` och supportpatchar
   - Tillämpar eventuella patchar som har installerats med `cweagans/composer-patches` Kompositpaket

1. Efter `composer install`

   - Composer-pluginen installerar korrigeringsfiler med centraliserad kvalitet

1. Distribution

   - Nödvändiga korrigeringsfiler och projektspecifika korrigeringsfiler installeras baserat på `.magento.env.yaml` fil (Adobe Commerce endast i molninfrastrukturprojekt).
   - Anpassade patchar och supportpatchar från `/m2-hotfixes` -katalogen installeras i alfabetisk ordning efter korrigeringsnamn.

På så sätt kan ni centralt hantera alla patchar för alla era installationer och bättre garantera säkerheten och stabiliteten i era Adobe Commerce-butiker. Använd följande metoder för att kontrollera korrigeringsstatus:

- [Infrastrukturprojekt i molnet](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html#view-available-patches-and-status)
- [Lokala projekt](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## Exempel på koder

- [Centraliserade korrigeringar i Magento Open Source](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [Centraliserade korrigeringsfiler i Adobe Commerce för molninfrastruktur](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [Plugin-program för centraliserad patcher Composer](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [Komponent för centraliserad patcher](https://github.com/AntonEvers/centralized-patcher)
