---
title: Kodkompilator
description: Lär dig hur du kör kodkompilatorn från kommandoraden.
exl-id: 08dbf808-ea79-4956-a0bc-f464bb80eee7
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# Kodkompilator

{{file-system-owner}}

Kodkompileringen innehåller följande (ingen särskild ordning):

- Programkodgenerering (fabriker, proxies)
- Aggregering för områdeskonfiguration (optimerade beroendeinjektionskonfigurationer per område)
- Generering av spärrar (optimerad kodgenerering av spärrar)
- Generering av cacheminne för spärr
- Databasgenerering av kod (genererad kod för API:er)
- Generering av servicedataattribut (genererade tilläggsklasser för dataobjekt)

Du hittar klasser för kodkompilering i namnutrymmet [\Magento\Setup\Module\Di\App\Task\Operation][operation].

Så här kör du single-tenant-kompilatorn:

```bash
bin/magento setup:di:compile
```

```
Generated code and dependency injection configuration successfully.
```

Så här kompilerar du kod innan du installerar Commerce-programmet:

I vissa fall kanske du vill kompilera koden innan du installerar Commerce-programmet.

1. Aktivera modulerna.

   ```bash
   bin/magento module:enable --all [-c|--clear-static-content]
   ```

   Använd alternativet `[-c|--clear-static-content]` för att rensa statiskt innehåll. Detta är nödvändigt om du tidigare aktiverat eller inaktiverat moduler och du måste rensa det statiska innehåll som tidigare genererats för dem.

   Se [Aktivera moduler](../../installation/tutorials/manage-modules.md).

1. Kompilera koden.

   ```bash
   bin/magento setup:di:compile
   ```

   ```
   Generated code and dependency injection configuration successfully.
   ```

Information om hur du kompilerar kod utan databas finns i [Distribuera statiska vyfiler utan att installera Magento](../cli/static-view-file-deployment.md).

<!-- link definitions -->

[operation]: https://github.com/magento/magento2/blob/2.4/setup/src/Magento/Setup/Module/Di/App/Task/Operation
