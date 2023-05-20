---
source-git-commit: 4b767014f325bef7e07cea11d01089206bf44caf
workflow-type: tm+mt
source-wordcount: '475'
ht-degree: 0%

---
# Adobe Commerce tekniska dokumentation

Vi välkomnar bidrag från både vår community och från Adobe anställda utanför dokumentationsteamen.

## Adobe uppförandekod med öppen källkod

Detta projekt har antagit [Adobe uppförandekod med öppen källkod](code-of-conduct.md) eller [.NET Foundation - uppförandekod](https://dotnetfoundation.org/code-of-conduct). Mer information finns i [Bidrar](contributing.md) artikel.

## Om dina bidrag till Adobe innehåll

Se [Adobe Docs Contributor Guide](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html).

Hur du bidrar beror på vem du är och vilken typ av ändringar du vill bidra med:

### Mindre ändringar

Om du bidrar med mindre uppdateringar av ditt hjärta kan du gå till artikeln och klicka på knappen **Redigera** i artikeln som går till artikelns GitHub-källa. Använd sedan bara GitHub-gränssnittet för att göra uppdateringarna. Se det allmänna [Adobe Docs Contributor Guide](https://experienceleague.adobe.com/docs/contributor/contributor-guide/introduction.html) för mer information.

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

## Så här använder du kod för att formatera ditt ämne

Alla artiklar i den här databasen använder smaksatt GitHub-kod. Om du inte är van vid att markera något läser du:

* [Grunderna i markeringar](https://help.github.com/articles/getting-started-with-writing-and-formatting-on-github/)
* [Utskrivbart markeringsdatablad](https://guides.github.com/pdfs/markdown-cheatsheet-online.pdf)

## Mallar

The `_jekyll` -katalogen innehåller mallämnen och obligatoriska resurser.
Mallarna som använder mallspråket Flytande finns i `_jekyll/templated` som HTML-filer.
The `_jekyll/_data` -katalogen innehåller filer med de data som används för att återge mallarna.

Så här återger du alla mallar:

1. Navigera till `_jekyll` katalog.

   cd_jekyll

1. Kör återgivningsskriptet.

```
_scripts/render
```

> **OBS!** Du måste köra skriptet från `_jekyll` katalog.
> **OBS!** Du måste ha installerat Ruby för att köra skriptet.

Skriptet kör återgivning och skriver återgivna mallar till `help/_includes/templated` katalog.

Läs Jekyll-dokumentationen för mer information om [Datafiler](https://jekyllrb.com/docs/datafiles, [Flytande filter](https://jekyllrb.com/docs/liquid/filters/)och andra funktioner.
