---
title: Bästa tillvägagångssätt för att konfigurera filerna "robots.txt" och "sitemap.xml"
description: Lär dig hur du skickar instruktioner om din Adobe Commerce webbplats till webbcrawler.
role: Developer
feature-set: Commerce
feature: Best Practices
exl-id: f3a81bab-a47a-46ad-b334-920df98c87ab
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '596'
ht-degree: 0%

---

# Bästa tillvägagångssätt för konfigurering `robots.txt` och `sitemap.xml` filer

I den här artikeln beskrivs de bästa sätten att använda `robots.txt` och `sitemap.xml` filer i Adobe Commerce, inklusive konfiguration och säkerhet. Dessa filer instruerar webrobotar (vanligtvis sökrobotar) att crawla sidor på en webbplats. Om du konfigurerar dessa filer kan webbplatsens prestanda förbättras och sökmotoroptimeringen förbättras.

>[!NOTE]
>
>De bästa sätten är att använda i projekt som endast använder den inbyggda Adobe Commerce Store. De gäller inte för Adobe Commerce-projekt som använder andra butikslösningar (till exempel Adobe Experience Manager, headless).

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Adobe Commerce i molninfrastruktur

Ett Adobe Commerce-standardprojekt innehåller en hierarki som innehåller en webbplats-, butiks- och butiksvy. För mer komplexa implementeringar kan du skapa ytterligare webbplatser, butiker och butiksvyer för en _flera platser_ storefront.

### Butiker för en webbplats

Följ dessa standarder när du konfigurerar `robots.txt` och `sitemap.xml` filer för butiker på en plats:

- Se till att ditt projekt använder [`ece-tools`](https://devdocs.magento.com/cloud/release-notes/ece-release-notes.html) version 2002.0.12 eller senare.
- Använd programmet Admin för att lägga till innehåll i `robots.txt` -fil.

   >[!TIP]
   >
   >Visa den autogenererade `robots.txt` fil för din butik på `<domain.your.project>/robots.txt`.

- Använd administratörsprogrammet för att generera en `sitemap.xml` -fil.

   >[!IMPORTANT]
   >
   >På grund av det skrivskyddade filsystemet i Adobe Commerce för molninfrastrukturprojekt måste du ange `pub/media` sökväg innan filen genereras.

- Använd ett anpassat fast VCL-fragment för att omdirigera från platsens rot till `pub/media/` plats för båda filerna:

   ```vcl
   {
     "name": "sitemaprobots_rewrite",
     "dynamic": "0",
     "type": "recv",
     "priority": "90",
     "content": "if ( req.url.path ~ \"^/?sitemap.xml$\" ) { set req.url = \"pub/media/sitemap.xml\"; } else if (req.url.path ~ \"^/?robots.txt$\") { set req.url = \"pub/media/robots.txt\";}"
   }
   ```

- Testa omdirigeringen genom att visa filerna i en webbläsare. Till exempel: `<domain.your.project>/robots.txt` och `<domain.your.project>/sitemap.xml`. Se till att du använder rotsökvägen som du konfigurerade omdirigeringen för och inte en annan sökväg.

>[!INFO]
>
>Se [Lägg till webbplatskarta och sökrobotar](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html) för detaljerade anvisningar.


### Lagringsplatser för flera platser

Du kan konfigurera och köra flera butiker med en enda implementering av Adobe Commerce i molninfrastrukturen. Se [Konfigurera flera webbplatser eller butiker](https://devdocs.magento.com/cloud/project/project-multi-sites.html).

Samma metodtips för att konfigurera `robots.txt` och `sitemap.xml` filer för [butiker för en webbplats](#single-site-storefronts) gäller för butiker med flera platser med två viktiga skillnader:

- Se till att `robots.txt` och `sitemap.xml` filnamnen innehåller namnen på motsvarande platser. Till exempel:
   - `domaineone_robots.txt`
   - `domaintwo_robots.txt`
   - `domainone_sitemap.xml`
   - `domaintwo_sitemap.xml`

- Använd ett något modifierat anpassat VCL-fragment för att dirigera om från platsens rot till `pub/media` plats för båda filerna på dina platser:

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

Konfigurera `robots.txt` och `sitemap.xml` filer för att förhindra att bottnar skannar och indexerar onödigt innehåll (se [Sökmotorrobotar](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots)).

>[!TIP]
>
>För lokala distributioner, där du skriver filerna beror på hur du har installerat Adobe Commerce. Skriv filerna till `/path/to/commerce/pub/media/` eller `/path/to/commerce/media`, beroende på vad som gäller för installationen.

## Säkerhet

Visa inte din administratörssökväg i din `robots.txt` -fil. Att ha administratörssökvägen exponerad är en sårbarhet för webbplatshackning och potentiell förlust av data. Ta bort Admin-sökvägen från `robots.txt` -fil.

För steg redigerar du `robots.txt` och ta bort alla poster i administratörssökvägen finns i [Marketing User Guide > SEO and Search > Search Engine Robots](https://experienceleague.adobe.com/docs/commerce-admin/marketing/seo/seo-overview.html#search-engine-robots).

>[!TIP]
>
>Om du behöver hjälp, [skicka en Adobe Commerce-supportanmälan](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/help-center-guide/magento-help-center-user-guide.html#submit-ticket).

## Ytterligare information

- [Förstå webbplatser, butiker och butiksvyer](https://devdocs.magento.com/cloud/configure/configure-best-practices.html#sites)
- [Lägga till webbplatser](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [Använd Snabbt för att blockera skadlig trafik för dina Adobe Commerce-sajter](https://devdocs.magento.com/cloud/cdn/fastly-vcl-blocking.html)
- [robots.txt ger 404 fel i Adobe Commerce i molninfrastruktur 2.3.x](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/robots.txt-gives-404-error-magento-commerce-cloud-2.3.x.html)
