---
source-git-commit: 2c12c6ea6e7b6ffeb07bbda17ded34e39de6656a
workflow-type: tm+mt
source-wordcount: '97'
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
