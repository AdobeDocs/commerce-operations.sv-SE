---
title: Programlägen
description: Commerce-programmet kan fungera i olika lägen beroende på dina behov. Visa en detaljerad lista över tillgängliga programlägen.
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 0%

---


# Programlägen

Du kan köra Commerce-programmet i något av följande _lägen_:

| Modulnamn | Beskrivning |
| ----------- | ----------- |
| standard | Gör att du kan distribuera Commerce-programmet på en enda server utan att ändra några inställningar. Standardläget är dock inte optimerat för produktion.<br>Om du vill distribuera Commerce-programmet på mer än en server eller optimera det för produktion ändrar du till något av de andra lägena.<ul><li>Filcachning för statisk vy har aktiverats</li><li>Undantag visas inte för användaren. I stället skrivs undantag till loggfiler.</li><li>Döljer egna `X-Magento-*` Rubriker för HTTP-begäran och -svar</li></ul> |
| utvecklare | Detta läge är endast avsett för utveckling:<ul><li>Inaktiverar cachelagring av statiska visningsfiler</li><li>Avancerad loggning</li><li>Aktiverar [automatisk kodkompilering](../cli/code-compiler.md)</li><li>Aktiverar förbättrad felsökning</li><li>Visar anpassade `X-Magento-*` Rubriker för HTTP-begäran och -svar</li><li>Resultat i långsammaste prestanda</li><li>Visar fel i förgrunden</li></ul> |
| produktion | Avsett för driftsättning i ett produktionssystem:<ul><li>Visar inte undantag för användaren (undantag skrivs endast till loggar).</li><li>Fungerar endast för statiska vyfiler från cache.</li><li>Förhindrar automatisk kompilering av kodfiler. Nya eller uppdaterade filer skrivs inte till filsystemet.</li><li>**Du kan inte aktivera eller inaktivera cachetyper i Admin.** Se [aktivera och inaktivera cache](../cli/manage-cache.md#enable-or-disable-cache-types).</li><li>Vissa fält, till exempel avsnitten om avancerad systemkonfiguration och utvecklarsystemkonfiguration i Admin, är inte tillgängliga i produktionsläge.</li></ul> |
| underhåll | Avsikten är att förhindra åtkomst till en plats medan den uppdateras eller konfigureras om är följande läge:<ul><li>Omdirigerar besökare till en standardplats `Service Temporarily Unavailable` sida.</li><li>När platsen är i underhållsläge, `var/` katalogen innehåller `.maintenance.flag` -fil.</li><li>Du kan konfigurera underhållsläge för att tillåta besökaråtkomst från en angiven lista med IP-adresser.</li></ul> |

>[!INFO]
>
>[Adobe Commerce i molninfrastruktur](https://devdocs.magento.com/cloud/bk-cloud.html) stöder endast produktions- och underhållslägen.

## Standardläge

Som namnet antyder är standardläget hur Commerce fungerar om inget annat läge anges. Med standardläget kan du distribuera Commerce-programmet på en enda server utan att ändra några inställningar. Standardläget är dock inte lika optimerat för produktion som produktionsläget.

Om du vill distribuera Commerce-programmet på mer än en server eller optimera det för produktion ändrar du till något av de andra lägena.

I standardläge:

- Fel loggas i filrapporter på servern och visas aldrig för en användare
- Statiska visningsfiler cachelagras
- Standardläget är inte optimerat för en produktionsmiljö, främst på grund av de negativa prestandaeffekterna av [statiska filer](https://glossary.magento.com/static-files) som genereras dynamiskt i stället för att materialiseras. Det innebär att när du skapar statiska filer och cachelagrar dem får det en större prestandaeffekt än om du genererar dem med verktyget för att skapa statiska filer.

Se [Ange åtgärdsläge](../cli/set-mode.md).

## Utvecklarläge

Kör Commerce-programmet i utvecklarläge när du utökar eller anpassar det.

I utvecklarläge:

- Statiska vyfiler cachelagras inte. de skrivs till `pub/static` katalog varje gång de anropas
- Visning av ej infångade undantag i webbläsaren
- Systeminloggning `var/report` är mycket detaljerad
- An [undantag](https://glossary.magento.com/exception) genereras i felhanteraren i stället för att loggas
- Ett undantag genereras när en [event](https://glossary.magento.com/event) prenumeranten kan inte anropas

Se [Ange åtgärdsläge](../cli/set-mode.md).

## Produktionsläge

Kör Commerce i produktionsläge när den distribueras till en produktionsserver. När du har optimerat servermiljön, t.ex. databasen och webbservern, bör du köra [distributionsverktyg för statiska vyfiler](../cli/static-view-file-deployment.md) för att skriva statiska vyfiler till `pub/static` katalog.

Detta förbättrar prestandan genom att tillhandahålla alla nödvändiga statiska filer vid distributionen i stället för att tvinga Commerce att dynamiskt leta reda på och kopiera (materialisera) statiska filer vid behov under körningen.

I produktionsläge:

- Statiska visningsfiler materialiseras inte, och URL:er för dem skapas direkt. Filer i statisk vy hanteras från [cache](https://glossary.magento.com/cache) endast.
- Fel loggas i filsystemet och visas aldrig för användaren.
- Du kan aktivera och inaktivera cachetyper _endast_ med [kommandorad](../cli/manage-cache.md#config-cli-subcommands-cache-en).
- Du _inte_ aktivera eller inaktivera cachetyper med Admin.

## Underhållsläge

Kör Commerce-programmet i underhållsläge för att koppla från din webbplats medan du slutför underhålls-, uppgraderings- eller konfigureringsuppgifter. I underhållsläge dirigerar webbplatsen om besökare till en standard `Service Temporarily Unavailable` sida.

Du kan skapa en [anpassad underhållssida](https://experienceleague.adobe.com/docs/commerce-operations/upgrade-guide/troubleshooting/maintenance-mode-options.html), aktivera och inaktivera underhållsläge manuellt och konfigurera underhållsläge så att besökare från auktoriserade IP-adresser kan visa butiken normalt. Se [aktivera och inaktivera underhållsläge](https://devdocs.magento.com/guides/v2.4/install-gde/install/cli/install-cli-subcommands-maint.html).

Om du använder Commerce på molninfrastruktur körs Commerce-programmet i underhållsläge under distributionsfasen. När distributionen har slutförts återgår Commerce-programmet till att köras i produktionsläge. Se [Distributionskopplingar](https://devdocs.magento.com/cloud/reference/discover-deploy.html#cloud-deploy-over-phases-hook) i _Commerce Cloud guide_.
