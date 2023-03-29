---
title: "Kör [!DNL Upgrade Compatibility Tool]"
description: Följ de här stegen för att köra [!DNL Upgrade Compatibility Tool] i ett kommandoradsgränssnitt för ditt Adobe Commerce-projekt.
source-git-commit: 653d755023f96c0a6acc312f74fd4a0292f13a73
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Ladda ned [!DNL Upgrade Compatibility Tool]

{{commerce-only}}

Så här kommer du igång med [!DNL Upgrade Compatibility Tool] i ett kommandoradsgränssnitt hämtar du det genom att köra följande kommando:

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

Du kan behöva ge verktyget körbara behörigheter med `chmod` kommando:

```bash
chmod +x ./uct/bin/uct
```

## The [!DNL Upgrade Compatibility Tool] i ett kommandoradsgränssnitt

The [!DNL Upgrade Compatibility Tool] är ett verktyg som kontrollerar en Adobe Commerce-anpassad instans mot en viss version genom att analysera alla moduler som är installerade i den. Den returnerar en lista med allvarliga problem, fel och varningar som måste åtgärdas innan du uppgraderar till den senaste versionen av Adobe Commerce.

Se det här [videosjälvstudiekurs](https://experienceleague.adobe.com/docs/commerce-learn/tutorials/upgrade/upgrade-compatibility-tool-overview.html?lang=en) (06:02) om du vill veta mer om [!DNL Upgrade Compatibility Tool].

Tillgängliga kommandon för [!DNL Upgrade Compatibility Tool] i ett kommandoradsgränssnitt:

| **Kommando** | **Beskrivning** |
|----------------|-----------------|
| `upgrade:check` | Det här kommandot kör [!DNL Upgrade Compatibility Tool] genom att analysera alla installerade moduler. |
| `dbschema:diff` | Det här kommandot visar alla skillnader i databasschemat mellan två angivna Adobe Commerce-versioner. |
| `core:code:changes` | Det här kommandot jämför din nuvarande Adobe Commerce-installation med en ren vaniljinstallation. |
| `refactor` | Det här kommandot åtgärdar automatiskt en reducerad uppsättning problem. |
| `graphql:compare` | Det här kommandot ger möjlighet att granska två GraphQL-slutpunkter och jämföra deras scheman. |
| `list` | Det här kommandot returnerar en lista med alla [!DNL Upgrade Compatibility Tool] tillgängliga kommandon. |
| `help` | Det här kommandot returnerar alla tillgängliga `help`för [!DNL Upgrade Compatibility Tool]. Det här kommandot kan köras såväl som ett alternativ med de föregående kommandona. |

## Använd `upgrade:check` kommando

The `upgrade:check` -kommandot kontrollerar om det finns några ändringar i kärnkoden för den specifika Adobe Commerce-instansen och alla anpassade kodändringar som har installerats i den.

The `upgrade:check` är det huvudsakliga kommandot som kör verktyget:

```bash
bin/uct upgrade:check <dir>
```

Plats `<dir>` värde är den katalog där din Adobe Commerce-instans finns.

Tillgängliga alternativ för `upgrade:check` kommando:

| **Kommando** | **Tillgängliga alternativ** |
|----------------|-----------------|
| `upgrade:check` | <ul><li>—help: Returnerar alla tillgängliga alternativ.</li><li>—current-version: Aktuell Adobe Commerce-version. Den här parametern är obligatorisk och måste alltid användas.</li><li>—min-issue-level: Du kan filtrera utgåvor efter miniminivån för utgåvor (standardvärdet är VARNING).</li><li>—ignore-current-version-compatibility-issues (eller -i): Om du inte vill inkludera allvarliga problem, fel och varningar från den aktuella versionen i rapporten.</li><li>—coming-version (or -c): Ange en specifik Adobe Commerce-version. Senaste tillgängliga kommer att användas om det utelämnas.</li></ul> |

The [!DNL Upgrade Compatibility Tool] låter dig köra `upgrade:check` kommando med `--ignore-current-version-compatibility-issues` alternativ. Använd det här alternativet om du bara vill få nya utgåvor som introduceras med uppdateringen från den aktuella versionen till målversionen i din [!DNL Upgrade Compatibility Tool] rapport:

```bash
bin/uct upgrade:check --ignore-current-version-compatibility-issues <dir>
```

>[!NOTE]
>
> Detta gäller endast för PHP API-valideringar.

### Lägga till `--coming-version` option

Du kan jämföra din nuvarande Adobe Commerce-installation med valfri Adobe Commerce-version `>=2.3` genom att använda `--coming-version` alternativ.

Du måste ange versionen som en parameter när du kör `upgrade:check` kommando:

```bash
bin/uct upgrade:check <dir> -c 2.4.3
```

Plats `-c, --coming-version[=COMING-VERSION]` avser målversionen av Adobe Commerce.

Det finns vissa begränsningar när du kör `--coming-version`:

- Den här parametern refererar till taggar som identifierar en viss version av Adobe Commerce.
- Det är ett krav att uttryckligen ange detta. om bara värdet inte fungerar.
- Ange taggversionen utan citattecken (varken enkla eller dubbla): ~~&quot;2.4.1-develop&quot;~~.
- Du bör INTE tillhandahålla äldre versioner än den som du har installerat, eller äldre än 2.3, som för närvarande är den äldsta som stöds.

## Använd `dbschema:diff` kommando

Du kan hämta skillnaden mellan databasschemat för två Adobe Commerce-versioner.

```bash
bin/uct dbschema:diff <current-version> <target-version>
```

Där argumenten är följande:

- `<current-version>`: alla Adobe Commerce-versioner som kan jämföras.
- `<target-version>`: också alla Adobe Commerce-versioner som kan jämföras.

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

## Använd `core:code:changes` kommando

Du kan jämföra din nuvarande Adobe Commerce-installation för att kontrollera om Adobe Commerce kärnkod har ändrats för att implementera en anpassning. Det här kommandot visar endast en lista över viktiga ändringar:

```bash
bin/uct core:code:changes <dir> <vanilla dir>
```

Där argumenten är följande:

- `<dir>`: Adobe Commerce installationskatalog.
- `<vanilla dir>`: Installationskatalogen för Adobe Commerce vanilla.

Tillgängliga alternativ för `core:code:changes` kommando:

| **Kommando** | **Tillgängliga alternativ** |
|----------------|-----------------|
| `core:code:changes` | `--help`: Returnerar alla tillgängliga `--help` alternativ. |

>[!NOTE]
>
> Det är en god vana att hålla anpassad kod utanför kärnkoden. Se Adobe Commerce 2.4 [uppgraderingsguide](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) om du vill ha mer information om bästa praxis för uppgradering.

### Vanilla-installation

A _vanilj_ installation är en ren installation av en angiven versionstagg eller gren för en specifik version.

The `bin/uct core:code:changes` -kommandot kontrollerar om det finns en vanilj-instans i systemet. Om det här är första gången du använder en vanilj-installation uppmanas du av en interaktiv kommandoradsfråga att hämta vanilj-projektet från Adobe Commerce-databasen (`https://repo.magento.com/`).

Du kan köra en [!DNL Upgrade Compatibility Tool] med `--vanilla-dir` om du vill ange installationskatalogen för Adobe Commerce vanilla.

Se [Distribuera vanilj-instans](https://developer.adobe.com/commerce/contributor/guides/code-contributions/#deploy-vanilla-magento-open-source-instance) för mer information.

## Använd `refactor` kommando

The [!DNL Upgrade Compatibility Tool] har möjlighet att automatiskt åtgärda en reducerad uppsättning problem:

- Funktioner som var tillåtna att användas utan att ett argument skickades, men med sådan användning har nu tagits bort.
- Användning av `$this` i Magento-mallar.
- Användning av PHP-nyckelord `final` i privata metoder.

För det kör du `refactor` kommando:

```bash
bin/uct refactor <dir>
```

Plats `<dir>` värde är den katalog där din Adobe Commerce-instans finns.

Tillgängliga alternativ för `refactor` kommando:

| **Kommando** | **Tillgängliga alternativ** |
|----------------|-----------------|
| `refactor` | `--help`: Returnerar alla tillgängliga `--help` alternativ. |

## Använd `graphql:compare` kommando

Det här kommandot ger möjlighet att [!DNL Upgrade Compatibility Tool] för att presentera två GraphQL-slutpunkter och jämföra sina scheman för att hitta nya och farliga förändringar mellan dem:

```bash
bin/uct graphql:compare <schema1> <schema2>
```

Där argumenten är följande:

- `<schema1>`: Slutpunkts-URL för den befintliga installationen.
- `<schema2>`: Slutpunkts-URL för vanilj-installationen.

Tillgängliga alternativ för `graphql:compare` kommando:

| **Kommando** | **Tillgängliga alternativ** |
|----------------|-----------------|
| `graphql:compare` | `--help`: Returnerar alla tillgängliga `--help` alternativ. |

## Använd `list` kommando

Returnera en lista med [!DNL Upgrade Compatibility Tool] tillgängliga kommandon, kör:

```bash
bin/uct list
```

## Använd `help` kommando

Om du vill se [!DNL Upgrade Compatibility Tool] allmänna kommandoalternativ och hjälp, kör:

```bash
bin/uct --help
```

Den returnerar en lista med alla tillgängliga `help` för [!DNL Upgrade Compatibility Tool] i ett kommandoradsgränssnitt:

```terminal
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

Det går att köra `--help` som ett alternativ när du kör ett specifikt kommando. Returnerar `--help` för det angivna kommandot.

Exempel på `upgrade:check` kommando med `--help` alternativ:

```bash
bin/uct upgrade:check --help
```

Detta returnerar specifika alternativ som kan köras för `upgrade:check` kommando:

```terminal
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

- Undvik att ha två moduler med samma namn.
- Följ Adobe Commerce [kodstandarder](https://developer.adobe.com/commerce/php/coding-standards/).
- Adobe Commerce 2.4 [Uppgraderingsguide](https://experienceleague.adobe.com/docs/commerce-operations/assets/adobe-commerce-2-4-upgrade-guide.pdf) bästa praxis.
- Kör [!DNL Upgrade Compatibility Tool] från [[!DNL Site-Wide Analysis Tool]](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/upgrade-compatibility-tool/use-upgrade-compatibility-tool/integrate-analysis-tool.html) for [Adobe Commerce i molninfrastruktur](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/overview.html){target=_blank} projekt.

## Optimera resultatet

The [!DNL Upgrade Compatibility Tool] innehåller en rapport med resultat med alla problem som identifieras i ditt projekt som standard. Du kan optimera resultaten för att fokusera på de problem som du måste åtgärda för att slutföra uppgraderingen:

- Använd alternativet `--ignore-current-version-compatibility-issues` när du bara vill få nya utgåvor som introduceras med uppdateringen från den aktuella versionen till målversionen i [!DNL Upgrade Compatibility Tool] rapport.
- Lägga till `--min-issue-level` den här inställningen gör att du kan ange en miniminivå för utgåvor, så att du bara kan prioritera de viktigaste problemen med din uppgradering.
- The [!DNL Upgrade Compatibility Tool] kräver minst 2 GB RAM-minne för att köras. Den här inställningen rekommenderas för att undvika problem på grund av en låg minnesbegränsning. The [!DNL Upgrade Compatibility Tool] visar en fråga om du kör `upgrade:check` kommando med låg `memory_limit` inställning.
