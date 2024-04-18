---
title: Avancerad lokal installation
description: Lär dig mer om avancerade installationsscenarier för Adobe Commerce för infrastruktur som du äger.
exl-id: e16e750a-e068-4a63-8ad9-62043e2a8231
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '2314'
ht-degree: 0%

---

# Avancerad lokal installation

>[!TIP]
>
>Förlorad? Behöver du hjälp? Prova vår [Snabbstart](composer.md) eller [Contributor-installation](https://developer.adobe.com/commerce/contributor/guides/install/) stödlinjer.

>[!NOTE]
>
>Om du väljer att aktivera SELinux finns mer information i [SELinux och iptables](prerequisites/security.md).

## Kommandoradsgränssnitt (CLI)

Adobe Commerce har ett enda kommandoradsgränssnitt för installations- och konfigureringsuppgifter: `<magento_root>/bin/magento`. Gränssnittet utför flera uppgifter, bland annat:

* Installation (och relaterade uppgifter som att skapa eller uppdatera databasschemat och skapa distributionskonfigurationen).
* Rensar cachen.
* Hantera index, inklusive omindexering.
* Skapa översättningsordlistor och översättningspaket.
* Generera obefintliga klasser som fabriker och spärrar för plugin-program och generera konfigurationen för beroendeinjicering för objekthanteraren.
* Distribuera statiska vyfiler.
* Skapa CSS från mindre.

Andra fördelar:

* Ett enda kommando (`<magento_root>/bin/magento list`) listar alla tillgängliga installations- och konfigurationskommandon.
* Enhetligt användargränssnitt baserat på Symfoni.
* CLI är utbyggbart så att tredjepartsutvecklare kan&quot;ansluta&quot; till det. Detta innebär också att man slipper inlärningskurva.
* Kommandon för inaktiverade moduler visas inte.

I det här avsnittet diskuteras hur du installerar Adobe Commerce-programmet med CLI. Mer information om konfiguration finns i [Konfigurationshandbok](../configuration/overview.md).

Installationsprogrammet kan köras flera gånger om det behövs så att du kan:

* Ange olika värden

  När du har konfigurerat webbservern för SSL (Secure Sockets Layer) kan du köra installationsprogrammet och ange SSL-alternativ.

* Åtgärda fel i tidigare installationer
* Installera Adobe Commerce i en annan databasinstans

## Innan du startar installationen

Utför följande steg innan du börjar:

* Verifiera att systemet uppfyller de krav som beskrivs i [systemkrav](system-requirements.md).

* Slutför alla [krav](prerequisites/overview.md) uppgifter.

* Slutför de första installationsstegen. Se [din installations- eller uppgraderingssökväg](overview.md).

* När du har loggat in på programservern [växla till filsystemets ägare](prerequisites/file-system/overview.md).

* Granska [snabbstart för installation](composer.md) översikt.

>[!NOTE]
>
>Du måste installera Adobe Commerce från `bin` underkatalog.

Du kan köra installationsprogrammet flera gånger med olika alternativ för att slutföra installationsåtgärder som följande:

* Installera i faser - När du till exempel har konfigurerat webbservern för SSL (Secure Sockets Layer) kan du köra installationsprogrammet igen och ange SSL-alternativ.

* Åtgärda fel i tidigare installationer.

* Installera Adobe Commerce i en annan databasinstans.

>[!NOTE]
>
>Installationsprogrammet skriver som standard inte över databasen om du installerar programmet i samma databasinstans. Du kan använda det valfria `cleanup-database` parameter för att ändra detta beteende.

Se även [Uppdatera, installera om, avinstallera](tutorials/uninstall.md).

### Säker installation

{{$include /help/_includes/secure-install.md}}

## Hjälpkommandon för installationsprogrammet

Du kan köra följande kommandon för att hitta värden för vissa obligatoriska argument:

| Installationsargument | Kommando |
| ------------------ | ------------------------------- |
| Språk | `bin/magento info:language:list` |
| Valuta | `bin/magento info:currency:list` |
| Tidszon | `bin/magento info:timezone:list` |

>[!NOTE]
>
>Om ett fel visas när du kör dessa kommandon kontrollerar du att du har uppdaterat installationsberoenden enligt beskrivningen i [Uppdatera installationsberoenden](https://developer.adobe.com/commerce/contributor/guides/install/update-dependencies/).

## Installera från kommandoraden

Installationskommandot har följande format:

```bash
bin/magento setup:install --<option>=<value> ... --<option>=<value>
```

I följande tabeller beskrivs namnen och värdena för installationsalternativen. Installationskommandon finns i [Exempel på lokala värdinstallationer](#sample-localhost-installations).

>[!NOTE]
>
>Alla alternativ som innehåller blanksteg eller specialtecken måste omslutas med enkla eller dubbla citattecken.

**Administratörsreferenser:**

Följande alternativ anger användarinformation och autentiseringsuppgifter för Admin-användaren.

Du kan skapa Admin-användaren under eller efter installationen. Om du skapar användaren under installationen krävs alla autentiseringsuppgifter för administratörer. Se [Exempel på lokala värdinstallationer](#sample-localhost-installations).

Följande tabeller innehåller många men inte alla tillgängliga installationsparametrar. En fullständig lista finns i [Referens för kommandoradsverktyg](https://devdocs.magento.com/guides/v2.4/reference/cli/magento.html).

| Namn | Värde | Obligatoriskt? |
|--- |--- |--- |
| `--admin-firstname` | Administratörsanvändarens förnamn. | Ja |
| `--admin-lastname` | Administratörsanvändarens efternamn. | Ja |
| `--admin-email` | Administratörsanvändarens e-postadress. | Ja |
| `--admin-user` | Administratörsanvändarnamn. | Ja |
| `--admin-password` | Administratörslösenord. Lösenordet måste innehålla minst 7 tecken och innehålla minst en bokstav och minst ett numeriskt tecken. Vi rekommenderar ett längre och mer komplext lösenord. Omsluter hela lösenordssträngen med enkla citattecken. Exempel: `--admin-password='A0b9%t3g'` | Ja |

**Konfigurationsalternativ för plats och databas:**

| Namn | Värde | Obligatoriskt? |
|--- |--- |--- |
| `--base-url` | Bas-URL som används för att komma åt din administratör och butiker i något av följande format:<br><br>`http[s]://<host or ip>/<your install dir>/`.<br><br>**Obs!** Schemat (http:// eller https://) och ett avslutande snedstreck krävs båda.<br><br>`<your install dir>` är den dokumentrelativa sökvägen där Adobe Commerce-programmet ska installeras. Beroende på hur du konfigurerar webbservern och de virtuella värdarna kan sökvägen vara magento2 eller tom.<br><br>För att få tillgång till Adobe Commerce eller MagenAdobe Commerce använder du antingen `http://127.0.0.1/<your install dir>/` eller `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` som representerar en bas-URL som definieras av en virtuell värdinställning eller av en virtualiseringsmiljö som Docker. Om du till exempel konfigurerar en virtuell värd med värdnamnet `magento.example.com`kan du installera programmet med `--base-url={{base_url}}` och få åtkomst till Admin via en URL som `http://magento.example.com/admin`. | Ja |
| `--backend-frontname` | URI (Uniform Resource Identifier) för åtkomst till administratören. Du kan utelämna den här parametern så att programmet kan generera en slumpmässig URI med följande mönster <code>admin_jkhgdfq</code>.<br><br>Vi rekommenderar en slumpmässig URI av säkerhetsskäl. En slumpmässig URI är svårare för hackare eller skadlig programvara att utnyttja.<br><br>URI:n visas i slutet av installationen. Du kan när som helst visa den senare med `bin/magento info:adminuri` -kommando.<br><br>Om du väljer att ange ett värde rekommenderar vi att du inte använder ett vanligt ord som admin, serverdel. Admin-URI kan innehålla alfanumeriska värden och understreck (`_`). | Nej |
| `--db-host` | Använd något av följande:<br><br>- Databasserverns kvalificerade värdnamn eller IP-adress.<br><br>- `localhost` (standard) eller `127.0.0.1` om databasservern finns på samma värd som webbservern.localhost betyder att MySQL-klientbiblioteket använder UNIX-socketar för att ansluta till databasen. `127.0.0.1` gör att klientbiblioteket använder TCP-protokollet. Mer information om socketar finns i [PHP-SUB_MYSQL-dokumentation](https://www.php.net/manual/en/ref.pdo-mysql.php).<br><br>**Obs!** Du kan också ange databasserverporten i värdnamnet som www.example.com:9000 | Ja |
| `--db-name` | Namnet på den databasinstans där du vill installera databastabellerna.<br><br>Standard är `magento2`. | Ja |
| `--db-user` | Användarnamn för databasinstansens ägare.<br><br>Standard är `root`. | Ja |
| `--db-password` | Lösenord för databasinstansens ägare. | Ja |
| `--db-prefix` | Använd bara om du installerar databastabellerna i en databasinstans som redan innehåller Adobe Commerce-tabeller.<br><br>I så fall använder du ett prefix för att identifiera tabellerna för den här installationen. Vissa kunder har mer än en Adobe Commerce- eller MagenAdobe Commerver-server med alla tabeller i samma databas.<br><br>Prefixet får innehålla högst fem tecken. Den måste börja med en bokstav och kan bara innehålla bokstäver, siffror och understreck.<br><br>Med det här alternativet kan dessa kunder dela databasservern med mer än en Adobe Commerce-installation |
| `--db-ssl-key` | Sökväg till klientnyckeln. | Nej |
| `--db-ssl-cert` | Sökväg till klientcertifikatet. | Nej |
| `--db-ssl-ca` | Sökväg till servercertifikatet. | Nej |
| `--language` | Språkkod som ska användas i Admin och storefront. (Om du inte redan har gjort det kan du visa listan med språkkoder genom att ange `bin/magento info:language:list` från bin-katalogen.) | Nej |
| `--currency` | Standardvaluta som ska användas i butiken. (Om du inte redan har gjort det kan du visa listan över valutor genom att ange `bin/magento info:currency:list` från bin-katalogen.) | Nej |
| `--timezone` | Standardtidszon att använda i Admin och storefront. (Om du inte redan har gjort det kan du visa listan över tidszoner genom att ange `bin/magento info:timezone:list` från `bin/` katalog.) | Nej |
| `--use-rewrites` | `1` innebär att du använder webbserveromskrivningar för genererade länkar i butiken och Admin.<br><br>`0` Inaktiverar användning av omskrivningar från webbservrar. Det här är standardinställningen. | Nej |
| `--use-secure` | `1` används för att använda SSL (Secure Sockets Layer) i butiks-URL:er. Kontrollera att webbservern stöder SSL innan du väljer det här alternativet.<br><br>`0` inaktiverar användningen av SSL. I det här fallet antas alla andra säkra URL-alternativ också vara 0. Det här är standardinställningen. | Nej |
| `--base-url-secure` | Säker bas-URL som används för att komma åt din administratör och butiker i följande format: `http[s]://<host or ip>/<your install dir>/` | Nej |
| `--use-secure-admin` | `1` innebär att du använder SSL för att komma åt administratören. Kontrollera att webbservern stöder SSL innan du väljer det här alternativet.<br><br>`0` betyder att du inte använder SSL med administratören. Det här är standardinställningen. | Nej |
| `--admin-use-security-key` | 1 gör att programmet använder ett slumpmässigt genererat nyckelvärde för att få åtkomst till sidor i Admin och i formulär. Dessa nyckelvärden hjälper till att förhindra attacker med förfalskade korsskriptattacker mellan webbplatser. Det här är standardinställningen.<br><br>`0` inaktiverar användningen av nyckeln. | Nej |
| `--session-save` | Använd något av följande:<br><br>- `db` för att lagra sessionsdata i databasen. Välj databaslagring om du har en klustrad databas, annars kanske det inte finns någon större fördel jämfört med filbaserad lagring.<br><br>- `files` för att lagra sessionsdata i filsystemet. Filbaserad sessionslagring är lämplig om inte filsystemåtkomsten är långsam, du har en klustrad databas eller du vill lagra sessionsdata i Redis.<br><br>- `redis` för att lagra sessionsdata i Redis. Om du använder Redis som standard- eller sidcache-lagring måste Redis vara installerat. Mer information om hur du konfigurerar stöd för Redis finns i Använda Redis för sessionslagring. | Nej |
| `--key` | Om du har ett, anger du en nyckel för att kryptera känsliga data i databasen. Om du inte har någon skapar programmet en åt dig. | Ja |
| `--cleanup-database` | Om du vill släppa databastabeller innan du installerar Adobe Commerce anger du den här parametern utan ett värde. Annars lämnas databasen intakt. | Nej |
| `--db-init-statements` | Avancerad MySQL-konfigurationsparameter. Använder databasinitieringssatser som ska köras vid anslutning till MySQL-databasen. Läs en referens som liknar den här innan du anger några värden.<br><br>Standard är `SET NAMES utf8;`. | Nej |
| `--sales-order-increment-prefix` | Ange ett strängvärde som ska användas som prefix för försäljningsorder. Vanligtvis används detta för att garantera unika ordernummer för betalningsprocessorer. | Nej |

**Konfigurationsalternativ för sökmotor:**

| Namn | Värde | Obligatoriskt? |
|--- |--- |--- |
| `--search-engine` | Den version av Elasticsearch eller OpenSearch som ska användas som sökmotor. Standardvärdet är `elasticsearch7`. Elasticsearch 5 har tagits bort och rekommenderas inte. | Nej |
| `--elasticsearch-host` | Värdnamnet eller IP-adressen där Elasticsearch körs. Standardvärdet är `localhost`. | Nej |
| `--elasticsearch-port` | Elasticsearch-porten för inkommande HTTP-begäranden. Standardvärdet är `9200`. | Nej |
| `--elasticsearch-index-prefix` | Ett prefix som identifierar sökindexet för Elasticsearch. Standardvärdet är `magento2`. | Nej |
| `--elasticsearch-timeout` | Antalet sekunder innan systemet timeout. Standardvärdet är `15`. | Nej |
| `--elasticsearch-enable-auth` | Aktiverar autentisering på Elasticsearch-servern. Standardvärdet är `false`. | Nej |
| `--elasticsearch-username` | Användar-ID för autentisering till Elasticsearch-servern. | Nej, om inte autentisering är aktiverat |
| `--elasticsearch-password` | Lösenordet som ska autentiseras på Elasticsearch-servern. | Nej, om inte autentisering är aktiverat |
| `--opensearch-host` | Värdnamnet eller IP-adressen där OpenSearch körs. Standardvärdet är `localhost`. | Nej |
| `--opensearch-port` | OpenSearch-porten för inkommande HTTP-begäranden. Standardvärdet är `9200`. | Nej |
| `--opensearch-index-prefix` | Ett prefix som identifierar OpenSearch-sökindexet. Standardvärdet är `magento2`. | Nej |
| `--opensearch-timeout` | Antalet sekunder innan systemet timeout. Standardvärdet är `15`. | Nej |
| `--opensearch-enable-auth` | Aktiverar autentisering på OpenSearch-servern. Standardvärdet är `false`. | Nej |
| `--opensearch-username` | Användar-ID:t som ska autentiseras på OpenSearch-servern. | Nej, om inte autentisering är aktiverat |
| `--opensearch-password` | Lösenordet som ska autentiseras på OpenSearch-servern. | Nej, om inte autentisering är aktiverat |

**[!DNL RabbitMQ]konfigurationsalternativ:**

| Namn | Värde | Obligatoriskt? |
|--- |--- |--- |
| `--amqp-host` | Använd inte `--amqp` om du inte redan har konfigurerat en installation av [!DNL RabbitMQ]. Se [!DNL RabbitMQ] för mer information om installation och konfigurering [!DNL RabbitMQ].<br><br>Värdnamnet där [!DNL RabbitMQ] är installerat. | Nej |
| `--amqp-port` | Porten som ska användas för att ansluta till [!DNL RabbitMQ]. Standardvärdet är 5672. | Nej |
| `--amqp-user` | Användarnamn för anslutning till [!DNL RabbitMQ]. Använd inte standardanvändaren `guest`. | Nej |
| `--amqp-password` | Lösenordet för att ansluta till [!DNL RabbitMQ]. Använd inte standardlösenordet `guest`. | Nej |
| `--amqp-virtualhost` | Det virtuella värdsystemet för anslutning till [!DNL RabbitMQ]. Standardvärdet är `/`. | Nej |
| `--amqp-ssl` | Anger om anslutning ska ske till [!DNL RabbitMQ]. Standardvärdet är `false`. Se [!DNL RabbitMQ] för information om hur du konfigurerar SSL för [!DNL RabbitMQ]. | Nej |
| `--consumers-wait-for-messages` | Ska konsumenterna vänta på ett meddelande från kön? 1 - Ja, 0 - Nej | Nej |

**Lås konfigurationsalternativ:**

| Namn | Värde | Obligatoriskt? |
|--- |--- |--- |
| `--lock-provider` | Lås leverantörens namn.<br><br>Tillgängliga låsleverantörer: `db`, `zookeeper`, `file`.<br><br>Standardlåsleverantör: `db` | Nej |
| `--lock-db-prefix` | Det specifika db-prefixet för att undvika låskonflikter när du använder `db` låsleverantör.<br><br>Standardvärdet: `NULL` | Nej |
| `--lock-zookeeper-host` | Värd och port för att ansluta till Zookeeper-klustret när du använder `zookeeper` låsleverantör.<br><br>Till exempel: `127.0.0.1:2181` | Ja, om du anger `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Sökvägen där Zookeeper sparar lås.<br><br>Standardsökvägen är: `/magento/locks` | Nej |
| `--lock-file-path` | Sökvägen där fillås sparas. | Ja, om du anger `--lock-provider=file` |

**Konfigurationsalternativ för konsumenter:**

{{$include /help/_includes/cli-consumers.md}}

>[!NOTE]
>
>Information om hur du aktiverar eller inaktiverar moduler efter installation av Adobe Commerce finns i [Aktivera och inaktivera moduler](tutorials/manage-modules.md).

**Känsliga data:**

{{$include /help/_includes/sensitive-data.md}}

### Exempel på lokala värdinstallationer

I följande exempel visas kommandon för att installera Adobe Commerce lokalt med olika alternativ.

#### Exempel 1 - Grundinstallation med administratörsanvändarkonto

I följande exempel installeras Adobe Commerce med följande alternativ:

* Programmet installeras i `magento2` katalog relativt webbserverns dokumentrot på `localhost` och sökvägen till administratören är `admin`; därför

  Din butiks-URL är `http://127.0.0.1`

* Databasservern finns på samma värd som webbservern.

  Databasnamnet är `magento`och både användarnamn och lösenord `magento`

* Använder serveromskrivning

* Administratören har följande egenskaper:

   * För- och efternamn är `Magento User`
   * Användarnamnet är `admin` och lösenordet är `admin123`
   * E-postadressen är `user@example.com`

* Standardspråket är `en_US` (på eng)
* Standardvalutan är amerikanska dollar
* Standardtidszonen är USA Central (America/Chicago)
* OpenSearch 1.2 är installerat på `os-host.example.com` och ansluts till port 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

Meddelanden som liknar följande för att ange att installationen lyckades:

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

#### Exempel 2 - Grundinstallation utan administratörsanvändarkonto

Du kan installera Adobe Commerce utan att skapa administratörsanvändaren, vilket visas i följande exempel.

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--language=en_US --currency=USD --timezone=America/Chicago --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

Meddelanden som följande om installationen lyckas:

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```

Efter installationen kan du skapa en administratörsanvändare med `admin:user:create` kommando:
[Skapa eller redigera en administratör](tutorials/admin.md#create-or-edit-an-administrator)

#### Exempel 3 - Installera med ytterligare alternativ

I följande exempel installeras Adobe Commerce med följande alternativ:

* Programmet installeras i `magento2` katalog relativt webbserverns dokumentrot på `localhost` och sökvägen till administratören är `admin`; därför

  Din butiks-URL är `http://127.0.0.1`

* Databasservern finns på samma värd som webbservern.

  Databasnamnet är `magento`och både användarnamn och lösenord `magento`

* Administratören har följande egenskaper:

   * För- och efternamn är `Magento User`
   * Användarnamnet är `admin` och lösenordet är `admin123`
   * E-postadressen är `user@example.com`

* Standardspråket är `en_US` (på eng)
* Standardvalutan är amerikanska dollar
* Standardtidszonen är USA Central (America/Chicago)
* Installationsprogrammet rensar först databasen innan tabellerna och schemat installeras
* Du kan använda prefixet för ökning av försäljningsorder `ORD$` (eftersom det innehåller ett specialtecken [`$`]måste värdet omges av citattecken)
* Sessionsdata sparas i databasen
* Använder serveromskrivning
* OpenSearch är installerat på `os-host.example.com` och ansluts till port 9200

```bash
magento setup:install --base-url=http://127.0.0.1/magento2/ \
--db-host=localhost --db-name=magento --db-user=magento --db-password=magento \
--admin-firstname=Magento --admin-lastname=User --admin-email=user@example.com \
--admin-user=admin --admin-password=admin123 --language=en_US \
--currency=USD --timezone=America/Chicago --cleanup-database \
--sales-order-increment-prefix="ORD$" --session-save=db --use-rewrites=1 \
--search-engine=opensearch --opensearch-host=os-host.example.com \
--opensearch-port=9200
```

>[!NOTE]
>
>Du måste ange kommandot antingen på en rad eller, som i föregående exempel, med ett `\` i slutet av varje rad.

Meddelanden som följande om installationen lyckas:

```terminal
Post installation file permissions check...
For security, remove write permissions from these directories: '/var/www/html/magento2/app/etc'
[Progress: 274 / 274]
[SUCCESS]: Magento installation complete.
[SUCCESS]: Admin Panel URI: /admin_puu71q
```
