---
title: Sökmotorkonfiguration
description: Konfigurera en sökmotor med Adobe Commerce och Magento Open Source.
source-git-commit: 80abb0180fcd8ecc275428c23b68feb5883cbc28
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 0%

---


# Sökmotorkonfiguration

I det här avsnittet beskrivs de minimiinställningar som du måste välja för att testa Elasticsearch eller OpenSearch med Adobe Commerce och Magento Open Source. Från och med version 2.4.4 och 2.4.3-p2 är alla fält märkta **Elasticsearch** gäller även OpenSearch.

Mer information om hur du konfigurerar sökmotorn finns i [Användarhandbok](https://docs.magento.com/user-guide/catalog/search-elasticsearch.html).

## Konfigurera sökmotorn från administratören

Så här konfigurerar du systemet att använda Elasticsearch eller OpenSearch:

1. Logga in på administratören som administratör.
1. Klicka **Lager** > Inställningar > **Konfiguration** > **Katalog** > **Katalog** > **Katalogsökning**.
1. Från **Sökmotor** markera motsvarande version av sökmotorn Om du använder OpenSearch måste du välja Elasticsearch7.

   I följande tabell visas de konfigurationsalternativ som krävs för att konfigurera och testa anslutningen med Commerce.
Om du inte har ändrat serverinställningarna för sökmotorn bör standardinställningarna fungera. Gå till nästa steg.

   | Alternativ | Beskrivning |
   |--- |--- |
   | **Värdnamn för Elasticsearch Server** | Ange det fullständiga värdnamnet eller IP-adressen för datorn som kör Elasticsearch eller OpenSearch.<br>Adobe Commerce om molninfrastruktur: Få ut det här värdet av ditt integreringssystem. |
   | **Elasticsearch Server-port** | Ange webbserverproxyporten. Standardvärdet är 9 200<br>Adobe Commerce om molninfrastruktur: Få ut det här värdet av ditt integreringssystem. |
   | **Elasticsearch-indexprefix** | Ange indexprefixet för sökmotorn. Om du använder en enda instans för mer än en Commerce-installation (mellanlagrings- och produktionsmiljöer) måste du ange ett unikt prefix för varje installation. I annat fall kan du använda standardprefixet magento2. |
   | **Aktivera Elasticsearch HTTP-autentisering** | Klicka **Ja** bara om du har aktiverat autentisering för sökmotorservern. Ange i så fall ett användarnamn och lösenord i de angivna fälten. |

1. Klicka **Testanslutning**.

   Exempelsvar:

   ![framgång](../../assets/configuration/elastic_test-success.png)

   Fortsätt med:

   - [Konfigurera Apache för sökmotorn](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-apache.html)
   - [Konfigurera nginx för sökmotorn](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/es-config-nginx.html)

   eller du ser:

   ![misslyckades](../../assets/configuration/elastic_test-fail.png)

Prova i så fall följande:

- Kontrollera att sökmotorservern körs.
- Om servern finns på en annan värd än Commerce loggar du in på Commerce-servern och pingar sökmotorvärden. Lös problem med nätverksanslutningen och testa anslutningen igen.
- Undersök kommandofönstret där du startade Elasticsearch eller OpenSearch för stackspår och undantag. Du måste lösa dem innan du fortsätter. Kontrollera särskilt att du har startat sökmotorn som en användare med `root` behörighet.
- Se till att [UNIX-brandväggen och SELinux](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/elasticsearch.html#firewall-selinux) är båda inaktiverade eller konfigurerade regler som gör att din sökmotor och Commerce kan kommunicera med varandra.
- Verifiera värdet för **Värdnamn för Elasticsearch Server** fält. Kontrollera att servern är tillgänglig. Du kan testa serverns IP-adress i stället.
- Använd `netstat -an | grep <listen-port>` för att verifiera att porten som anges i **Elasticsearch Server-port** fältet används inte av en annan process.

   Om du till exempel vill se om sökmotorn körs på standardporten använder du följande kommando:

   ```bash
   netstat -an | grep 9200
   ```

   Om den körs på port 9200 visas den på ungefär följande sätt:

   ```terminal
   `tcp        0      0 :::9200            :::-         LISTEN`
   ```

## Indexera om katalogsökning och uppdatera helsidescachen

När du har ändrat sökmotorkonfigurationen måste du indexera om katalogens sökindex och uppdatera helsidescachen med hjälp av Admin eller kommandoraden.

Så här uppdaterar du cachen med hjälp av administratören:

1. Klicka på Admin **System** > **Cachehantering**.
1. Markera kryssrutan bredvid **Sidcache**.
1. Från **Åtgärder** i övre högra hörnet klickar du på **Uppdatera**.

   ![cachehantering](../../assets/configuration/refresh-cache.png)

Så här rensar du cachen med kommandoraden: [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

Så här indexerar du om med kommandoraden:

1. Logga in på din Commerce-server som eller växla till [ägare av filsystem](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html).
1. Ange något av följande kommandon:

   Ange följande kommando om du bara vill indexera om katalogsökindexet:

   ```bash
   bin/magento indexer:reindex catalogsearch_fulltext
   ```

   Ange följande kommando för att indexera om alla indexerare:

   ```bash
   bin/magento indexer:reindex
   ```

1. Vänta tills omindexeringen har slutförts.

   >[!INFO]
   >
   >Till skillnad från cacheminnet uppdateras indexerare av ett cron-jobb. Se till att [cron är aktiverat](../cli/configure-cron-jobs.md) innan du börjar använda sökmotorn.

