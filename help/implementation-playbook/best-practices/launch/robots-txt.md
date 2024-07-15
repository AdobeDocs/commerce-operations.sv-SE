---
title: Bästa tillvägagångssätt för att konfigurera webbcrawler
description: Lär dig hur du skickar instruktioner om din Adobe Commerce-webbplats till webbcrawler med hjälp av filerna robots.txt och sitemap.xml.
role: Developer
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: e1e7ad76b1df8e920ab7f9740fd4be8dc7335954
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---


# Bästa tillvägagångssätt för att konfigurera webbcrawler

Den här artikeln innehåller tips om hur du använder `robots.txt`- och `sitemap.xml`-filer i Adobe Commerce, inklusive konfiguration och säkerhet. De här filerna instruerar webbcrawlningar (oftast robotar för sökmotorer) hur du crawlar sidor på en webbplats. Om du konfigurerar dessa filer kan webbplatsens prestanda förbättras och sökmotoroptimeringen förbättras.

>[!NOTE]
>
>De bästa sätten är att använda i projekt som endast använder den inbyggda Adobe Commerce Store. De gäller inte för Adobe Commerce-projekt som använder andra butikslösningar (till exempel Adobe Experience Manager, headless).

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Adobe Commerce i molninfrastruktur

Ett Adobe Commerce-standardprojekt innehåller en hierarki som innehåller en webbplats-, butiks- och butiksvy. För mer komplexa implementeringar kan du skapa ytterligare webbplatser, butiker och butiksvyer för en _multi-site_ -butik.

### Butiker för en webbplats

Följ dessa metodtips när du konfigurerar `robots.txt`- och `sitemap.xml`-filer för butiker med en plats:

- Kontrollera att ditt projekt använder [`ece-tools`](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) version 2002.0.12 eller senare.
- Använd administratörsprogrammet för att lägga till innehåll i filen `robots.txt`.

  >[!TIP]
  >
  >Visa den automatiskt genererade `robots.txt`-filen för din butik på `<domain.your.project>/robots.txt`.

- Använd administratörsprogrammet för att generera en `sitemap.xml`-fil.

  >[!IMPORTANT]
  >
  >På grund av det skrivskyddade filsystemet på Adobe Commerce i molninfrastrukturprojekt måste du ange sökvägen `pub/media` innan du genererar filen.

- Använd ett anpassat fast VCL-fragment för att omdirigera från platsens rot till platsen `pub/media/` för båda filerna:

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
  }
  ```

- Testa omdirigeringen genom att visa filerna i en webbläsare. Till exempel `<domain.your.project>/robots.txt` och `<domain.your.project>/sitemap.xml`. Se till att du använder rotsökvägen som du konfigurerade omdirigeringen för och inte en annan sökväg.

>[!INFO]
>
>Mer information finns i [Lägg till webbplatskarta och sökrobotar](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html).


### Lagringsplatser för flera platser

Du kan konfigurera och köra flera butiker med en enda implementering av Adobe Commerce i molninfrastrukturen. Se [Konfigurera flera webbplatser eller butiker](https://devdocs.magento.com/cloud/project/project-multi-sites.html).

Samma metodtips för att konfigurera `robots.txt`- och `sitemap.xml`-filer för [butiker med en plats](#single-site-storefronts) gäller för flera platslager med två viktiga skillnader:

- Kontrollera att filnamnen `robots.txt` och `sitemap.xml` innehåller namnen på motsvarande platser. Exempel:
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- Använd ett något ändrat anpassat Fast VCL-fragment för att omdirigera från platsens rot till platsen `pub/media` för båda filerna på platserna:

  ```vcl
  {
    "name": "sitemaprobots_rewrite",
    "dynamic": "0",
    "type": "recv",
    "priority": "90",
    "content": "if ( req.url.path == \"/robots.txt\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) { set req.url = \"pub/media/\" re.group.1 \"_robots.txt\"; }} else if ( req.url.path == \"/sitemap.xml\" ) { if ( req.http.host ~ \"(domainone|domaintwo).com$\" ) {  set req.url = \"pub/media/\" re.group.1 \"_sitemap.xml\"; }}"
  }
  ```

## Adobe Commerce lokalt

Använd administratörsprogrammet för att konfigurera `robots.txt`- och `sitemap.xml`-filerna så att de inte kan skanna och indexera onödigt innehåll (se [Sökmotorrotfiler](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)).

>[!TIP]
>
>För lokala distributioner, där du skriver filerna beror på hur du har installerat Adobe Commerce. Skriv filerna till `/path/to/commerce/pub/media/` eller `/path/to/commerce/media`, beroende på vilket som är rätt för din installation.

## Säkerhet

Visa inte din administratörssökväg i din `robots.txt`-fil. Att ha administratörssökvägen exponerad är en sårbarhet för webbplatshackning och potentiell förlust av data. Ta bort administratörssökvägen från filen `robots.txt`.

Anvisningar om hur du redigerar filen `robots.txt` och tar bort alla poster i administratörssökvägen finns i [Marknadsföringsanvändarhandbok > SEO och sökning > Sökmotorrobotar](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>Om du behöver hjälp kan du [skicka in en Adobe Commerce-supportanmälan](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Ytterligare information

- [Om webbplatser, butiker och butiksvyer](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [Lägger till webbplatser](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [Använd Snabbt för att blockera skadlig trafik för dina Adobe Commerce-webbplatser](https://devdocs.magento.com/cloud/cdn/fastly-vcl-blocking.html)
- [robots.txt ger ett 404-fel i Adobe Commerce i molninfrastruktur 2.3.x](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)
