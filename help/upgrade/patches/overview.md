---
title: Så här fungerar korrigeringar
description: Lär dig mer om de olika typerna av patchar för Adobe Commerce och hur de fungerar.
exl-id: d7072ed4-7d51-41fe-881a-aae3b2000b55
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Så här fungerar patchar

>[!WARNING]
>
>Vi rekommenderar starkt att du testar alla korrigeringsfiler i en staging- eller utvecklingsmiljö innan du distribuerar till produktionen. Vi rekommenderar även att du säkerhetskopierar dina data innan du implementerar en korrigering. Se [Säkerhetskopiera och återställa filsystemet](../../installation/tutorials/backup.md).

Patch-filer (eller diff-filer) är textfiler som innehåller följande information:

- De filer som ska ändras.
- Radnumret som börjar ändringen och antalet rader som ska ändras.
- Den nya koden som ska bytas in.

När korrigeringsprogrammet körs läses den här filen in och de angivna ändringarna görs i filen/filerna.

Det finns tre typer av patchar:

- **Programfixar** - Programfixar som Adobe publicerar på [Säkerhetscenter](https://magento.com/security/patches).
- **Enskilda korrigeringsfiler** - korrigeringsfiler som skapas och distribueras individuellt av Adobe Commerce Support.
- **Anpassade korrigeringsfiler** - Ej officiella korrigeringsfiler som du kan skapa från en Git-implementering.

## Programfixar

Programfixar är korrigeringar som innehåller effektiva säkerhets- eller kvalitetskorrigeringar som påverkar många handlare. Dessa korrigeringar tillämpas på nästa korrigeringsversion för den tillämpliga delversionen. Adobe släpper snabbkorrigeringar efter behov.

Du hittar snabbkorrigeringar i [Säkerhetscenter](https://magento.com/security/patches). Följ instruktionerna på sidan för att hämta korrigeringsfilen, beroende på version och installationstyp. Använd [kommandoraden](../patches/apply.md#) eller [Composer](../patches/apply.md) för att tillämpa snabbkorrigeringar.

>[!NOTE]
>
>Snabbkorrigeringar kan innehålla ändringar som är inkompatibla bakåt.

## Enskilda patchar

Enskilda korrigeringsfiler innehåller korrigeringar av låg kvalitet för ett specifikt problem. Dessa korrigeringar tillämpas på den senaste delversionen som stöds (till exempel 2.4.x), men kan saknas i den tidigare delversionen som stöds (till exempel 2.3.x). Adobe släpper enskilda patchar efter behov.

Använd [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE){target="_blank"} för att tillämpa enskilda korrigeringar.

>[!NOTE]
>
>Enskilda korrigeringsfiler innehåller inte ändringar som är inkompatibla bakåt.

## Egna patchar

Ibland tar det ett tag för Adobe Engineering Team att inkludera en felkorrigering som gjorts på GitHub i en Adobe Commerce Composer-version. Under tiden kan du skapa en patch från GitHub och använda plugin-programmet [`cweagans/composer-patches`](https://github.com/cweagans/composer-patches/) för att tillämpa den på din Composer-baserade installation.

Använd [kommandoraden](apply.md#command-line) eller [disposition](apply.md#composer) för att använda anpassade korrigeringsfiler.

Det finns många sätt att skapa anpassade korrigeringsfiler. I följande exempel fokuseras på att skapa en korrigering från en känd Git-implementering.

Så här skapar du en anpassad patch:

1. Skapa en `patches/composer`-katalog i ditt lokala projekt.
1. Identifiera GitHub-implementeringen eller pull-begäran som ska användas för korrigeringen. I det här exemplet används [`2d31571`](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede) commit, som är länkat till GitHub-utgåvan [#6474](https://github.com/magento/magento2/issues/6474).
1. Lägg till `.patch` eller `.diff`-tilläggen i den implementerade URL:en. Använd `.diff` för en mindre filstorlek. Till exempel: [https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff](https://github.com/magento/magento2/commit/2d31571f1bacd11aa2ec795180abf682e0e9aede.diff)
1. Spara sidan som en fil i katalogen `patches/composer`. Exempel: `github-issue-6474.diff`.
1. Redigera filen och ta bort `app/code/<VENDOR>/<PACKAGE>` från alla sökvägar så att de är relativa till katalogen `vendor/<VENDOR>/<PACKAGE>`.

   >[!NOTE]
   >
   >Textredigerare som automatiskt tar bort efterföljande tomt utrymme eller lägger till nya rader kan bryta lagningen. Använd en enkel textredigerare för att göra dessa ändringar.

I följande exempel visas den tidigare nämnda DIFF-filen när alla instanser av `app/code/Magento/Payment` har tagits bort:

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

Du kan använda patchar på något av följande sätt:

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE){target="_blank"}
- [Kommandorad](/help/upgrade/patches/apply.md#command-line)
- [Disposition](/help/upgrade/patches/apply.md#composer)

>[!NOTE]
>
>Information om hur du tillämpar en korrigering på ett Adobe Commerce-infrastrukturprojekt finns i [Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i _Commerce på molnet_.
