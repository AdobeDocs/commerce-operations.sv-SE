---
title: Snabbstart av lokal installation
description: Lär dig hur du installerar Adobe Commerce på din egen infrastruktur med Composer. Upptäck snabbstartssteg och konfigurationskrav.
exl-id: a93476e8-2b30-461a-91df-e73eb1a14d3c
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '964'
ht-degree: 0%

---

# Snabbstart av lokal installation

Instruktionerna på den här sidan beskriver hur du installerar Adobe Commerce på en infrastruktur med självbetjäning. Mer information om hur du uppgraderar en befintlig installation finns i [_uppgraderingshandboken_](../upgrade/overview.md).

Adobe använder [Composer](https://getcomposer.org/) för att hantera Adobe Commerce-komponenter och deras beroenden. Att använda Composer för att hämta Adobe Commerce-metapaketet ger följande fördelar:

- Återanvänd bibliotek från tredje part utan att paketera dem med källkod
- Minska antalet tilläggskonflikter och kompatibilitetsproblem genom att använda en komponentbaserad arkitektur med robust beroendehantering
- Ansluta till standarden [PHP-Framework Interoperability Group (FIG)](https://www.php-fig.org/)
- Paketera om Magento Open Source med andra komponenter
- Använda Adobe Commerce i produktionsmiljö

>[!NOTE]
>
>Utvecklare som bidrar till Magento Open Source bör använda installationsmetoden [git-baserad](https://developer.adobe.com/commerce/contributor/guides/install/) .

## Förutsättningar

Innan du fortsätter måste du göra följande:

- Slutför alla [nödvändiga aktiviteter](system-requirements.md).
- [Installera disposition](https://getcomposer.org/download/).
- Hämta [autentiseringsnycklar](prerequisites/authentication-keys.md) till Adobe Commerce Composer-databasen.

## Logga in som ägare av filsystemet

Läs mer om ägarskap, behörigheter och filsystemets ägare i [Översikt över ägarskap och behörigheter ](prerequisites/file-system/overview.md).

Så här byter du till filsystemets ägare:

1. Logga in på programservern som, eller växla till, en användare med behörighet att skriva till filsystemet.

   Om du använder basskalet kan du använda följande syntax för att växla till filsystemets ägare och ange kommandot samtidigt:

   ```bash
   su <file system owner> -s /bin/bash -c <command>
   ```

   Om filsystemets ägare inte tillåter inloggningar kan du göra följande:

   ```bash
   sudo -u <file system owner>  <command>
   ```

1. Om du vill köra CLI-kommandon från en katalog lägger du till `<app_root>/bin` i systemet `PATH`.

   Eftersom skal har olika syntaxer bör du läsa en referens som [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

   Exempel på basgränssnitt för CentOS:

   ```bash
   export PATH=$PATH:/var/www/html/magento2/bin
   ```

   Du kan också köra kommandona på följande sätt:

   - `cd <app_root>/bin` och kör dem som `./magento <command name>`
   - `app_root>/bin/magento <command name>`
   - `<app_root>` är en underkatalog till webbserverns docroot

## Hämta metapackage

Så här hämtar du Adobe Commerce metapaket:

1. Logga in på programservern som, eller växla till, ägare av [filsystemet](prerequisites/file-system/overview.md).
1. Byt till webbserverns dokumentkatalog eller en katalog som du har konfigurerat som ett virtuellt värddokument.
1. Skapa ett Composer-projekt med ett Commerce-metapaket.

   **Magento Open Source**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Ange dina autentiseringsnycklar när du uppmanas att göra det. Offentliga och privata nycklar skapas och konfigureras från [Commerce Marketplace - Åtkomstnycklar](https://commercemarketplace.adobe.com/customer/account/login/). Kopiera och klistra in värdet för den offentliga nyckeln för `[!UICONTROL username]`. Kopiera och klistra in värdet för den privata nyckeln för `[!UICONTROL password]`.

   >[!NOTE]
   >
   > Om du använder en Composer `[auth.json](https://experienceleague.adobe.com/en/docs/commerce-cloud-service/user-guide/develop/authentication-keys)`-fil eller en systemvariabel som konfigurerats med dina Commerce-autentiseringsnycklar uppmanas du inte att ange autentiseringsnycklar.

   Om du stöter på fel, till exempel `Could not find package...` eller `...no matching package found`, kontrollerar du att det inte finns några stavfel i kommandot. Om du fortfarande råkar ut för fel kanske du inte har behörighet att ladda ned Adobe Commerce. Kontakta [Adobe Commerce Support](https://support.magento.com/hc/en-us) om du behöver hjälp.

   Se [Felsökning](https://support.magento.com/hc/en-us/articles/360033818091) om du behöver hjälp med fler fel.

### Exempel - Mindre version

Mindre releaser innehåller nya funktioner, kvalitetskorrigeringar och säkerhetskorrigeringar. Använd Composer för att ange en mindre release. Om du till exempel vill ange metapaketet för Adobe Commerce 2.4.6:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### Exempel - Kvalitetskorrigering

Kvalitetsuppdateringar innehåller i första hand funktionella _- och_-säkerhetskorrigeringar. De kan dock ibland även innehålla nya bakåtkompatibla funktioner. Använd Composer för att hämta en kvalitetskorrigering. Om du till exempel vill ange metapaketet för Adobe Commerce 2.4.6:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6 <install-directory-name>
```

### Exempel - Säkerhetsuppdatering

Säkerhetsuppdateringar innehåller endast säkerhetskorrigeringar. De är utformade för att göra uppgraderingsprocessen snabbare och enklare.

Säkerhetsuppdateringar använder Composer-namnkonventionen `2.4.6-px`. Använd Composer för att ange en korrigering. Om du till exempel vill hämta metapaketet Adobe Commerce 2.4.6-p1:

```bash
composer create-project --repository-url=https://repo.magento.com/ magento/project-enterprise-edition=2.4.6-p1 <install-directory-name>
```

## Ange filbehörigheter

Du måste ange läs- och skrivbehörighet för webbservergruppen innan du installerar Adobe Commerce. Detta är nödvändigt för att kommandoraden ska kunna skriva filer till filsystemet.

```bash
cd /var/www/html/<magento install directory>
find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
chown -R :www-data . # Ubuntu
chmod u+x bin/magento
```

## Installera programmet

Du måste använda kommandoraden för att installera Adobe Commerce.

I det här exemplet antas att installationskatalogen har namnet `magento2ee`, att `db-host` finns på samma dator (`localhost`) och att `db-name`, `db-user` och `db-password` alla är `magento`:

```bash
bin/magento setup:install \
--base-url=http://localhost/magento2ee \
--db-host=localhost \
--db-name=magento \
--db-user=magento \
--db-password=magento \
--admin-firstname=admin \
--admin-lastname=admin \
--admin-email=admin@admin.com \
--admin-user=admin \
--admin-password=admin123 \
--language=en_US \
--currency=USD \
--timezone=America/Chicago \
--use-rewrites=1 \
--search-engine=opensearch \
--opensearch-host=os-host.example.com \
--opensearch-port=9200 \
--opensearch-index-prefix=magento2 \
--opensearch-timeout=15
```

>[!TIP]
>
>Du kan anpassa Admin URI med alternativet `--backend-frontname`. Adobe rekommenderar dock att du utelämnar det här alternativet och låter installationskommandot automatiskt generera en slumpmässig URI. En slumpmässig URI är svårare för hackare eller skadlig programvara att utnyttja. URI:n visas i konsolen när installationen är klar.

>[!TIP]
>
>En fullständig beskrivning av CLI-installationsalternativen finns i [Installera programmet från kommandoraden](advanced.md).

## Sammanfattning av kommandon

Om du vill visa en fullständig lista med kommandon anger du:

```bash
bin/magento list
```

Om du vill ha hjälp för ett visst kommando anger du:

```bash
bin/magento help <command>
```

Exempel:

```bash
bin/magento help setup:install
```

```bash
bin/magento help cache:enable
```

Följande tabell sammanfattar de tillgängliga kommandona. Kommandon visas endast i sammanfattningsform. Mer information om ett kommando får du om du klickar på länken i kolumnen Kommando.

| Kommando | Beskrivning | Förutsättningar |
|--- |--- |--- |
| `magento setup:install` | Installerar programmet | Ingen |
| `magento setup:uninstall` | Tar bort programmet. | Programmet är installerat |
| `magento setup:upgrade` | Uppdaterar programmet. | Distributionskonfiguration |
| `magento maintenance:{enable/disable}` | Aktiverar eller inaktiverar underhållsläge (i underhållsläge kan bara undantagna IP-adresser komma åt Admin eller storefront). | Programmet är installerat |
| `magento setup:config:set` | Skapar eller uppdaterar distributionskonfigurationen. | Ingen |
| `magento module:{enable/disable}` | Aktivera eller inaktivera moduler. | Ingen |
| `magento setup:store-config:set` | Anger alternativ som är relaterade till butiken, till exempel bas-URL, språk och tidszon. | Distributionskonfiguration |
| `magento setup:db-schema:upgrade` | Uppdaterar databasschemat. | Distributionskonfiguration |
| `magento setup:db-data:upgrade` | Uppdaterar databasdata. | Distributionskonfiguration |
| `magento setup:db:status` | Kontrollerar om databasen är uppdaterad med koden. | Distributionskonfiguration |
| `magento admin:user:create` | Skapar en administratör. | Du kan skapa användare för följande:<br><br>Distributionskonfiguration<br><br>Aktivera minst databasen `Magento_User` och `Magento_Authorization` modules<br><br>(enklaste sättet är att använda `bin/magento setup:upgrade`) |
| `magento list` | Visar alla tillgängliga kommandon. | Ingen |
| `magento help` | Tillhandahåller hjälp för det angivna kommandot. | Ingen |

### Vanliga argument

Följande argument är gemensamma för alla kommandon. Dessa kommandon kan köras antingen före eller efter att programmet har installerats:

| Lång version | Kort version | Betydelse |
|--- |--- |--- |
| `--help` | `-h` | Få hjälp för alla kommandon. Till exempel `./magento help setup:install` eller `./magento help setup:config:set`. |
| `--quiet` | `-q` | Tyst läge, inga utdata. |
| `--no-interaction` | `-n` | Inga interaktiva frågor. |
| `--verbose=1,2,3` | `-v, -vv, -vvv` | Detaljnivå. `--verbose=3` eller `-vvv` visar till exempel felsökningsintensiteten, som är den mest detaljerade utdata. Standardvärdet är `--verbose=1` eller `-v`. |
| `--version` | `-V` | Visa den här programversionen |
| `--ansi` | n/a | Framtvinga ANSI-utdata |
| `--no-ansi` | n/a | Inaktivera ANSI-utdata |

>[!NOTE]
>
>Grattis! Du har slutfört snabbinstallationen. Behöver du mer avancerad hjälp? Ta en titt på guiden [Avancerad installation](advanced.md).
