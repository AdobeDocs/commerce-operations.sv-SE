---
source-git-commit: 9eeb0e3a1c75b25cc70b092d23f02ebfe355d6bd
workflow-type: tm+mt
source-wordcount: '377'
ht-degree: 0%

---
# Fragment

## Endast Commerce {#commerce-only}

>[!NOTE]
>
>[!DNL Upgrade Compatibility Tool] är endast tillgänglig för Adobe Commerce-instanser.

<!-- Configuration guide snippets -->

## Ägare till filsystem {#file-system-owner}

>[!WARNING]
>
>Alla Magento CLI-kommandon måste köras av [filsystemets ägare](/help/configuration/cli/config-cli.md#prerequisites).

## Säkerhetskopieringskommandon {#tip-backup-command}

>[!TIP]
>
>Kommandot `support:backup` är _inte_ samma kodsäkerhetskopiering som utfördes av kommandot `setup:backup`. Kommandot `support:backup` är avsett att säkerhetskopiera kod för granskning av Adobe Commerce Support.

## B2B-patchar {#b2b-patches}

>[!NOTE]
>
>När säkerhetsuppdateringen har installerats måste Adobe Commerce B2B-handlare även uppdatera till den senaste kompatibla versionen av B2B-säkerhetsuppdateringen. Se [Versionsinformation för B2B](https://experienceleague.adobe.com/en/docs/commerce-admin/b2b/release-notes).

## Endast Adobe Commerce {#ee-only}

>[!NOTE]
>
>Den här funktionen är endast tillgänglig för Adobe Commerce-instanser.

## Delad DB är inaktuell {#deprecate-split-db}

>[!IMPORTANT]
>
>Den delade databasfunktionen var [inaktuell](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) i version 2.4.2 av Adobe Commerce. Se [Återgå från en delad databas till en enskild databas](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## Bakåtkompatibla ändringar {#bics}

>[!NOTE]
>
>Adobe Commerce-versioner kan innehålla ändringar som är inkompatibla bakåt (BIC). Om du vill granska ändringar som är inkompatibla bakåt läser du [BIC-referens](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). Viktiga bakåtkompatibla problem beskrivs i [BIC-markeringar](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/). Inte alla releaser innehåller viktiga BIC:er.

## Beta ansvarsfriskrivning {#beta}

>[!IMPORTANT]
>
>Beta-releaser kan innehålla defekter och tillhandahålls i befintligt skick utan någon garanti av något slag. Adobe har ingen skyldighet att upprätthålla, korrigera, uppdatera, ändra, modifiera eller på annat sätt ge support (från Adobe Support Services eller någon annan tjänst) för betaversioner. Kunderna bör vara försiktiga och inte på något sätt förlita sig på att betaversioner och/eller tillhörande dokumentation eller material fungerar eller fungerar korrekt. Därför är all användning av betaversioner helt och hållet på kundens egen risk.

## CVE-meddelande {#cve-notice}

>[!NOTE]
>
>Från och med version 2.3.2 kommer vi att tilldela och publicera indexerade CVE-nummer (Common Vulnerabilities and Exposure) med varje säkerhetsfel som rapporteras till oss av externa parter. Detta gör det enklare för användare att identifiera oadresserade säkerhetsluckor i driftsättningen. Du kan läsa mer om CVE-identifierare på [CVE](https://cve.mitre.org/).

## Annan versionsinformation {#other-release-info}

>[!NOTE]
>
>Även om koden för förbättringar och felkorrigeringar som beskrivs i den här versionsinformationen ingår i Adobe Commerce, kommer flera av dessa projekt (till exempel B2B, Page Builder och Progressive Web Applications (PWA) Studio) också att släppas oberoende av varandra. Felkorrigeringar för dessa projekt beskrivs i den separata, projektspecifika versionsinformation som finns i dokumentationen för varje projekt. Se [produktversionsöversikt](/help/release/release-notes/overview.md).

## PHP-processkontroll {#php-process-control}

Innan du kan köra indexerare i parallellt läge måste du aktivera stöd för processkontroll (`pcntl`) i PHP. Se [Installation](https://www.php.net/manual/en/pcntl.installation.php) i PHP-dokumentationen.
