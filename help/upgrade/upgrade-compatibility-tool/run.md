---
title: Kör  [!DNL Upgrade Compatibility Tool]
description: Följ de här stegen för att köra  [!DNL Upgrade Compatibility Tool]  i ett kommandoradsgränssnitt för ditt Adobe Commerce-projekt.
exl-id: ea467a74-18eb-476b-96e2-23f4fc257d73
source-git-commit: bfb952d29bd3d7fc7147107216981e05202e44aa
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 0%

---

# Hämta [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

Om du vill komma igång med [!DNL Upgrade Compatibility Tool] i ett kommandoradsgränssnitt hämtar du det genom att köra följande kommando:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

Du kan behöva ge verktyget körbar behörighet med kommandot `chmod`:

```bash
chmod +x ./uct/bin/uct
```

## [!DNL Upgrade Compatibility Tool] i ett kommandoradsgränssnitt

[!DNL Upgrade Compatibility Tool] är ett verktyg som kontrollerar en Adobe Commerce-anpassad instans mot en viss version genom att analysera alla installerade moduler. Den returnerar en lista med allvarliga problem, fel och varningar som måste åtgärdas innan du uppgraderar till den senaste versionen av Adobe Commerce.

Se den här [videosjälvstudien](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) om du vill veta mer om [!DNL Upgrade Compatibility Tool].

Tillgängliga kommandon för [!DNL Upgrade Compatibility Tool] i ett kommandoradsgränssnitt:

| **Kommando** | **Beskrivning** |
|----------------|-----------------|
| `upgrade:check` | Det här kommandot kör [!DNL Upgrade Compatibility Tool] genom att analysera alla installerade moduler. |
| `dbschema:diff` | Det här kommandot visar alla skillnader i databasschemat mellan två angivna Adobe Commerce-versioner. |
| `core:code:changes` | Det här kommandot jämför din nuvarande Adobe Commerce-installation med en ren vaniljinstallation. |
| `refactor` | Det här kommandot åtgärdar automatiskt en reducerad uppsättning problem. |
| `graphql:compare` | Det här kommandot ger möjlighet att granska två GraphQL-slutpunkter och jämföra deras scheman. |
| `list` | Det här kommandot returnerar en lista med alla [!DNL Upgrade Compatibility Tool] tillgängliga kommandon. |
| `help` | Det här kommandot returnerar alla tillgängliga `help`-alternativ för [!DNL Upgrade Compatibility Tool]. Det här kommandot kan köras såväl som ett alternativ med de föregående kommandona. |

## Använd kommandot `upgrade:check`

Kommandot `upgrade:check` söker efter kärnkodändringar för den specifika Adobe Commerce-instansen och alla anpassade kodändringar som är installerade i den.

Kommandot `upgrade:check` är huvudkommandot för att köra verktyget:

```bash
bin/uct upgrade:check <dir>
```

Värdet `<dir>` är den katalog där din Adobe Commerce-instans finns.

Tillgängliga alternativ för kommandot `upgrade:check`:

| **Kommando** | **Tillgängliga alternativ** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help: Returnerar alla tillgängliga alternativ.</li><li>—current-version: Aktuell Adobe Commerce-version. Adobe Commerce-installationsversionen används om den utelämnas.</li><li>—min-issue-level: Du kan filtrera utgåvor efter den minsta utgåvnivån (standardvärdet är VARNING).</li><li>—ignore-current-version-compatibility-issues (eller -i): Om du inte vill ta med kritiska problem, fel och varningar från den aktuella versionen i rapporten.</li><li>—coming-version (eller -c): Ange en specifik Adobe Commerce-version som mål. Senaste tillgängliga kommer att användas om det utelämnas.</li></ul> |

Med [!DNL Upgrade Compatibility Tool] kan du köra kommandot `upgrade:check` med ett `--ignore-current-version-compatibility-issues`-alternativ. Använd det här alternativet om du bara vill få nya utgåvor som introduceras med uppdateringen från den aktuella versionen till målversionen i din [!DNL Upgrade Compatibility Tool]-rapport:

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> Detta gäller endast för PHP API-valideringar.

### Lägger till alternativet `--coming-version`

Du kan jämföra din nuvarande Adobe Commerce-installation med valfri Adobe Commerce-version `>=2.3` genom att använda alternativet `--coming-version`.

Du måste ange versionen som en parameter när du kör kommandot `upgrade:check`:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

Där `-c, --coming-version[=COMING-VERSION]` refererar till målversionen för Adobe Commerce.

Det finns vissa begränsningar när `--coming-version` körs:

- Den här parametern refererar till taggar som identifierar en viss version av Adobe Commerce.
- Det är ett krav att uttryckligen ange detta, att bara värdet av det inte fungerar.
- Ange taggversionen utan citattecken (varken enkla eller dubbla): ~~&#39;2.4.1-develop&#39;~~.
- Du bör INTE tillhandahålla äldre versioner än den som du har installerat, eller äldre än 2.3, som för närvarande är den äldsta som stöds.

## Använd kommandot `dbschema:diff`

Du kan hämta skillnaden mellan databasschemat för två Adobe Commerce-versioner.

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

Där argumenten är följande:

- `<current-version>`: alla Adobe Commerce-versioner för jämförelse.
- `<target-version>`: även alla Adobe Commerce-versioner för jämförelse.

Exempel på körning:

```bash
bin/uct dbschema:diff 2.4.3 2.4.3-p3

DB schema differences between versions 2.4.3 and 2.4.3-p3:

Table klarna_payments_quote constraint QUOTE_ID_KLARNA_PAYMENTS_QUOTE_QUOTE_ID_QUOTE_ENTITY_ID is present only in version 2.4.3-p3
Table klarna_payments_quote index KLARNA_PAYMENTS_QUOTE_SESSION_ID is present only in version 2.4.3-p3
Table customer_entity column session_cutoff is present only in version 2.4.3-p3
Table customer_visitor column session_id length value is different. 2.4.3: "64", 2.4.3-p3: "1"
Table customer_visitor column session_id comment value is different. 2.4.3: "Session ID", 2.4.3-p3: "Deprecated: Session ID value no longer used"
Table customer_visitor column created_at is present only in version 2.4.3-p3
Table oauth_consumer column secret length value is different. 2.4.3: "32", 2.4.3-p3: "128"
Table oauth_token column secret length value is different. 2.4.3: "32", 2.4.3-p3: "128"
Table admin_user_session column session_id nullable value is different. 2.4.3: "false", 2.4.3-p3: "true"
Table admin_user_session column session_id length value is different. 2.4.3: "128", 2.4.3-p3: "1"
Table admin_user_session column session_id comment value is different. 2.4.3: "Session ID value", 2.4.3-p3: "Deprecated: Session ID value no longer used"

Total detected differences between version 2.4.3 and 2.4.3-p3: 11
```

## Använd kommandot `core:code:changes`

Du kan jämföra din nuvarande Adobe Commerce-installation för att kontrollera om Adobe Commerce kärnkod har ändrats för att implementera en anpassning. Det här kommandot visar endast en lista över viktiga ändringar:

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Där argumenten är följande:

- `<dir>`: Adobe Commerce installationskatalog.
- `<vanilla dir>`: Installationskatalogen för Adobe Commerce vanilla.

Tillgängliga alternativ för kommandot `core:code:changes`:

| **Kommando** | **Tillgängliga alternativ** |
|----------------|-----------------|
| `core:code:changes` | `--help`: Returnerar alla tillgängliga `--help`-alternativ. |

>[!NOTE]
>
> Det är en god vana att hålla anpassad kod utanför kärnkoden. Mer information om bästa praxis för uppgradering finns i Adobe Commerce 2.4 [uppgraderingsguiden](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) .

### Vanilla-installation

En _vanilj_-installation är en ren installation av en angiven versionstagg eller gren för en specifik version.

Kommandot `bin/uct core:code:changes` kontrollerar om det finns en vanilj-instans i systemet. Om det här är första gången du använder en vanilj-installation uppmanas du av en interaktiv kommandoradsfråga att hämta vanilj-projektet från Adobe Commerce-databasen (`https://repo.magento.com/`).

Du kan köra ett [!DNL Upgrade Compatibility Tool]-kommando med alternativet `--vanilla-dir` för att ange Adobe Commerce vanilj-installationskatalogen.

Mer information finns i avsnittet [Distribuera vanilj-instans](https://developer.adobe.com/commerce/contributor/guides/code-contributions/#deploy-vanilla-magento-open-source-instance).

## Använd kommandot `refactor`

[!DNL Upgrade Compatibility Tool] kan automatiskt åtgärda en reducerad uppsättning problem:

- Funktioner som var tillåtna att användas utan att ett argument skickades, men med sådan användning har nu tagits bort.
- Användning av `$this` i Magento-mallar.
- Användning av PHP-nyckelordet `final` i privata metoder.

För det kör du kommandot `refactor`:

```bash
bin/uct refactor <dir>
```

Värdet `<dir>` är den katalog där din Adobe Commerce-instans finns.

Tillgängliga alternativ för kommandot `refactor`:

| **Kommando** | **Tillgängliga alternativ** |
|----------------|-----------------|
| `refactor` | `--help`: Returnerar alla tillgängliga `--help`-alternativ. |

## Använd kommandot `graphql:compare`

Det här kommandot ger [!DNL Upgrade Compatibility Tool] möjlighet att granska två GraphQL-slutpunkter och jämföra deras scheman för att hitta brytningar och farliga ändringar mellan dem:

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Där argumenten är följande:

- `<schema1>`: Slutpunkts-URL för den befintliga installationen.
- `<schema2>`: Slutpunkts-URL för vanilj-installationen.

Tillgängliga alternativ för kommandot `graphql:compare`:

| **Kommando** | **Tillgängliga alternativ** |
|----------------|-----------------|
| `graphql:compare` | `--help`: Returnerar alla tillgängliga `--help`-alternativ. |

## Använd kommandot `list`

Om du vill returnera en lista över de [!DNL Upgrade Compatibility Tool] tillgängliga kommandona kör du:

```bash
bin/uct list
```

## Använd kommandot `help`

Om du vill visa allmänna alternativ och hjälp för kommandot [!DNL Upgrade Compatibility Tool] kör du:

```bash
bin/uct --help
```

Den returnerar en lista med alla tillgängliga `help`-alternativ för [!DNL Upgrade Compatibility Tool] i ett kommandoradsgränssnitt:

```
- --raw             To output raw command list
- --format=FORMAT   The output format (txt, xml, json, or md) [default: "txt"]
- --short           To skip describing commands' arguments
- -h, --help            Display help for the given command. When no command is given display help for the list command
- -q, --quiet           Do not output any message
- -V, --version         Display this application version
- --ansi|--no-ansi  Force (or disable --no-ansi) ANSI output
- -n, --no-interaction  Do not ask any interactive question
- -v|vv|vvv, --verbose  Increase the verbosity of messages: 1 for normal output, 2 for more verbose output and 3 for debug
```

Det går att köra `--help` som ett alternativ när ett specifikt kommando körs. Det returnerar `--help` alternativ för det angivna kommandot.

Exempel på kommandot `upgrade:check` med alternativet `--help`:

```bash
bin/uct upgrade:check --help
```

Detta returnerar specifika alternativ som kan köras för kommandot `upgrade:check`:

```
- -a, --current-version[=CURRENT-VERSION]: Current Adobe Commerce version, version of the Adobe Commerce installation will be used if omitted.
- -c, --coming-version[=COMING-VERSION]: Target Adobe Commerce version, latest released version of Adobe Commerce will be used if omitted. Provides a list of all available Adobe Commerce versions.
- --json-output-path[=JSON-OUTPUT-PATH]: Path of the file where the output will be exported in json format.
- --html-output-path[=HTML-OUTPUT-PATH]: Path of the file where the output will be exported in HTML format.
- --min-issue-level[=MIN-ISSUE-LEVEL]            Minimal issue level you want to see in the report (warning, error or critical). [default: "warning"]
- -i, --ignore-current-version-compatibility-issues  Ignore common issues for current and coming version
- --context=CONTEXT: Execution context. This option is for integration purposes and does not affect the execution result.
- -h, --help: Display help for that specific command. If no command is provided, `list` command is the default result.
- -q, --quiet: Do not output any messages while executing the command.
- -v, --version: Display application version.
- --ansi, --no-ansi: Enable ANSI output.
- -n, --no-interaction: Do not ask any interactive question while executing the command.
- -v, --vv, --vvv, --verbose: Increase verbosity of output communications. 1 for normal output, 2 for verbose output, and 3 for DEBUG output.
```

## Följ Adobe Commerce metodtips

- Undvik två moduler med samma namn.
- Följ Adobe Commerce [kodningsstandarder](https://developer.adobe.com/commerce/php/coding-standards/).
- Adobe Commerce 2.4 [Uppgraderingsguide](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) bästa praxis.
- Kör [!DNL Upgrade Compatibility Tool] från [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) för [Adobe Commerce i molninfrastrukturprojekt](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank}.

## Optimera resultatet

[!DNL Upgrade Compatibility Tool] tillhandahåller en rapport som innehåller resultat med alla problem som identifieras i ditt projekt som standard. Du kan optimera resultaten för att fokusera på de problem som du måste åtgärda för att slutföra uppgraderingen:

- Använd alternativet `--ignore-current-version-compatibility-issues` om du bara vill få nya utgåvor som introduceras med uppdateringen från den aktuella versionen till målversionen i din [!DNL Upgrade Compatibility Tool]-rapport.
- Om du lägger till alternativet `--min-issue-level` kan du med den här inställningen ange lägsta problemnivå, så att du bara kan prioritera de viktigaste problemen med uppgraderingen.
- [!DNL Upgrade Compatibility Tool] kräver minst 2 GB RAM för att kunna köras. Den här inställningen rekommenderas för att undvika problem på grund av en låg minnesbegränsning. [!DNL Upgrade Compatibility Tool] visar en fråga om du kör kommandot `upgrade:check` med låg `memory_limit`-inställning.
