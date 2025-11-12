---
source-git-commit: 1e3508e2e8e99d686dfa692415e2b4b41e8b80e8
workflow-type: tm+mt
source-wordcount: '726'
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

## Alpha ansvarsfriskrivning {#alpha}

>[!IMPORTANT]
>
>[Alpha](/help/release/versioning-policy.md#alpha-patch-release)-versioner kan vara ofullständiga och innehåller troligtvis fel. De tillhandahålls i befintligt skick utan någon garanti av något slag. Adobe har ingen skyldighet att upprätthålla, korrigera, uppdatera, ändra, modifiera eller på annat sätt ge support (via Adobe Support Services eller på annat sätt) för Alpha. Kunderna bör inte förlita sig på att Alpha-releaser eller tillhörande dokumentation eller material fungerar som de ska. Användningen av Alpha-releaser är helt på kundens egen risk.

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

## Egna patchar {#custom-patches-disclaimer}

>[!IMPORTANT]
>
>Adobe har inte stöd för att tillämpa officiella, Adobe-tillhandahållna patchar med den här metoden. Använd följande metod på egen risk. Använd [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"} om du vill tillämpa officiella korrigeringar. Utför alltid omfattande testning innan du distribuerar någon anpassad patch.

## Oktober 2025 backports för säkerhetsuppdatering {#oct-2025-backports}

<!--These fixes were backported to 2.4.8-pe, 2.4.7-p8, and 2.4.6-p13-->

* **Migrera från TinyMCE till Hugerte.org**

  På grund av att stödet för TinyMCE 5 och 6 har upphört och att licensieringen inte är kompatibel med TinyMCE 7 migreras den aktuella implementeringen av Adobe Commerce WYSIWYG-redigeraren från TinyMCE till den öppna [HugeRTE-redigeraren](https://hugerte.org/).

  Tack vare den här migreringen är Adobe Commerce fortfarande kompatibelt med öppen källkodslicensiering, undviker kända TinyMCE 6-problem och levererar en modern redigeringsupplevelse som stöds av både handlare och utvecklare.

* **Stöd för ActiveMQ Artemis STOMP-protokoll för Apache har lagts till**

  Stöd för ActiveMQ Artemis-meddelandehanterare med öppen källkod har lagts till via STOMP (Simple Text Oriented Messaging Protocol). Det är ett tillförlitligt och skalbart meddelandesystem som ger flexibilitet för STOMP-baserade integreringar. Se [Apache ActiveMQ Artemis](https://experienceleague.adobe.com/en/docs/commerce-operations/configuration-guide/message-queues/message-queue-framework#apache-activemq-artemis-stomp) i *Commerce Configuration Guide*.

## Utcheckningssidan kan inte läsa in static.min.js och mixins.min.js {#checkout-page-fails-to-load-static-min-js-and-mixins-min-js}

Efter de senaste ändringarna av CSP/SRI läses inte den utcheckade sidan in static.min.js och mixins.min.js när både JavaScript bundling och minification är aktiverade i produktionsläge. Därför körs inte RequireJS-mixins, och urcheckningen av blockeringsmallar kan inte lösas (till exempel `"Failed to load the 'Magento_Checkout/shipping' template requested by 'checkout.steps.shipping-step.shippingAddress'"`).

**Lösning**:

* Inaktivera JavaScript-paketering, eller
* Om JavaScript bundling är aktiverat inaktiverar du JavaScript minification.

>[!IMPORTANT]
>
>Inaktivera inte CSP eller ta bort SRI-skydd i produktionen. Bypass på plugin-nivå bör endast användas som en sista utväg för en snabbkorrigering och måste granskas av säkerhetsteamet.

**Programfix**:

En snabbkorrigering är tillgänglig. Se [Utcheckningen misslyckas när JS-miniatyr och paketering är aktiverat](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-27997) i kunskapsbasen för korrigeringsinformation.
