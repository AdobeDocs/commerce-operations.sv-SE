---
source-git-commit: ca9e04d50e69b8a51ec4a6fbcf1d35f0fb363fab
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---
# Ökning

Det här projektet innehåller flera olika omformningsuppgifter för att automatisera olika aspekter av arbetsflödet, som att generera data för nyhetssammanfattningar, återge mallade filer, optimera bilder och generera kartor. Nedan visas beskrivningar och riktlinjer för användning för varje åtgärd av typen Rake som definieras i filen Rakefile.

## Gör om uppgifter

### `render`

Återger mallfilerna i katalogen `_jekyll/templates` med data från `_jekyll/_data/`. Resultatet hittas i katalogen `help/includes/templated`.

**Användning:**

```sh
rake render
```

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

## Förutsättningar

- Ruby och Bundler är installerade.
- Nödvändiga pärlor specificerade i filen Gemfile.
- Python, [PyGMT](https://www.pygmt.org/latest/install.html) och [pdf2svg](https://formulae.brew.sh/formula/pdf2svg) för aktiviteten `azure_regions`.

## Inställningar

1. Installera nödvändiga pärlor:

   ```sh
   bundle install
   ```

2. Kontrollera att Python, PyGMT och pdf2svg är installerade för aktiviteten `azure_regions`. Mer information om konfigurationen finns i dokumentationen i kommentarer på [_scripts/azure_regions.py](_scripts/azure_regions.py).
