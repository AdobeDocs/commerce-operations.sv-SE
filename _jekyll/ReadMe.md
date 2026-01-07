---
source-git-commit: 4589c405bab743001e967a9825d578ee1a03c216
workflow-type: tm+mt
source-wordcount: '672'
ht-degree: 0%

---
# Ökning

Det här projektet innehåller flera olika omformningsuppgifter för att automatisera olika aspekter av arbetsflödet, som att generera data för nyhetssammanfattningar, återge mallade filer, optimera bilder och generera kartor. Nedan visas beskrivningar och riktlinjer för användning för varje åtgärd av typen Rake som definieras i filen Rakefile.

## Gör om uppgifter

### `render`

Återger mallfilerna i katalogen `_jekyll/templates` med data från `_jekyll/_data/`. Resultatet hittas i katalogen `help/includes/templated`. Den här aktiviteten upprätthåller automatiskt relationer och tidsstämplar efter återgivningen.

**Användning:**

```sh
rake render
```

**Vad den gör:**
- Kör återgivningsskriptet för att generera mallfiler
- Kör `includes:maintain_all` för att uppdatera inkluderade relationer och tidsstämplar
- Ser till att alla inkluderade metadata är aktuella efter rendering

### `image_optim`

Optimerar bilder i ändrade ej implementerade filer. För andra bilder använder du argumentet `path` för att ange katalogen eller filen.

**Användning:**

```sh
rake image_optim
```

**Med `path` argument:**

```sh
rake image_optim path=../path/to/dir/or/file
```

### `whatsnew`

Genererar data för en nyhetssammanfattning. Standardtidsramen är sedan den senaste uppdateringen. Du kan ange en annan period med argumentet `since`.

**Användning:**

```sh
rake whatsnew
```

**Med `since` argument:**

```sh
rake whatsnew since="jul 4"
```

### `whatsnew_bp`

Genererar data för en nyhetssammanfattning på Best Practices. Standardtidsramen är sedan den senaste uppdateringen. Du kan ange en annan period med argumentet `since`.

**Användning:**

```sh
rake whatsnew_bp
```

**Med `since` argument:**

```sh
rake whatsnew_bp since="jul 4"
```

### `azure_regions`

Skapar en Azure-regionskarta. Indatafilen ska placeras i `_jekyll/tmp/azure-regions.json`. Resultatet hittas i `_jekyll/tmp/azure-regions.svg`. Observera att du behöver Python, [PyGMT](https://www.pygmt.org/latest/install.html) och [pdf2svg](https://formulae.brew.sh/formula/pdf2svg) installerade.

**Användning:**

```sh
rake azure_regions
```

### `get_released_versions`

Hämtar de senaste 10 versionerna från databasen `magento/magento2`. Kräver att [GitHub CLI](https://cli.github.com/) installeras och autentiseras.

**Användning:**

```sh
rake get_released_versions
```

**Utdata:** Genererar `tmp/core-release.txt` med versionstaggnamn och datum.

### `first_merge_date`

Hämtar datumet för den första sammanfogningen till en angiven gren. Kräver att [GitHub CLI](https://cli.github.com/) installeras och autentiseras.

**Användning:**

```sh
rake first_merge_date base=develop
```

**Argument:**

- `base` (obligatoriskt): Målgrennamnet som ska kontrolleras för sammanslagningar.

### `includes:maintain_relationships`

Identifierar och uppdaterar filen `include-relationships.yml` genom att söka igenom alla markeringsfiler i katalogen `help` efter inkluderingssatser med mönstret `{{$include /help/_includes/filename.md}}`. Med den här aktiviteten behålls automatiskt relationerna mellan de huvudsakliga innehållsfilerna och deras inkluderade filer.

**Användning:**

```sh
rake includes:maintain_relationships
```

**Vad den gör:**
- Läser listan över befintliga inkluderingsfiler från katalogen `help/_includes`
- Söker igenom alla huvudmarkeringsfiler för att hitta vilka som refererar till var och en av dem
- Använder mönstret `{{$include /help/_includes/filename.md}}` för att identifiera referenser
- Uppdaterar filen `include-relationships.yml` med identifierade relationer
- Innehåller en sammanfattning av ändringar som gjorts och identifierar orefererade inkluderar

### `includes:maintain_timestamps`

Underhåller att inkludera tidsstämplar genom att lägga till de senaste tidsstämplarna för filändring i huvudfilerna. Den här aktiviteten läser filen `include-relationships.yml`, kontrollerar git-historik för varje inkluderingsfil och lägger till eller uppdaterar tidsstämplar i slutet av huvudfilerna.

**Användning:**

```sh
rake includes:maintain_timestamps
```

**Vad den gör:**
- Inläsningar innehåller relationer från `include-relationships.yml`
- För varje huvudfil hittas det senaste Git-datumet bland dess inkluderingsfiler
- Lägger till eller uppdaterar HTML-kommentarer med tidsstämplar i slutet av huvudfilerna
- Använder formatet: `<!-- Last updated from includes: YYYY-MM-DD HH:MM:SS -->`
- Detaljerade utdata visar vilka filer som har kontrollerats och deras tidsstämplar

**Exempelutdata:**

```console
Processing installation/advanced.md...
  Latest include change: 2024-04-16 09:42:31
  Include files checked: help/_includes/cli-consumers.md (2022-09-12 09:38:25), help/_includes/secure-install.md (2022-09-08 11:33:05), help/_includes/sensitive-data.md (2024-04-16 09:42:31)
  Added new timestamp
```

### `includes:maintain_all`

En smidig åtgärd som kör både `includes:maintain_relationships` och `includes:maintain_timestamps` i sekvens. Detta är det rekommenderade sättet att behålla både inkluderade relationer och tidsstämplar.

**Användning:**

```sh
rake includes:maintain_all
```

### `unused_includes`

Sökningar innehåller filer i katalogen `help/_includes` som inga kodningsfiler refererar till. Detta hjälper till att identifiera överblivna inkluderingsfiler som kan tas bort på ett säkert sätt.

**Användning:**

```sh
rake unused_includes
```

## Visar tillgängliga uppgifter

Om du vill visa alla tillgängliga penseldrag med beskrivningar använder du:

```sh
rake --tasks
```

Mer detaljerad information om en viss uppgift finns i:

```sh
rake -T [task_name]
```

## Inkludera hanteringsaktiviteter

Alla inkluderingsrelaterade uppgifter är ordnade under namnutrymmet `includes` för bättre organisation:

```sh
# Discover and maintain include relationships
rake includes:maintain_relationships

# Add/update timestamps based on include file changes
rake includes:maintain_timestamps

# Do both operations in sequence (recommended)
rake includes:maintain_all
```

## Inkludera relationernas filformat

Filen `include-relationships.yml` spårar relationerna mellan huvudinnehållsfilerna och deras inkluderade filer. Den här filen underhålls automatiskt av `maintain_include_relationships`-streckaktiviteten, som identifierar relationer genom att läsa befintliga inkluderingsfiler och söka efter huvudfiler som refererar till dem.

**Filstruktur:**

```yaml
---
metadata:
  last_updated: '2025-08-22 14:04:37'
  description: 'Index of main files and their included files for automatic timestamp updates'
  total_relationships: 57
  auto_discovered: true
  discovery_date: '2025-08-22 14:04:37'
relationships:
  configuration/deployment/example-environment-variables.md:
    - "/help/_includes/config-save-config.md"
    - "/help/_includes/config-update-build-system.md"
    - "/help/_includes/config-update-prod-system.md"
  # ... more relationships
```

**Fält:**
- `metadata.last_updated`: Tidsstämpel för den senaste uppdateringen
- `metadata.total_relationships`: Totalt antal huvudfiler med inkluderingar
- `metadata.auto_discovered`: Anger att filen genererades automatiskt
- `metadata.discovery_date`: Datum när relationer först upptäcktes
- `relationships`: Mappning av huvudfiler till de inkluderade filerna

**Inkludera satsformat:**
Huvudinnehållsfiler använder följande syntax för att inkludera andra filer:

```markdown
{{$include /help/_includes/filename.md}}
```

## Förutsättningar

- Ruby och Bundler är installerade.
- Nödvändiga pärmar har angetts i Gemfile (huvudberoenden anges av `adobe-comdox-exl-rake-tasks`).
- [GitHub CLI](https://cli.github.com/) för `get_released_versions`- och `first_merge_date`-aktiviteterna.
- Python, [PyGMT](https://www.pygmt.org/latest/install.html) och [pdf2svg](https://formulae.brew.sh/formula/pdf2svg) för aktiviteten `azure_regions`.

## Inställningar

1. Installera nödvändiga pärlor:

   ```sh
   bundle install
   ```

2. Kontrollera att Python, PyGMT och pdf2svg är installerade för aktiviteten `azure_regions`. Mer information om konfigurationen finns i dokumentationen i kommentarer på [_scripts/azure_regions.py](_scripts/azure_regions.py).
