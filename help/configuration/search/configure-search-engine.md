---
title: Sökmotorkonfiguration
description: Konfigurera en sökmotor för lokal distribution av Adobe Commerce.
feature: Configuration, Search
exl-id: 61fbe0c2-bdd5-4f57-a518-23e180401804
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '643'
ht-degree: 0%

---

# Sökmotorkonfiguration

I det här avsnittet beskrivs minimiinställningarna som du måste välja för att testa Elasticsearch eller OpenSearch med lokala distributioner av Adobe Commerce.

>[!TIP]
>
>I version 2.4.4 och 2.4.3-p2 gäller alla fält med etiketten **Elasticsearch** även OpenSearch.
>&#x200B;>När stöd för Elasticsearch 8.x introducerades i version 2.4.6 skapades nya etiketter för att skilja mellan Elasticsearch- och OpenSearch-konfigurationer.

Mer information om hur du konfigurerar sökmotorn finns i [användarhandboken](https://experienceleague.adobe.com/docs/commerce-admin/catalog/catalog/search/search-configuration.html?lang=sv-SE).

## Konfigurera sökmotorn från administratören

>[!TIP]
>
>Anvisningar om hur du uppgraderar till en ny version av sökmotorn finns i [Krav för uppgradering](../../upgrade/prepare/prerequisites.md).

Så här konfigurerar du systemet att använda Elasticsearch eller OpenSearch:

1. Logga in på administratören som administratör.
1. Klicka på **[!UICONTROL Stores]** > [!UICONTROL Settings] > **[!UICONTROL Configuration]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog]** > **[!UICONTROL Catalog Search]**.
1. Välj motsvarande version av sökmotorn i listan **[!UICONTROL Search Engine]**.

   I följande tabell visas de alternativ som krävs för att konfigurera och testa anslutningen med Commerce. Om du inte har ändrat serverinställningarna för sökmotorn bör standardinställningarna fungera. Gå till nästa steg.

   | Alternativ | Beskrivning |
   |--- |--- |
   | **[!UICONTROL Server Hostname]** | Ange det fullständiga värdnamnet eller IP-adressen för datorn som kör Elasticsearch eller OpenSearch.<br>Adobe Commerce i molninfrastruktur: Få det här värdet från ditt integreringssystem. |
   | **[!UICONTROL Server Port]** | Ange webbserverproxyporten. Standardvärdet är 9200<br>Adobe Commerce i molninfrastrukturen: Få det här värdet från ditt integreringssystem. |
   | **[!UICONTROL Index Prefix]** | Ange indexprefixet för sökmotorn. Om du använder en enda instans för mer än en Commerce-installation (mellanlagrings- och produktionsmiljöer) måste du ange ett unikt prefix för varje installation. I annat fall kan du använda standardprefixet magento2. |
   | **[!UICONTROL Enable HTTP Auth]** | Klicka bara på **[!UICONTROL Yes]** om du har aktiverat autentisering för sökmotorservern. Ange i så fall ett användarnamn och lösenord i de angivna fälten. |
   | **[!UICONTROL Server Timeout]** | Ange hur lång tid (i sekunder) som du vill vänta när du försöker upprätta en anslutning till Elasticsearch- eller OpenSearch-servern. |

1. Klicka på **[!UICONTROL Test Connection]**.

   Exempelsvar:

   ![lyckades](../../assets/configuration/elastic_test-success.png)

   Fortsätt med:

   - [Konfigurera Apache för sökmotorn](../../installation/prerequisites/search-engine/configure-apache.md)
   - [Konfigurera nginx för sökmotorn](../../installation/prerequisites/search-engine/configure-nginx.md)

   eller du ser:

   ![misslyckades](../../assets/configuration/elastic_test-fail.png)

Prova i så fall följande:

- Kontrollera att sökmotorservern körs.
- Om servern finns på en annan värd än Commerce loggar du in på Commerce-servern och pingar sökmotorvärden. Lös problem med nätverksanslutningen och testa anslutningen igen.
- Undersök det kommandofönster där du startade Elasticsearch eller OpenSearch för stackspår och undantag. Du måste lösa dem innan du fortsätter. Kontrollera särskilt att du har startat sökmotorn som en användare med `root`-behörighet.
- Kontrollera att både [UNIX-brandväggen och SELinux](../../installation/prerequisites/search-engine/overview.md#firewall-and-selinux) är inaktiverade, eller konfigurera regler så att sökmotorn och Commerce kan kommunicera med varandra.
- Verifiera värdet för fältet **[!UICONTROL Server Hostname]**. Kontrollera att servern är tillgänglig. Du kan testa serverns IP-adress i stället.
- Använd kommandot `netstat -an | grep <listen-port>` för att verifiera att porten som anges i fältet **[!UICONTROL Server Port]** inte används av en annan process.

  Om du till exempel vill se om sökmotorn körs på standardporten använder du följande kommando:

  ```bash
  netstat -an | grep 9200
  ```

  Om den körs på port 9200 visas den på ungefär följande sätt:

  ```
  `tcp        0      0 :::9200            :::-         LISTEN`
  ```

## Indexera om katalogsökning och uppdatera helsidescachen

När du har ändrat sökmotorkonfigurationen måste du indexera om katalogens sökindex och uppdatera helsidescachen med hjälp av Admin eller kommandoraden.

Så här uppdaterar du cachen med hjälp av administratören:

1. Klicka på **[!UICONTROL System]** > **[!UICONTROL Cache Management]** i Admin.
1. Markera kryssrutan bredvid **[!UICONTROL Page Cache]**.
1. Klicka på **[!UICONTROL Actions]** Uppdatera **i listan** i det övre högra hörnet.

   ![cachehantering](../../assets/configuration/refresh-cache.png)

Så här rensar du cachen med kommandoraden: [`bin/magento cache:clean`](../cli/manage-cache.md#clean-and-flush-cache-types)

Så här indexerar du om med kommandoraden:

1. Logga in på din Commerce-server som, eller växla till, ägare av [filsystemet](../../installation/prerequisites/file-system/overview.md).
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
   >Till skillnad från cacheminnet uppdateras indexerare av ett cron-jobb. Kontrollera att [kron är aktiverat](../cli/configure-cron-jobs.md) innan du börjar använda sökmotorn.
