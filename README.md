---
source-git-commit: 4589c405bab743001e967a9825d578ee1a03c216
workflow-type: tm+mt
source-wordcount: '866'
ht-degree: 3%

---
# Adobe Commerce tekniska dokumentation

Vi välkomnar bidrag från såväl communityn som från Adobe-anställda utanför dokumentationsteamen.

## Förimplementera kopplingar för bildoptimering

Den här databasen innehåller automatiska förimplementeringskopplingar som optimerar bilder innan implementering. **Alla medverkande bör aktivera dessa kopplingar** för att säkerställa konsekvent bildoptimering och minskad databasstorlek.

### Snabbinställningar

När du har klonat databasen kör du:

```bash
.githooks/setup-hooks.sh
```

### Vad krokarna gör

- Identifiera automatiskt mellanlagrade bildfiler (PNG, JPG, JPEG, GIF, SVG)
- Kör `image_optim` för att komprimera och optimera bilder
- Scenoptimerade bilder på nytt automatiskt
- Säkerställ att alla dedikerade bilder optimeras korrekt

### Fördelar

- Minskad databasstorlek
- Snabbare sidinläsning för dokumentation
- Enhetlig bildkvalitet för alla deltagare
- Ingen manuell optimering krävs

Detaljerade installationsanvisningar, felsökning och konfiguration finns i [`.githooks/README.md`](.githooks/README.md).

## Adobe Open Source - uppförandekod

Detta projekt har antagit [Adobe Open Source Code of Conduct](code-of-conduct.md) eller [.NET Foundation Code of Conduct](https://dotnetfoundation.org/code-of-conduct). Mer information finns i artikeln [Contributing](contributing.md).

## Om dina bidrag till Adobe-innehåll

Se [Adobe Docs Contributor Guide](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

Hur du bidrar beror på vem du är och vilken typ av ändringar du vill bidra med:

### Mindre ändringar

Om du bidrar med mindre uppdateringar kan du besöka artikeln och klicka på feedbackområdet som visas längst ned i artikeln, klicka på **Detaljerade feedbackalternativ** och sedan på **Föreslå en redigering** för att gå till markeringskällfilen på GitHub. Använd GitHub-gränssnittet för att göra uppdateringar. Mer information finns i den allmänna [Adobe Docs Contributor-guiden](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

Mindre korrigeringar och förtydliganden som du lämnar in för dokumentation och kodexempel i den här rapporten omfattas av Adobe användarvillkor.

### Större ändringar eller nya artiklar från communitymedlemmar

Om du är en del av Adobe-communityn och vill skapa en ny artikel eller skicka större ändringar använder du fliken Problem i Git-databasen för att skicka in ett problem för att starta en konversation med dokumentationsteamet. När du har gått med på en plan måste du arbeta med en anställd för att få in det nya innehållet genom en kombination av arbete i det offentliga och privata arkivet.

### Större förändringar för Adobe medarbetare

Om du är teknikskribent, programchef eller utvecklare för en Adobe Experience Cloud-lösning och det är ditt jobb att bidra till eller skapa tekniska artiklar, bör du använda den privata databasen på `https://git.corp.adobe.com/AdobeDocs`.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## Verktyg och inställningar

Deltagare i communityn kan använda GitHub-gränssnittet för grundläggande redigering eller förgrena rapporten för att göra större insatser.

Mer information finns i [Adobe Docs Contributor Guide](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

## Så här använder du kod för att formatera ämnet

Alla artiklar i den här databasen använder smaksatt GitHub-kod. Om du inte är van vid att markera något läser du:

- [Grunderna för markeringar](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
- [Utskrivbart kalkylblad för markering](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## Mallar

För vissa ämnen använder vi datafiler och mallar för att generera publicerat innehåll. Användningsexempel för den här metoden är:

- Publicera stora mängder programmatiskt genererat innehåll
- En enda källa till sanning för kunder i flera system som kräver maskinläsbara filformat, som YAML, för integrering (t.ex. Site-Wide Analysis Tool)

Exempel på mallat innehåll är, men är inte begränsade till, följande:

- [Referens för CLI-verktyg](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html)
- [Produkttillgänglighetstabeller](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)
- [Systemkravstabeller](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)

### Generera mallat innehåll

I allmänhet behöver de flesta skribenter bara lägga till en releaseversion till tabellerna med produkttillgänglighet och systemkrav. Underhåll för allt annat mallat innehåll automatiseras eller hanteras av en dedikerad teammedlem. De här instruktionerna är avsedda för de flesta skribenter.

>**OBS!**
>
>- För att generera mallinnehåll måste du arbeta på kommandoraden i en terminal.
>- Du måste ha installerat Ruby för att köra återgivningsskriptet. Se [_jekyll/.ruby-version ] (_jekyll/.ruby-version) för den version som krävs.

Här nedan finns en beskrivning av filstrukturen för mallat innehåll:

- `_jekyll` - Innehåller teman och obligatoriska resurser
- `_jekyll/_data` - Innehåller de maskinläsbara filformat som används för att återge mallar
- `_jekyll/templated` - Innehåller HTML-baserade mallfiler som använder mallspråket Flytande
- `help/_includes/templated` - Innehåller genererade utdata för mallat innehåll i `.md`-filformat så att det kan publiceras i Experience League-avsnitt. Återgivningsskriptet skriver automatiskt genererade utdata till den här katalogen åt dig

Så här uppdaterar du mallinnehåll:

1. Öppna en datafil i katalogen `/jekyll/_data` i textredigeraren. Exempel:

   - [Produkttillgänglighetstabeller](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html): `/jekyll/_data/product-availability.yml`
   - [Systemkravstabeller](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html): `/jekyll/_data/system-requirements.yml`

1. Använd den befintliga YAML-strukturen för att skapa poster.

   Om du till exempel vill lägga till en version av Adobe Commerce i produkttillgänglighetstabellerna lägger du till följande i varje post i `extensions`- och `services`-avsnitten i `/jekyll/_data/product-availability.yml`-filen (ändra versionsnummer efter behov):

   ```yaml
   support:
      - core: 1.2.3
        version: 4.5.6
   ```

1. Navigera till katalogen `_jekyll`.

   ```bash
   cd _jekyll
   ```

1. Generera mallinnehåll och skriv utdata till katalogen `help/_includes/templated`.

   ```bash
   bundle exec rake render
   ```

   >**OBS!** Du måste köra skriptet från katalogen `_jekyll`. Om detta är första gången du kör skriptet måste du installera Ruby-beroenden först med kommandot `bundle install`. Huvudsakliga rasteraktiviteter och beroenden (Jekyll, Rake, bildoptimering) tillhandahålls av `adobe-comdox-exl-rake-tasks`-grammet för bättre underhåll i Adobe Commerce dokumentationsarkiv. Anpassade uppgifter som är specifika för den här databasen implementeras i `Rakefile`.

1. Gå tillbaka till katalogen `root`.

   ```bash
   cd ..
   ```

1. Verifiera att de förväntade `help/_includes/templated` filerna har ändrats.

   ```bash
   git status
   ```

   Utdata bör se ut ungefär så här:

   ```bash
   modified:   _data/product-availability.yml
   modified:   help/_includes/templated/product-availability-extensions.md
   ```

1. Gör ändringar.

   ```bash
   git add .
   git commit -m "descriptive message of the intended commit"
   git push
   ```

Mer information om [datafiler](https://jekyllrb.com/docs/datafiles), [flytande filter](https://jekyllrb.com/docs/liquid/filters/) och andra funktioner finns i dokumentationen för Jekyll.

## Tillgängliga uppspelningsuppgifter

I den här databasen används streckuppgifter som tillhandahålls av `adobe-comdox-exl-rake-tasks` Gem. Om du vill se alla tillgängliga uppgifter kör du:

```bash
cd _jekyll
bundle exec rake --tasks
```
