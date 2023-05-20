---
title: Gemensamma kommandon
description: Visa ett exempel på vanliga kommandon och användningsområden för Commerce CLI.
exl-id: d35a1dd9-10b3-4364-b6f4-b1e259a04e3d
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '248'
ht-degree: 0%

---

# Gemensamma kommandon

Nedan sammanfattas några av de tillgängliga kommandona.

**Visa en fullständig lista med kommandon**:

```bash
bin/magento list
```

Exempel på hjälpkommando:

```bash
bin/magento help <command>
```

```bash
bin/magento help cache:enable
```

Kommandona visas endast i sammanfattad form. Om du vill ha mer information om ett kommando klickar du på länken i kolumnen Kommando.

| Kommando | Beskrivning |
|--- |--- |
| [`magento cache:{enable/disable/clean/flush/status}`](../cli/manage-cache.md) | Hanterar cacheminnet |
| [`magento indexer:{status/show-mode/set-mode/reindex/info/reset/show-dimensions-mode/set-dimensions-mode}`](../cli/manage-indexers.md) | Hanterar indexerare |
| [`magento cron:run`](../cli/configure-cron-jobs.md) | Kör Commerce cron-jobb |
| [`magento setup:di:compile`](../cli/code-compiler.md) | Kompilerar alla obefintliga proxies och fabriker, och förkompilerar klassdefinitioner, arvsinformation och plugin-definitioner för en butik och webbplats. |
| [`magento info:dependencies:{show-modules/show-modules-circular/show-framework}`](../cli/dependency-reports.md) | Modulberoenden, cirkulära beroenden och Commerce Framework-beroenden. |
| [`magento i18n:{collect-phrases/pack/uninstall}`](../cli/localization.md) | Skapar en översättningsordlista eller ett översättningspaket |
| [`magento setup:static-content:deploy`](../cli/static-view-file-deployment.md) | Distribuerar statiska vyfiler |
| [`magento dev:source-theme:deploy`](../cli/create-symlinks.md) | Skapar CSS från LESS |
| [`magento dev:tests:run`](../cli/unit-tests.md) | Kör automatiska tester |
| [`magento dev:xml:convert`](../cli/convert-layout-files.md) | Uppdatera dina XML-layoutfiler så att de matchar den nya XSLT-formatmallen (Extensible Stylesheet Language Transformations) |
| [`magento setup:perf:generate-fixtures`](../cli/generate-data.md) | Generera data som ska användas för prestandatestning. |
| [`magento sampledata:install`](../../installation/sample-data/overview.md) | Installerar valfria exempeldata när du har installerat Commerce-programmet.<br><br>Mer information om exempeldata finns i [Valfria exempeldata](../../installation/sample-data/overview.md). |
| [`magento config:{set/sensitive:set/show/}`](../cli/set-configuration-values.md) | Hanterar serverdelskonfigurationer |
| [`magento admin:user:{create/unlock}`](../../installation/tutorials/admin.md#create-edit-or-unloack-an-administrator-account) | Skapar/redigerar/låser upp administratörsanvändare. |
| [`magento dev:template-hints:{enable/disable}`](https://developer.adobe.com/commerce/frontend-core/guide/themes/debug/) | Aktiverar/inaktiverar tips för utvecklarmallar. |

## Vanliga argument

Följande argument är gemensamma för alla kommandon. Dessa kommandon kan köras antingen före eller efter att Commerce-programmet har installerats:

| Lång version | Kort version | Betydelse |
|--- |--- |--- |
| `--help` | `-h` | Få hjälp för alla kommandon. Till exempel: `./magento help setup:install` eller `./magento help setup:config:set`. |
| `--quiet` | `-q` | Tyst läge; inga utdata. |
| `--no-interaction` | `-n` | Inga interaktiva frågor. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Detaljnivå. Till exempel: `--verbose=3` eller `-vvv` I visas felsökningsdetalj, vilket är den mest utförliga utdata. Standard är `--verbose=1` eller `-v`. |
| `--version` | `-V` | Visa den här programversionen |
| `--ansi` | n/a | Framtvinga ANSI-utdata |
| `--no-ansi` | n/a | Inaktivera ANSI-utdata |
