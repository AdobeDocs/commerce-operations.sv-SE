---
title: Kodkompilator
description: Lär dig hur du kör kodkompilatorn från kommandoraden.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---


# Kodkompilator

{{file-system-owner}}

Kodkompileringen innehåller följande (ingen särskild ordning):

- Programkodgenerering (fabriker, proxies)
- Aggregering för områdeskonfiguration (optimerad) [beroendeinjektion](https://glossary.magento.com/dependency-injection) konfigurationer per område)
- Generering av spärrar (optimerad kodgenerering av spärrar)
- Generering av cacheminne för spärr
- Databasgenerering av kod (genererad kod för API:er)
- Generering av servicedataattribut (genererad) [extension](https://glossary.magento.com/extension) klasser för dataobjekt)

Du kan hitta klasser för kodkompilering i [\Magento\Setup\Module\Di\App\Task\Operation][operation] namnutrymme.

Så här kör du single-tenant-kompilatorn:

```bash
bin/magento setup:di:compile
```

```terminal
Generated code and dependency injection configuration successfully.
```

Så här kompilerar du kod innan du installerar Commerce-programmet:

I vissa fall kanske du vill kompilera kod innan du installerar Commerce-programmet.

1. Aktivera modulerna.

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   Använd `[-c|--clear-static-content]` alternativ för att rensa [statiskt innehåll](https://glossary.magento.com/static-content). Detta är nödvändigt om du tidigare aktiverat eller inaktiverat moduler och du måste rensa det statiska innehåll som tidigare genererats för dem.

   Se [Aktivera moduler](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-enable.html).

1. Kompilera koden.

   ```bash
   bin/magento setup:di:compile
   ```

   ```terminal
   Generated code and dependency injection configuration successfully.
   ```

Information om hur du kompilerar kod utan databas finns i [Distribuera statiska vyfiler utan att installera Magento](../cli/static-view-file-deployment.md).

<!-- link definitions -->

[operation]: https://github.com/magento/magento2/blob/2.4/setup/src/Magento/Setup/Module/Di/App/Task/Operation
