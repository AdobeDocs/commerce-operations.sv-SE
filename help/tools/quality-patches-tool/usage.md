---
title: Användning
description: Lär dig använda [!DNL Quality Patches Tool].
exl-id: f9ad37e9-2d0f-4bc8-a98b-6d60b6f56d42
feature: Configuration, Install
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '910'
ht-degree: 0%

---

# Användning

The [[!DNL Quality Patches Tool]](https://github.com/magento/quality-patches) levererar individuella plåster som utvecklats av Adobe och Magento Open Source-communityn. Med den kan du tillämpa, återställa och visa allmän information om alla enskilda korrigeringsfiler som är tillgängliga för den installerade versionen av Adobe Commerce eller Magento Open Source. Du kan använda korrigeringsfiler i Adobe Commerce- och Magento Open Source-projekt oavsett vem som har utvecklat korrigeringsfilen. Du kan till exempel använda en korrigering som utvecklats av communityn på Adobe Commerce-projekt.


Titta på detta [teknisk video](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/tools/quality-patch-tool.html?lang=en) och lär dig hur du använder verktyget för kvalitetskorrigeringar för Adobe Commerce och Magento Open Source.

>[!INFO]
>
>Se [Tillämpa enskilda patchar](#apply-individual-patches) för instruktioner om hur du använder korrigeringsfiler i dina Adobe Commerce- eller Magento Open Source-projekt. Se [[!DNL Quality Patches Tool]: Sök efter patchar](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) för att se en fullständig lista över de släppta plåstren.

>[!WARNING]
>
>Det rekommenderas inte att du använder [!DNL Quality Patches Tool] för att använda ett stort antal patchar eftersom det gör koden mer komplex och gör det svårare att uppgradera till en ny version.

## Installera

>[!INFO]
>
>Om det inte redan är installerat måste du installera [[!DNL Git]](https://github.com/git-guides/install-git) eller [Lappa](https://man7.org/linux/man-pages/man1/patch.1.html) före installation av [!DNL Quality Patches Tool]. Lägg till `magento/quality-patches` Disposition-paket till `composer.json` fil:

```bash
composer require magento/quality-patches
```

## Visa enskilda patchar

Så här visar du en lista över enskilda korrigeringsfiler som är tillgängliga för din version av Adobe Commerce eller Magento Open Source:

```bash
./vendor/bin/magento-patches status
```

Utdata ser ut ungefär så här:

| ID | Titel | Typ | Status | Information |
|--- |--- |--- |--- |--- |
| MAGECLOUD-5069 | FPC inaktiveras under distributioner | Valfritt | Ej tillämpat | Komponenter som påverkas:<br> - magento/module-page-cache |
| MCLOUD-5650 | Håll distributionskonfigurationen efter läsning från fil | Valfritt | Ej tillämpat | Komponenter som påverkas:<br> - magento/framework |
| MCLOUD-5684 | Sidnumreringen fungerar inte - product_list_limit=all | Valfritt | Ej tillämpat | Komponenter som påverkas: - magento/module-elasticsearch |
| MCLOUD-5837 | Åtgärda problem med belastningsutjämnare | Föråldrat | Används | Rekommenderad ersättning: MC-1 <br> Komponenter som påverkas: - magento/framework |
| BUNDLE-2554 | Ange fel för betalningsinformation | Valfritt | Ej tillämpat | Komponenter som påverkas: <br>- amzn/amazon-betal-module |
| MC-1 | Åtgärdar problem 1 | Valfritt | Används | Komponenter som påverkas: <br> - magento/module-cms |
| MC-2 | Åtgärdsproblem 2 | Valfritt | Ej tillämpat | Komponenter som påverkas: <br> - magento/module-cms |
| MC-3 | Åtgärdar problem 3 | Valfritt | Ej tillämpat | Nödvändiga patchar:<br> - MC-2 <br>Komponenter som påverkas: <br>- magento/module-cms |
| MC-3-V2 | Uppdaterad korrigering för utgåva 3, ersätter patchen MC-3 | Valfritt | Ej tillämpligt | Komponenter som påverkas:  <br>- magento/module-cms |

Adobe Commerce 2.3.5

Statustabellen innehåller:

- **Typ**:
   - `Optional` — Alla patchar från [!DNL Quality Patches Tool] och [Commerce on Cloud Infrastructure Guide > Apply patches](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) är valfritt för installationer i Adobe Commerce och Magento Open Source.
   - `Deprecated` — Adobe har ersatt det enskilda plåstret. Om du har använt korrigeringen rekommenderar vi att du återställer den. Återställningsåtgärden tar även bort korrigeringen från statustabellen.

- **Status**:
   - `Applied` — Korrigeringen har applicerats.
   - `Not applied` — Korrigeringen har inte installerats.
   - `N/A` — Det går inte att definiera status för korrigeringen på grund av konflikter.

- **Information**:
   - `Affected components` — En lista över de moduler som påverkas.
   - `Required patches` — En lista över korrigeringsfiler som måste tillämpas för en angiven korrigeringsfil för att den ska fungera korrekt (beroenden).
   - `Recommended replacement` — Den korrigering som rekommenderas som ersättning för en borttagen patch.

>[!INFO]
>
>När du har uppgraderat till en ny version av Adobe Commerce eller Magento Open Source måste du tillämpa korrigeringarna igen om de inte ingår i den nya versionen. Se [Tillämpa patchar igen efter en uppgradering](#re-apply-patches-after-an-upgrade).

## Tillämpa enskilda patchar {#apply-individual-patches}

>[!WARNING]
>
>Det är bäst att testa alla korrigeringsfiler i en staging- eller utvecklingsmiljö innan de distribueras till produktionen. Vi rekommenderar även att du säkerhetskopierar dina data innan du använder en patch. Se [Säkerhetskopiera och återställa filsystemet, mediet och databasen](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html).

Om du vill använda en enda korrigering kör du följande kommando där `MAGETWO-XXXX` är det korrigerings-ID som anges i statustabellen:

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX
```

Du kan också använda flera korrigeringsfiler samtidigt genom att separera varje ytterligare korrigerings-ID med ett mellanslag:

```bash
./vendor/bin/magento-patches apply MAGETWO-XXXX MAGETWO-YYYY
```

Du måste rensa cacheminnet när du har tillämpat korrigeringar för att se ändringarna i Adobe Commerce-programmet:

```bash
./bin/magento cache:clean
```

>[!INFO]
>
>Överväg att ha en lista över tillämpade korrigeringsfiler på en separat plats. Du kan behöva installera om vissa av dem efter att du uppgraderat till en ny version av Adobe Commerce eller Magento Open Source. Se [Tillämpa patchar igen efter en uppgradering](#re-apply-patches-after-an-upgrade).

## Återställ enskilda korrigeringsfiler

>[!WARNING]
>
>Det är bäst att testa alla korrigeringsfiler i en staging- eller utvecklingsmiljö innan de distribueras till produktionen. Vi rekommenderar även att du säkerhetskopierar dina data innan du använder en patch. Se [Säkerhetskopiera och återställa filsystemet, mediet och databasen](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/tutorials/backup.html).

Om du vill återställa en enskild korrigering kör du följande kommando där `MAGETWO-XXXX` är det korrigerings-ID som anges i statustabellen:

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX
```

Du kan också återställa flera korrigeringsfiler samtidigt genom att separera varje ytterligare korrigerings-ID med ett mellanslag:

```bash
./vendor/bin/magento-patches revert MAGETWO-XXXX MAGETWO-YYYY
```

Så här återställer du alla tillämpade patchar:

```bash
./vendor/bin/magento-patches revert --all
```

Du måste rensa cachen efter att du har återställt korrigeringsfiler för att se ändringarna i Adobe Commerce-programmet:

```bash
./bin/magento cache:clean
```

## Få uppdateringar

Adobe Commerce släpper regelbundet nya patchar. Du måste uppdatera [!DNL Quality Patches Tool] för att få nya individuella patchar:

```bash
composer update magento/quality-patches
```

Visa tillagda korrigeringar:

>[!TIP]
>
>Nya tilläggspatchar visas längst ned i tabellen.

```bash
./vendor/bin/magento-patches status
```

## Tillämpa patchar igen efter en uppgradering {#re-apply-patches-after-an-upgrade}

När du uppgraderar till en ny version av Adobe Commerce eller Magento Open Source måste du installera om patchar om de inte ingår i den nya versionen.

Så här återanvänder du patchar:

1. Uppdatera [!DNL Quality Patches Tool]:

   ```bash
   composer update magento/quality-patches.
   ```

1. Öppna listan med tidigare använda korrigeringar, som rekommenderas i [Tillämpa enskilda patchar](#apply-individual-patches).

1. Tillämpa patcharna:

   ```bash
   ./vendor/bin/magento-patches apply MAGETWO-XXXX
   ```

   Det bästa sättet är att lägga på patchar en åt gången.

1. Rensa cachen:

   ```bash
   ./bin/magento cache:clean
   ```

   >[!INFO]
   >
   >När du kör `status` de korrigeringar som ingick i den nya versionen inte längre visas i tabellen med tillgängliga korrigeringar.

## Loggning

The [!DNL Quality Patches Tool] loggar alla åtgärder i `<Magento_root>/var/log/patch.log` -fil.
