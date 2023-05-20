---
title: Aktivera eller inaktivera underhållsläge
description: Följ de här stegen för att anpassa vad kunderna ser när driftsättningen av Adobe Commerce eller Magento Open Source är nere för underhåll.
exl-id: 5d9f1493-e771-47b4-b906-3771026cf07a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---

# Aktivera eller inaktivera underhållsläge

Följande guide hänvisar till en standardsida för underhållsläge. Om du behöver använda en anpassad underhållssida finns mer information i [Skapa den anpassade underhållssidan](../../upgrade/troubleshooting/maintenance-mode-options.md) ämne.

Adobe Commerce och Magento Open Source använder [underhållsläge](../../configuration/bootstrap/application-modes.md#maintenance-mode) för att inaktivera startspärr. Det är praktiskt att inaktivera startfunktionen när du underhåller, uppgraderar eller konfigurerar om platsen.

Programmet identifierar underhållsläge enligt följande:

* If `var/.maintenance.flag` finns inte, underhållsläget är inaktiverat och programmet fungerar normalt.
* Annars är underhållsläget aktiverat om inte `var/.maintenance.ip` finns.

   `var/.maintenance.ip` kan innehålla en lista med IP-adresser. Om en startpunkt nås via HTTP och klientens IP-adress motsvarar en av posterna i listan, är underhållsläget inaktiverat.

## Installera programmet

Innan du använder det här kommandot för att aktivera eller inaktivera underhållsläge måste du [installera programmet](../advanced.md).

## Aktivera eller inaktivera underhållsläge

Använd `magento maintenance` CLI-kommando för att aktivera eller inaktivera underhållsläge.

Kommandoanvändning:

```bash
bin/magento maintenance:enable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:disable [--ip=<ip address> ... --ip=<ip address>] | [ip=none]
```

```bash
bin/magento maintenance:status
```

The `--ip=<ip address>` option är en IP-adress som ska undantas från underhållsläge (till exempel utvecklare som utför underhållet). Om du vill undanta mer än en IP-adress i samma kommando använder du alternativet flera gånger.

>[!NOTE]
>
>Använda `--ip=<ip address>` med `magento maintenance:disable` sparar listan över IP-adresser för senare bruk. Om du vill rensa listan över undantagna IP-adresser använder du `magento maintenance:enable --ip=none` eller se [Underhåll listan över undantagna IP-adresser](#maintain-the-list-of-exempt-ip-addresses).

The `bin/magento maintenance:status` kommandot visar status för underhållsläge.

Om du till exempel vill aktivera underhållsläge utan undantag för IP-adresser:

```bash
bin/magento maintenance:enable
```

Så här aktiverar du underhållsläge för alla klienter utom 192.0.2.10 och 192.0.2.11:

```bash
bin/magento maintenance:enable --ip=192.0.2.10 --ip=192.0.2.11
```

När du har placerat programmet i underhållsläge måste du stoppa alla konsumentprocesser i meddelandekön.
Ett sätt att hitta dessa processer är att köra `ps -ef | grep queue:consumers:start` och sedan köra `kill <process_id>` för varje konsument. I en miljö med flera noder upprepar du den här uppgiften på varje nod.

## Underhåll listan över undantagna IP-adresser

Om du vill behålla listan över undantagna IP-adresser kan du antingen använda `[--ip=<ip list>]` i föregående kommandon eller så kan du använda följande:

```bash
bin/magento maintenance:allow-ips <ip address> .. <ip address> [--none]
```

The `<ip address> .. <ip address>` är en valfri, utrymmesavgränsad lista över IP-adresser som ska undantas.

The `--none` alternativet rensar listan.

## Inställningar för flera butiker

<!-- To set up multiple stores, each with a different layout and localized content, create a skin for each and put it into `pub/errors/{name}` where `{name}` is the store code. To distinguish between stores and websites with the same instance, use `pub/errors/{type}-{name}` where `{type}` is either `store` or `website` and matches the `MAGE_RUN_TYPE` in your server configuration. Another option is to pass the `$_GET['skin']` parameter to the intended processor. This method requires a specific configuration on your server. -->
<!-- Replace the line below with the commented text after https://github.com/magento/magento2/pull/35095 is merged. -->

Om du vill skapa flera butiker, var och en med olika layouter och lokaliserat innehåll, skickar du `$_GET['skin']` -parametern till den avsedda processorn.

I följande exempel använder vi en `503` skriv error template file, som kräver lokaliserat innehåll.

Konstruktorn för `Error_Processor` klassen godkänner `skin` GET-parameter för att ändra layout:

```php
if (isset($_GET['skin'])) {
    $this->_setSkin($_GET['skin']);
}
```

Detta kan också läggas till i en omskrivningsregel i `.htaccess` fil som lägger till en `skin` parametern till URL:en.

### $_GET[&#39;skin&#39;] parameter

Så här använder du `skin` parameter:

1. Kontrollera om `.maintenance.flag` finns.
1. Observera värdadressen som refererar till `HTTP_HOST`eller andra variabler som ENV-variabler.
1. Kontrollera om `skin` parametern finns.
1. Ange parametern med hjälp av reglerna för omskrivning nedan.

   Här är några exempel på skrivregler:

   * RewriteCond `%{DOCUMENT_ROOT}/var/.maintenance.flag -f`
   * RewriteCond `%{HTTP_HOST} ^sub.example.com$`
   * RewriteCond `%{QUERY_STRING} !(^|&)skin=sub(&|$)` [NC]
   * RewriteRule `^ %{REQUEST_URI}?skin=sub` [L]

1. Kopiera följande filer:

   * `pub/errors/default/503.phtml` till `pub/errors/sub/503.phtml`
   * `pub/errors/default/css/styles.css` till `pub/errors/sub/styles.css`

1. Redigera dessa filer för att tillhandahålla lokaliserat innehåll i `503.phtml` -fil och egen formatering i `styles.css` -fil.

   Se till att dina sökvägar pekar mot `errors` katalog. Katalognamnet måste matcha URL-parametern som anges i `RewriteRule`. I föregående exempel `sub` används, vilket anges som en parameter i `RewriteRule` (`skin=sub`)

>[!NOTE]
>
>The [nginx](../../configuration/multi-sites/ms-nginx.md) inställningen måste läggas till för flerlagringsinställningar.
