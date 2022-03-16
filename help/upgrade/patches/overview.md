---
title: Så här fungerar korrigeringar
description: Lär dig mer om de olika typerna av patchar för Adobe Commerce och Magento Open Source och hur de fungerar.
source-git-commit: 06ac3169a5e3813e4f50246f54f91998e14b5985
workflow-type: tm+mt
source-wordcount: '619'
ht-degree: 0%

---


# Så här fungerar patchar

>[!WARNING]
>
>Vi rekommenderar starkt att du testar alla korrigeringsfiler i en staging- eller utvecklingsmiljö innan du distribuerar till produktionen. Vi rekommenderar starkt att du säkerhetskopierar dina data innan du implementerar en korrigering. Se [Säkerhetskopiera och återställa filsystemet](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-backup.html).

Patch-filer (eller diff-filer) är textfiler som innehåller följande information:

- Den eller de filer som ska ändras.
- Radnumret som börjar ändringen och antalet rader som ska ändras.
- Den nya koden som ska bytas in.

När [patch](https://en.wikipedia.org/wiki/Patch_(Unix)) programmet körs, filen läses in och de angivna ändringarna görs i filen/filerna.

Det finns tre typer av patchar:

- **Programfixar**—Patchar som Adobe publicerar på [Security Center](https://magento.com/security/patches).
- **Enskilda patchar**—Patchar som Adobe Commerce Support skapar och distribuerar individuellt.
- **Egna patchar**—Icke-officiella korrigeringsfiler som du kan skapa från en Git-implementering.

## Programfixar

Programfixar är korrigeringar som innehåller effektiva säkerhets- eller kvalitetskorrigeringar som påverkar många handlare. Dessa korrigeringar tillämpas på nästa korrigeringsversion för den tillämpliga delversionen. Adobe släpper snabbkorrigeringar efter behov.

Du hittar snabbkorrigeringar i [Security Center](https://magento.com/security/patches). Följ instruktionerna på sidan för att hämta korrigeringsfilen, beroende på version och installationstyp. Använd [kommandorad](../patches/apply.md#) eller [Disposition](../patches/apply.md) för att använda snabbkorrigeringar.

>[!NOTE]
>
>Snabbkorrigeringar kan innehålla ändringar som är inkompatibla bakåt.

## Enskilda patchar

Enskilda korrigeringsfiler innehåller korrigeringar av låg kvalitet för ett specifikt problem. Dessa korrigeringar tillämpas på den senaste delversionen som stöds (till exempel 2.4.x), men kan saknas i den tidigare delversionen som stöds (till exempel 2.3.x). Adobe släpper enskilda patchar efter behov.

Använd [Verktyget Korrigeringar](https://devdocs.magento.com/quality-patches/tool.html) för att lägga på individuella plåster.

>[!NOTE]
>
>Enskilda korrigeringsfiler innehåller inte ändringar som är inkompatibla bakåt.

## Egna patchar

Ibland tar det ett tag för Adobe Engineering Team att inkludera en felkorrigering som gjorts på GitHub i en Adobe Commerce- eller Magento Open Source Composer-version. Under tiden kan du skapa en patch från GitHub och använda [`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/) plugin-program för att använda det i din Composer-baserade installation.

Använd [kommandorad] eller [Disposition] om du vill använda anpassade patchar.

Det finns många sätt att skapa anpassade korrigeringsfiler. I följande exempel fokuseras på att skapa en korrigering från en känd Git-implementering.

Så här skapar du en anpassad patch:

1. Skapa en `patches/composer` i ditt lokala projekt.
1. Identifiera GitHub-implementeringen eller pull-begäran som ska användas för korrigeringen. I det här exemplet används [`2d31571`](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede) implementering, länkad till GitHub-utgåva [#6474](https://github.com/magento/magento2/issues/6474).
1. Lägg till `.patch` eller `.diff` tillägg till implementerings-URL:en. Använd `.diff` för en mindre filstorlek. Till exempel: [https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. Spara sidan som en fil i `patches/composer` katalog. Exempel, `github-issue-6474.diff`.
1. Redigera filen och ta bort `app/code/<VENDOR>/<PACKAGE>` från alla sökvägar så att de är relativa till `vendor/<VENDOR>/<PACKAGE>` katalog.

   >[!NOTE]
   >
   >Textredigerare som automatiskt tar bort efterföljande tomt utrymme eller lägger till nya rader kan bryta lagningen. Använd en enkel textredigerare för att göra dessa ändringar.

I följande exempel visas den tidigare nämnda DIFF-filen efter att alla instanser av `app/code/Magento/Payment`:

```diff
diff --git a/view/frontend/web/js/view/payment/iframe.js b/view/frontend/web/js/view/payment/iframe.js
index c8a6fef58d31..7d01c195791e 100644
--- a/view/frontend/web/js/view/payment/iframe.js
+++ b/view/frontend/web/js/view/payment/iframe.js
@@ -154,6 +154,7 @@ define(
              */
             clearTimeout: function () {
                 clearTimeout(this.timeoutId);
+                this.fail();
 
                 return this;
             },
```

## Tillämpar patchar

Du kan använda patchar på följande sätt:

- [Verktyget Korrigeringar](https://devdocs.magento.com/quality-patches/tool.html)
- [Kommandorad](/help/upgrade/patches/apply.md#command-line)
- [Disposition](/help/upgrade/patches/apply.md#composer)

>[!NOTE]
>
>Information om hur du tillämpar en korrigering på ett Adobe Commerce-infrastrukturprojekt finns i [Tillämpa patchar](https://devdocs.magento.com/cloud/project/project-patch.html) i _Molnguide_.
