---
source-git-commit: 0709cd6510adce0f513894fdecb2de5ac88d0e87
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 3%

---
# Adobe Commerce tekniska dokumentation

Vi välkomnar bidrag från såväl communityn som från Adobe anställda utanför dokumentationsteamen.

## Adobe uppförandekod med öppen källkod

Detta projekt har antagit [Adobe Open Source Code of Conduct](code-of-conduct.md) eller [.NET Foundation Code of Conduct](https://dotnetfoundation.org/code-of-conduct). Mer information finns i artikeln [Contributing](contributing.md).

## Om dina bidrag till Adobe innehåll

Se [Adobe Docs Contributor Guide](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

Hur du bidrar beror på vem du är och vilken typ av ändringar du vill bidra med:

### Mindre ändringar

Om du bidrar med mindre uppdateringar kan du gå till artikeln och klicka på feedbackområdet som visas längst ned i artikeln. Klicka på **Detaljerade alternativ för feedback** och klicka sedan på **Föreslå en redigering** om du vill gå till källfilen för markering på GitHub. Använd GitHub-gränssnittet för att göra uppdateringar. Se det allmänna [Adobe Docs Contributor Guide](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) för mer information.

Mindre korrigeringar och förtydliganden som du lämnar in för dokumentation och kodexempel i den här rapporten omfattas av Adobe användarvillkoren.

### Större ändringar eller nya artiklar från communitymedlemmar

Om du är en del av Adobe-communityn och vill skapa en ny artikel eller skicka in större ändringar använder du fliken Problem i Git-databasen för att skicka in ett problem för att starta en konversation med dokumentationsteamet. När du har gått med på en plan måste du arbeta med en anställd för att få in det nya innehållet genom en kombination av arbete i det offentliga och privata arkivet.

<!--
If you submit a pull request with significant changes to documentation and code examples, you'll see a message in the pull request asking you to submit an online contribution license agreement (CLA). We need you to complete the online form before we can review your pull request.
-->

### Stora förändringar för anställda i Adobe

Om du är teknikskribent, programchef eller utvecklare för en Adobe Experience Cloud-lösning och det är ditt jobb att bidra till eller skriva tekniska artiklar bör du använda det privata arkivet på `https://git.corp.adobe.com/AdobeDocs`.

<!--Employees from other parts of the Adobe world should use the public repo for minor updates.-->

## Verktyg och inställningar

Deltagare i communityn kan använda GitHub-gränssnittet för grundläggande redigering eller förgrena rapporten för att göra större insatser.

Se [Adobe Docs Contributor Guide](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) för mer information.

## Så här använder du kod för att formatera ämnet

Alla artiklar i den här databasen använder smaksatt GitHub-kod. Om du inte är van vid att markera något läser du:

* [Grunderna i markeringar](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
* [Utskrivbart markeringsblad](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## Mallar

För vissa ämnen använder vi datafiler och mallar för att generera publicerat innehåll. Användningsexempel för den här metoden är:

* Publicera stora mängder programmatiskt genererat innehåll
* En enda källa till sanning för kunder i flera system som kräver maskinläsbara filformat, som YAML, för integrering (t.ex. Site-Wide Analysis Tool)

Exempel på mallat innehåll är, men är inte begränsade till, följande:

* [Referens för CLI-verktyg](https://experienceleague.adobe.com/docs/commerce-operations/reference/commerce-on-premises.html)
* [Produkttillgänglighetstabeller](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html)
* [Systemkravstabeller](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html)

### Generera mallat innehåll

I allmänhet behöver de flesta skribenter bara lägga till en releaseversion till tabellerna med produkttillgänglighet och systemkrav. Underhåll för allt annat mallat innehåll automatiseras eller hanteras av en dedikerad teammedlem. De här instruktionerna är avsedda för de flesta skribenter.

>**OBS!**
>
>* För att generera mallinnehåll måste du arbeta på kommandoraden i en terminal.
>* Du måste ha installerat Ruby för att köra återgivningsskriptet. Se [_jekyll/.ruby-version](_jekyll/.ruby-version) för den version som krävs.

Här nedan finns en beskrivning av filstrukturen för mallat innehåll:

* `_jekyll`—Innehåller teman och obligatoriska resurser
* `_jekyll/_data`—Innehåller de maskinläsbara filformat som används för att återge mallar
* `_jekyll/templated`—Innehåller HTML-baserade mallfiler som använder mallspråket Flytande
* `help/_includes/templated`—Innehåller genererade utdata för mallinnehåll i `.md` filformat så att det kan publiceras i Experience League-ämnen; återgivningsskriptet skriver automatiskt genererade utdata i den här katalogen åt dig

Så här uppdaterar du mallinnehåll:

1. Öppna en datafil i textredigeraren `/jekyll/_data` katalog. Exempel:

   * [Produkttillgänglighetstabeller](https://experienceleague.adobe.com/docs/commerce-operations/release/product-availability.html): `/jekyll/_data/product-availability.yml`
   * [Systemkravstabeller](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html): `/jekyll/_data/system-requirements.yml`

1. Använd den befintliga YAML-strukturen för att skapa poster.

   Om du till exempel vill lägga till en version av Adobe Commerce i produkttillgänglighetstabellerna lägger du till följande i varje post i `extensions` och `services` avsnitt i `/jekyll/_data/product-availability.yml` fil (ändra versionsnummer efter behov):

   ```
   support:
      - core: 1.2.3
        version: 4.5.6
   ```

1. Navigera till `_jekyll` katalog.

   ```
   cd _jekyll
   ```

1. Generera mallinnehåll och skriv utdata till `help/_includes/templated` katalog.

   ```
   rake render
   ```

   >**OBS!** Du måste köra skriptet från `_jekyll` katalog. Om detta är första gången du kör skriptet måste du installera Ruby-beroenden först med `bundle install` -kommando.

1. Navigera tillbaka till `root` katalog.

   ```
   cd ..
   ```

1. Verifiera att `help/_includes/templated` filer ändrades.

   ```
   git status
   ```

   Utdata bör se ut ungefär så här:

   ```
   modified:   _data/product-availability.yml
   modified:   help/_includes/templated/product-availability-extensions.md
   ```

1. Gör ändringar.

   ```
   git add
   git commit -m "_descriptive message of the intended commit_"
   git push
   ```

Läs Jekyll-dokumentationen för mer information om [Datafiler](https://jekyllrb.com/docs/datafiles), [Flytande filter](https://jekyllrb.com/docs/liquid/filters/)och andra funktioner.
