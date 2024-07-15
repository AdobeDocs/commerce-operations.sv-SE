---
title: Ange åtgärdsläge
description: Läs om hur du ställer in Adobe Commerce driftslägen.
exl-id: 62d183fa-d4ff-441d-b8bd-64ef5ae10978
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---

# Ange åtgärdsläge

{{file-system-owner}}

För att förbättra säkerheten och användarvänligheten har vi lagt till ett kommando som växlar [programlägen](../bootstrap/application-modes.md) från utvecklare till produktion och vice versa.

Produktionsläget har bättre prestanda eftersom statiska vyfiler fylls i i katalogen `pub/static` och på grund av kodkompilering.

>[!INFO]
>
>I version 2.0.6 och senare ställer Commerce inte uttryckligen in fil- eller katalogbehörigheter när du växlar mellan standardläge, utvecklings- och produktionsläge. Till skillnad från andra lägen ställs utvecklare och produktionslägen in i filen `env.php`. Adobe Commerce i molninfrastruktur har endast stöd för produktions- och underhållslägen.
>
>Se [Commerce ägarskap och behörigheter i utveckling och produktion](../deployment/file-system-permissions.md).

När du byter till utvecklare eller produktionsläge tar vi bort innehållet i följande kataloger:

```terminal
var/cache
generated/metadata
generated/code
var/view_preprocessed
pub/static
```

Undantag:

- `.htaccess` filer tas inte bort
- `pub/static` innehåller en fil som anger version av statiskt innehåll. Den här filen tas inte bort

>[!INFO]
>
>Som standard använder Commerce katalogerna `var` för att lagra cache, loggar och kompilerad kod. Du kan anpassa den här katalogen, men i den här guiden antas den vara `var`.

## Visa det aktuella läget

Det enklaste sättet att göra det är att köra det här kommandot som [filsystemsägare](../../installation/prerequisites/file-system/overview.md). Om du har delat värdskap är detta den användare som din leverantör ger dig att logga in på servern. Om du har en privat server är det vanligtvis ett lokalt användarkonto på Commerce-servern.

Kommandoanvändning:

```bash
bin/magento deploy:mode:show
```

Ett meddelande som liknar följande visas:

```terminal
Current application mode: {mode}. (Note: Environment variables may override this value.)
```

där:

- **`{mode}`** kan vara antingen `default`, `developer` eller `production`

## Ändra lägen

Kommandoanvändning:

```bash
bin/magento deploy:mode:set {mode} [-s|--skip-compilation]
```

där:

- **`{mode}`** krävs; det kan vara antingen `developer` eller `production`

- **`--skip-compilation`** är en valfri parameter som du kan använda för att hoppa över [kodkompilering](../cli/code-compiler.md) när du ändrar till produktionsläge.

Här följer några exempel.

### Ändra till produktionsläge

```bash
bin/magento deploy:mode:set production
```

Meddelanden som liknar följande:

```terminal
Enabled maintenance mode
Requested languages: en_US
=== frontend -> Magento/luma -> en_US ===
... more ...
Successful: 1884 files; errors: 0
---

=== frontend -> Magento/blank -> en_US ===
... more ...
Successful: 1828 files; errors: 0
---

=== adminhtml -> Magento/backend -> en_US ===
... more ...
---

=== Minify templates ===
... more ...
Successful: 897 files modified
---

New version of deployed files: 1440461332
Static content deployment complete
Gathering css/styles-m.less sources.
Successfully processed LESS and/or Sass files
CSS deployment complete
Generated classes:
      Magento\Sales\Api\Data\CreditmemoCommentInterfacePersistor
      Magento\Sales\Api\Data\CreditmemoCommentInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoCommentSearchResultInterfaceFactory
      Magento\Sales\Api\Data\CreditmemoComment\Repository
      Magento\Sales\Api\Data\CreditmemoItemInterfacePersistor
      ... more ...
Compilation complete
Disabled maintenance mode
Enabled production mode.
```

### Växla till utvecklarläge

När du byter från produktion till utvecklarläge bör du rensa genererade klasser och objekthanterarentiteter som proxies för att undvika oväntade fel. När du har gjort det kan du ändra läge. Gör så här:

1. Om du ändrar från produktionsläge till utvecklarläge tar du bort innehållet i katalogerna `generated/code` och `generated/metadata`:

   ```bash
   rm -rf <magento_root>/generated/metadata/* <magento_root>/generated/code/*
   ```

1. Ange läge:

   ```bash
   bin/magento deploy:mode:set developer
   ```

   Följande meddelande visas:

   ```terminal
   Enabled developer mode.
   ```

### Ändra till standardläge

```bash
bin/magento deploy:mode:set default
```

Följande meddelande visas:

```terminal
Enabled default mode.
```

### Kör CLI-kommandon var som helst

[Kör CLI-kommandon var som helst](../cli/config-cli.md#config-install-cli-first).

Om du inte har lagt till `<Commerce-install-directory>/bin` i systemet `PATH` kan du förvänta dig ett fel när du kör kommandot själv.
