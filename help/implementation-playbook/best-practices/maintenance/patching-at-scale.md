---
title: Bästa tillvägagångssätt för att distribuera patchar i stor skala
description: Se hur centraliserad patchning för Adobe Commerce kan hjälpa er att hantera företagsprojekt.
role: Developer
feature: Best Practices
badge: label="Medverkad av Tony Evers, Sr. Technical Architect, Adobe" type="Informative" url="https://www.linkedin.com/in/evers-tony/" tooltip="Medverkad av Tony Evers"
exl-id: 08c38dc5-3dc2-49ee-b56f-59e1718e12b5
source-git-commit: 2c9f827326315bc4ef77d511dddce81e059a1092
workflow-type: tm+mt
source-wordcount: '1251'
ht-degree: 0%

---

# Bästa tillvägagångssätt för att distribuera Adobe Commerce-patchar i stor skala

Om du hanterar flera Adobe Commerce-installationer kan [patchning](../../../upgrade/patches/apply.md) vara en komplex process. _Centraliserad korrigering_ är en bra metod för företag. Det hjälper er att installera rätt patchar på alla era Adobe Commerce-installationer. I det här avsnittet beskrivs hur du uppnår centraliserad korrigeringsdistribution för alla typer av Adobe Commerce [korrigeringar](../../../upgrade/patches/overview.md).

>[!NOTE]
>
>Följande innehåll publicerades ursprungligen i [Distribuera Adobe Commerce-korrigeringar vid skalförändring](https://blog.developer.adobe.com/distributing-adobe-commerce-patches-at-scale-137412e05a20) i Adobe Tech Blog. Den har ändrats så att den fokuserar på steg och kodexempel för implementering av en centraliserad patchningsstrategi. Se det ursprungliga inlägget för mer information om de olika typer av korrigeringar som beskrivs här.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce på plats

## Strategi

Eftersom det finns många olika typer av patchar och många sätt att tillämpa dem, hur vet du vilken korrigering som används först? Ju fler korrigeringar du har, desto större chans att de gäller för samma fil eller för samma kodrad. Patchar tillämpas i följande ordning:

1. **Säkerhetsuppdateringar** är en del av den statiska kodbasen i en Adobe Commerce-version.
1. **Composer-korrigeringar** till `composer install` och `composer update` plugin-program som [cweagans/Composer-patches](https://packagist.org/packages/cweagans/composer-patches).
1. Alla **nödvändiga korrigeringsfiler** ingår i [Cloud Patches for Commerce](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/release-notes/cloud-patches.html)-paketet.
1. Markerade **kvalitetspatchar** som ingår i [!DNL [Quality Patches Tool]](../../../tools/quality-patches-tool/usage.md).
1. **Anpassade korrigeringsfiler** och Adobe Commerce Support-korrigeringsfiler i katalogen `/m2-hotfixes` i alfabetisk ordning efter korrigeringsnamn.

   >[!IMPORTANT]
   >
   >Ju fler korrigeringar du använder, desto mer komplex blir koden. Komplex kod kan göra det svårare att uppgradera till en ny version av Adobe och öka den totala ägandekostnaden.

Om du ansvarar för att underhålla flera installationer av Adobe Commerce kan det vara en utmaning att se till att alla instanser har samma uppsättning installerade patchar. Varje installation har en egen Git-databas, `/m2-hotfixes`-katalog och `composer.json`-fil. Den enda garanti du har är att **säkerhetspatcharna** och **nödvändiga korrigeringsfiler** för molnanvändare installeras som en del av Adobe Commerce huvudversion.

För närvarande finns det ingen centraliserad lösning på det här problemet, men Composer erbjuder ett sätt att överbrygga gapet. Med paketet [`cweagans/composer-patches`](https://packagist.org/packages/cweagans/composer-patches) kan du [använda korrigeringar från beroenden](https://github.com/cweagans/composer-patches/tree/1.x#allowing-patches-to-be-applied-from-dependencies). Du kan skapa ett Composer-paket som installerar alla korrigeringsfiler och sedan kräva paketet i alla dina projekt.

Det omfattar **säkerhetspatchar**, **nödvändiga patchar** och **Composer-patchar**, men vad gäller kvalitetspatchar och innehållet i katalogen `/m2-hotfixes`?

## Använd patchar och snabbkorrigeringar av hög kvalitet

Du kan installera kvalitetsuppdateringar på både molninfrastruktur och lokala installationer med kommandot `vendor/bin/magento-patches apply`. Du måste se till att kommandot `vendor/bin/magento-patches apply` körs efter `composer install`-åtgärder.

>[!NOTE]
>
>I molninfrastrukturen kan du även installera kvalitetspatchar genom att ange dem i projektets `.magento.env.yaml`-fil. Exemplet som beskrivs här kräver att du använder kommandot `vendor/bin/magento-patches apply`.

Du kan ange vilka korrigeringsfiler som ska användas i filen `composer.json` för ett anpassat Composer-komponentpaket och sedan skapa ett plugin-paket som kör kommandot efter `composer install` -åtgärder.

Sammanfattningsvis kräver det här centraliserade korrigeringsexemplet att du skapar två anpassade Composer-paket:

- **Komponentpaket:** `centralized-patcher`

   - Definierar listan med kvalitetspatchar och `m2-hotfixes` som ska installeras
   - Kräver paketet `centralized-patcher-composer-plugin`, som kör kommandot `vendor/bin/magento-patches apply` efter `composer install`-åtgärder

- **Plugin-paket:** `centralized-patcher-composer-plugin`

   - Definierar en `CentralizedPatcher` PHP-klass som läser listan med kvalitetspatchar från paketet `centralized-patcher`
   - Kör kommandot `vendor/bin/magento-patches apply` för att installera listan med kvalitetsuppdateringar efter `composer install`-åtgärder

### `centralized-patcher`

Du kan skapa ett Composer-komponentpaket (`centralized-patcher`) för att hantera alla kvalitetspatchar och `/m2-hotfixes` centralt i alla dina Adobe Commerce-installationer.

Komponentpaketet måste:

- Kopiera innehållet i katalogen `/m2-hotfixes` till alla dina installationer under distributionen.
- Definiera listan med kvalitetspatchar som ska installeras.
- Kör kommandot `vendor/bin/magento-patches` om du vill installera samma lista över kvalitetspatchar i alla installationer (med plugin-paketet [`centralized-patcher-composer-plugin`](#centralized-patcher-composer-plugin) som ett beroende).

Så här skapar du komponentpaketet `centralized-patcher`:

1. Skapa en `composer.json`-fil med följande innehåll:

   >[!NOTE]
   >
   >Attributet `require` i följande exempel visar ett `require`-beroende av det [plugin-paket](#centralized-patcher-composer-plugin) som du måste skapa senare i det här exemplet.

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

1. Skapa en `/m2-hotfixes`-katalog i ditt paket och lägg till den i attributet `map` i din `composer.json`-fil. Attributet `map` innehåller filer som ska kopieras från det här paketet till roten för det målprojekt som du vill korrigera.

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
   >Paketet `centralized-patcher` kopierar innehållet i katalogen `/m2-hotfixes` till katalogen m2-hotfixes för målprojektet på `composer install`.  Eftersom molndistributionsskripten tillämpar m2-snabbkorrigeringar efter `composer install` installeras alla snabbkorrigeringar av distributionsmekanismen.

1. Definiera de kvalitetspatchar som ska installeras i attributet `quality-patches`.

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


Attributet `quality-patches` i föregående kodexempel innehåller två korrigeringar från [hela korrigeringslistan](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) som exempel.  Dessa kvalitetsuppdateringar installeras i alla projekt som kräver paketet `centralized-patcher` med kommandot `vendor/bin/magento-patches apply`.

I testsyfte kan du skapa en exempelkorrigering (`/m2-hotfixes/EXAMPLE-PATCH_2.4.6.patch`).

>[!NOTE]
>
>Du bör placera dina egna korrigeringsfiler i katalogen `m2-hotfixes` tillsammans med korrigeringsfiler som du får direkt från Adobe Commerce Support.

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

Eftersom det här exemplet använder den lokala metoden för att installera kvalitetsuppdateringar måste du se till att kommandot `vendor/bin/magento-patches apply` körs efter `composer install`-åtgärder. Detta plugin-program aktiveras efter `composer install`-åtgärder, som kör kommandot `vendor/bin/magento-patches apply`.

Så här skapar du komponentpaketet `centralized-patcher-compose-plugin`:

1. Skapa en `composer.json`-fil med följande innehåll:

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

1. Skapa en PHP-fil och definiera en `CentralizedPatcher`-klass för att läsa listan med kvalitetspatchar från [`centralized-patcher`](#centralized-patcher)-komponentpaketet och installera dem direkt efter varje `composer install` -åtgärd.

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

Du kan ha ett scenario där bara 95 % av patcharna krävs i alla projekt, medan några patchar bara gäller för en viss instans. Det vanliga sättet att använda lappning fungerar fortfarande. Du kan behålla projektspecifika korrigeringsfiler i katalogen `/m2-hotfixes` och installera korrigeringsfiler för kvalitet per projekt.

Om du använder det här arbetssättet utför **inte** några korrigeringar i katalogen `/m2-hotfixes` som har kopierats till ditt projekt av komponentpaketet `centralized-patcher`. Du kan förhindra oavsiktliga implementeringar genom att lägga till `/m2-hotfixes` i `.gitignore`-filen. När du har uppdaterat filen `.gitignore` måste du komma ihåg att alla projektspecifika `/m2-hotfixes` måste läggas till med kommandot `git add –force`.

## Köra olika Adobe Commerce-versioner

Se till att du anger rätt beroende i `centralized-patcher`-komponentpaketet. Du kan till exempel behöva Adobe Commerce 2.4.5-p2 för en viss version av ditt paket, som bara innehåller korrigeringsfiler som är kompatibla med Adobe Commerce 2.4.5-p2. Du kan ha en annan version av det här paketet som är kompatibel med Adobe Commerce 2.4.4.

## Förstå resultatet

Precis som med Adobe Commerce i molninfrastrukturen förutsätter den här artikeln att din distributionsprocess använder kommandot `composer install` och inte `composer update` eller `git pull` för att distribuera ny kod till dina servrar. Flödet för centraliserad korrigeringsinstallation ser då ut så här:

1. Installera Composer

   - Installerar Adobe Commerce, inklusive säkerhetsfunktionerna -p1 eller -p2 och funktionspatchar
   - Kombinerar centraliserade `/m2-hotfixes` och supportpatchar med projektspecifika `/m2-hotfixes` och supportpatchar
   - Tillämpar eventuella korrigeringar som har installerats med Composer-paketet `cweagans/composer-patches`

1. Efter `composer install`

   - Composer-pluginen installerar korrigeringsfiler med centraliserad kvalitet

1. Distribution

   - Nödvändiga korrigeringsfiler och projektspecifika kvalitetspatchar installeras baserat på filen `.magento.env.yaml` (endast Adobe Commerce i molninfrastrukturprojekt).
   - Anpassade korrigeringsfiler och supportkorrigeringsfiler från katalogen `/m2-hotfixes` installeras i alfabetisk ordning efter korrigeringsnamn.

På så sätt kan ni centralt hantera alla patchar för alla era installationer och bättre garantera säkerheten och stabiliteten i era Adobe Commerce-butiker. Använd följande metoder för att kontrollera korrigeringsstatus:

- [Molninfrastrukturprojekt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html#view-available-patches-and-status)
- [Lokala projekt](../../../tools/quality-patches-tool/usage.md#view-individual-patches)

## Exempel på koder

- [Centraliserade korrigeringar i Magento Open Source](https://github.com/AntonEvers/centralized-patches-on-magento-open-source)
- [Centraliserade korrigeringar i Adobe Commerce i molninfrastruktur](https://github.com/AntonEvers/centralized-patches-on-adobe-commerce-cloud)
- [Plugin-programmet för centraliserad patcher Composer](https://github.com/AntonEvers/centralized-patcher-composer-plugin)
- [Central patchkomponent](https://github.com/AntonEvers/centralized-patcher)
