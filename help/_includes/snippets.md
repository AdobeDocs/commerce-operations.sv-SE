---
source-git-commit: 74cb55f4552bc1b2dace37d9a6f7e68939d1c262
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---
# Fragment

## Endast handel {#commerce-only}

>[!NOTE]
>
>The [!DNL Upgrade Compatibility Tool] finns endast för Adobe Commerce-instanser.

<!-- Configuration guide snippets -->

## Ägare till filsystem {#file-system-owner}

>[!WARNING]
>
>Alla Magento CLI-kommandon måste köras av [ägare av filsystem](/help/configuration/cli/config-cli.md#prerequisites).

## Säkerhetskopieringskommandon {#tip-backup-command}

>[!TIP]
>
>The `support:backup` kommandot är _not_ samma kodsäkerhetskopiering som utförs av `setup:backup` -kommando. The `support:backup` ska säkerhetskopiera kod för granskning av Adobe Commerce Support.

## Endast Adobe Commerce {#ee-only}

>[!NOTE]
>
>Den här funktionen är endast tillgänglig för Adobe Commerce-instanser.

## Delad DB är inaktuell {#deprecate-split-db}

>[!IMPORTANT]
>
>Den delade databasfunktionen var [föråldrad](https://community.magento.com/t5/Magento-DevBlog/Deprecation-of-Split-Database-in-Magento-Commerce/ba-p/465187?_ga=2.128934671.2024864496.1657558157-1596100530.1657558157) i version 2.4.2 av Adobe Commerce. Se [Återgå från en delad databas till en enda databas](/help/configuration/storage/revert-split-database.md).

<!-- End of Configuration guide snippets -->

## Bakåtkompatibla ändringar {#bics}

>[!NOTE]
>
>Adobe Commerce och Magento Open Source kan innehålla ändringar som är inkompatibla bakåt (BIC). Om du vill granska ändringar som är inkompatibla bakåt kan du läsa [BIC-referens](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/). Viktiga bakåtkompatibla problem beskrivs i [BIC i korthet](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/). Inte alla releaser innehåller viktiga BIC:er.

## CVE-meddelande {#cve-notice}

>[!NOTE]
>
>Från och med version 2.3.2 kommer vi att tilldela och publicera indexerade CVE-nummer (Common Vulnerabilities and Exposure) med varje säkerhetsfel som rapporteras till oss av externa parter. Detta gör det enklare för användare att identifiera oadresserade säkerhetsluckor i driftsättningen. Du kan läsa mer om CVE-identifierare på [CVE](https://cve.mitre.org/).
