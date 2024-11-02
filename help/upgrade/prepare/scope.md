---
title: Förstå uppgraderingsomfång
description: Lär dig mer om bakåtkompatibla ändringar i en release som kan påverka Adobe Commerce anpassade moduler eller tillägg från tredje part.
exl-id: dab2a14f-dbf0-422e-afb4-642e2220ec7a
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '897'
ht-degree: 0%

---

# Förstå omfattningen av uppgraderingen

Granska [versionsinformationen](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview) för att förstå omfattningen av en release, inklusive förbättringar, felkorrigeringar och kända problem som kan påverka externa och anpassade moduler.

## Bakåtkompatibla ändringar

Adobe Commerce-versioner kan innehålla ändringar som är inkompatibla bakåt. Läs igenom vår bakåtkompatibla ändringsdokumentation och se följande:

- **[Större markeringar av ändringar](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/highlights/)** - Ändringar som har stor effekt och som kräver detaljerade förklaringar och specialinstruktioner för att säkerställa att tredjepartsmoduler fortsätter att fungera.
- **[Mindre ändring, referens](https://developer.adobe.com/commerce/php/development/backward-incompatible-changes/reference/)** - Referensdokumentation som genererats från kodbasen som beskriver mindre ändringar av klasser, API-medlemskap, databas, beroendeinjektion, gränssnitt, layouter, system och XSD.

## Tredjepartstillägg

Adobe Commerce Marketplace nya kompatibilitetsprincip säkerställer att _alla_ listade tillägg är kompatibla med den senaste versionen inom 30 dagar från GA-datumet. Därför är det viktigt att du alltid har tillgång till tredjepartstillägg via Marketplace.

## Anpassade moduler

Alla anpassade moduler ska kontrolleras mot målversionen som du vill uppgradera till. Det här är den mest tids- och resursintensiva uppgraderingsprocessen. När du utvärderar dina anpassade moduler måste du leta efter bakåtkompatibla ändringar och vara medveten om nya metoder, som till exempel att kontrollenheten har kopplats ned. Du kan läsa mer om detta i [versionsinformationen](https://experienceleague.adobe.com/en/docs/commerce-operations/release/notes/overview). Se även till att du följer [bästa praxis](https://developer.adobe.com/commerce/php/best-practices/extensions/) för modulutveckling.

## [!DNL Upgrade Compatibility Tool]

[!DNL Upgrade Compatibility Tool] är ett kommandoradsverktyg som analyserar din instans med avseende på eventuella uppgraderingsproblem. Den söker efter problem mellan den version du har installerat och den version du försöker uppgradera till.

Om du använder det här verktyget minskar det arbete som krävs för att förstå omfattningen och effekten av en uppgradering. Det hjälper dig att undvika vanliga kodproblem när du uppgraderar och ger en tydlig vägledning om hur du löser identifierade problem. Det kan även hjälpa dig att prioritera de viktigaste problemen för att säkerställa en lyckad uppgradering, vilket sparar både tid och kostnader vid uppgradering.

Se följande avsnitt för att komma igång med [!DNL Upgrade Compatibility Tool]. Se [!DNL Upgrade Compatibility Tool] [handboken](../upgrade-compatibility-tool/overview.md) för mer teknisk information och avancerade användningsexempel.

### Ladda ned verktyget

Hämta verktyget med Composer. Det kräver PHP 7.3 eller senare, minst 2 GB RAM, Node.js (om du kontrollerar kompatibiliteten med GraphQL) och en Adobe Commerce-licens.

```bash
composer create-project magento/upgrade-compatibility-tool uct --repository https://repo.magento.com
```

### Kör verktyget

Så här analyserar du instansen och kontrollerar om det finns fel, varningar och allvarliga problem:

```bash
bin/uct upgrade:check <dir> -c <coming version> 
```

>[!NOTE]
>
> Argumentet `<dir>` är den katalog där kodbasen lagras. Alternativet `-c` jämför din kodbas med den angivna versionen.

Så här identifierar du de mest kritiska problemen som ditt team måste ta itu med:

```bash
bin/uct upgrade:check /path/to/magento/ --ignore-current-compatibility-issues –min-issue-level critical --vanilla-dir /path/to/vanilla/code/ /path/to/magento/app/code/Vendor/
```

Fler alternativ att använda med det här kommandot är:

- `--ignore-current-version-compatibility-issues` - Utelämnar alla kända allvarliga problem, fel och varningar i den aktuella versionen. Den innehåller bara fel mot den version du försöker uppgradera.

- `--min-issue-level` - Gör att du kan ange en miniminivå för antalet utgåvor så att du bara kan prioritera de viktigaste utgåvorna av din uppgradering. Alternativen är varning, fel och kritiska i stigande ordning av allvarlighetsgrad.

- `-m | [=MODULE-PATH]` - Om du bara vill analysera en viss leverantör, modul eller katalog kan du även ange sökvägen som ett alternativ.

- `--vanilla-dir` - Gör att du kan kontrollera om det finns några funktioner eller anpassningar som inte är standard i kärnkoden. Det är viktigt att dessa rensas upp i förväg. En vanilj-instans av din version hämtas automatiskt som referens.

  >[!NOTE]
  >
  > Detta kan även göras med kommandot `core:code:changes` i verktyget).

### Analysera utdata

[!DNL Upgrade Compatibility Tool] exporterar en JSON-fil som identifierar den kod eller de moduler som påverkas, allvarlighetsgraden och en beskrivning av problemet för varje problem som upptäcks. Den ger också en sammanfattande rapport med en komplexitetspoäng, som gör att ditt team kan förstå ungefär vad som krävs för att uppgradera till den senaste versionen. Ju lägre komplexitetspoäng, desto enklare är det att uppgradera.

Följande utdata visar en exempelsammanfattningsrapport:

```console
 ------------------------ --------
  Installed version        2.4.2
  Adobe Commerce version   2.4.3
  Running time             0m:48s
  Checked modules          14
  Core checked modules     0
  Core modified files      0
  % core modified files    0.00
  PHP errors found         109
  PHP warnings found       0
  GraphQL errors found     0
  GraphQL warnings found   0
  Total errors found       109
  Total warnings found     0
  Complexity score         218
 ------------------------ --------
```

### Tips och råd

Alla problem som verktyget identifierade visas i rapporten med specifika felkoder. Använd [felmeddelandereferensen](../upgrade-compatibility-tool/error-messages.md) om du vill ha mer information om varje problem. Adobe ger också förslag på hur du kan åtgärda olika typer av problem så att du kan planera dina åtgärder.

Använd rapporten för att beräkna hur mycket arbete det kommer att ta att uppdatera koden för uppgraderingen. Baserat på din erfarenhet kan du uppskatta hur stor uppgradering som krävs baserat på det totala antalet identifierade problem och problemens svårighetsgrad. Eftersom det här är ett kommandoradsverktyg kan du införliva detta i automatiska testnings- och kodkontrollsviter och använda JSON-utdata för att generera rapporter.

Vi rekommenderar att du sparar resultaten från varje uppgraderingsprojekt så att du kan jämföra framtida uppgraderingsresultat med tidigare resultat. Med fortsatt användning kommer du att börja utveckla en bra bild av hur stor insats det krävs för att uppgradera till nästa version, bara från den sammanfattande rapporten från verktyget.

Vi rekommenderar även att du kör verktyget regelbundet när du arbetar med uppgraderingen för att få en överblick över hur arbetet fortskrider. Antalet problem bör minska när du åtgärdar dem. Detta hjälper även teamet att bestämma vilket tillvägagångssätt som passar bäst för att distribuera materialet.

[!DNL Upgrade Compatibility Tool] fortsätter att förbättras och framtida versioner innehåller funktioner som automatiska korrigeringar som hjälper dig att åtgärda problem så snabbt som möjligt. De senaste förbättringarna som släpptes i januari 2022 inkluderar kompatibilitetstester för PHP 8.1 och visualiseringsfunktioner för HTML som hjälper dig att snabbt identifiera områden som kan kräva mer arbete med att uppgradera.
