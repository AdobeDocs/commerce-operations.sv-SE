---
title: Programlägen
description: Commerce-programmet kan fungera i olika lägen beroende på dina behov. Visa en detaljerad lista över tillgängliga programlägen.
exl-id: a2a71f43-682f-4fa4-940a-1f6a4d441c41
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '719'
ht-degree: 0%

---

# Programlägen

Du kan köra Commerce-programmet i något av följande _lägen_:

| Lägesnamn | Beskrivning | Molnsupport |
| ------------------------ | ------------------- | ------------- |
| [standard](#default-mode) | Distribuera och kör Commerce-programmet på en enda server utan att ändra inställningarna. _Inte_ optimerad för produktion. | no |
| [utvecklare](#developer-mode) | Perfekt för utveckling när du utökar eller anpassar Commerce-programmet. | no |
| [produktion](#production-mode) | Distribuera och kör Commerce-programmet till ett produktionssystem. | Ja |
| [underhåll](#maintenance-mode) | Förhindra åtkomst till en webbplats när du utför uppdateringar och konfigurationer. | Ja |

Se [Ange åtgärdsläge](../cli/set-mode.md) om du vill lära dig hur du ändrar Adobe Commerce driftslägen manuellt.

## Molnsupport

Du behöver inte hantera programlägena för ett molninfrastrukturprojekt. På grund av det skrivskyddade filsystemet kan du inte ändra lägen i fjärrmolnmiljöer. Adobe Commerce i molninfrastrukturen kör automatiskt programmet i _underhåll_ under en distribution, vilket gör att webbplatsen är offline tills distributionen är klar. Annars stannar programmet kvar i _produktion_ läge. Se [Distributionsprocess](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html#deploy-phase) i _Guide för Commerce on Cloud Infrastructure_.

Om du använder Cloud Docker för Commerce som utvecklingsverktyg kan du driftsätta ditt molninfrastrukturprojekt i en Docker-miljö i _utvecklare_ men prestanda är långsammare på grund av ytterligare filsynkroniseringsåtgärder. Se [Distribuera Docker-miljön](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode) i _Handbok för Cloud Docker for Commerce_.

## Standardläge

The _standard_ I kan du distribuera Commerce-programmet på en enda server utan att ändra några inställningar. Standardläget är dock inte optimerat för produktion på grund av de statiska filernas negativa prestandapåverkan. Att skapa statiska filer och cacha dem har större prestandapåverkan än att generera dem med verktyget för att skapa statiska filer.

I standardläge:

- Undantag skrivs till loggfiler i stället för att visas
- Statiska visningsfiler cachelagras
- Döljer egna `X-Magento-*` Rubriker för HTTP-begäran och -svar

Commerce körs i standardläge om inget annat läge anges.

## Utvecklarläge

The _utvecklare_ Du bör använda läget för att utöka och anpassa Commerce-programmet. Filer i statisk vy cachelagras inte, utan skrivs till `pub/static` on demand.

I utvecklarläge:

- Aktiverar [automatisk kodkompilering](../cli/code-compiler.md) och förbättrad felsökning
- Visning av ej infångade undantag i webbläsaren
- Systeminloggning `var/report` är mycket detaljerad
- Ett undantag genereras i felhanteraren i stället för att loggas
- Ett undantag genereras när en händelseprenumerant inte kan anropas
- Visar anpassade `X-Magento-*` Rubriker för HTTP-begäran och -svar

## Produktionsläge

The _produktion_ är bäst för att distribuera Commerce-programmet på ett produktionssystem. När du har optimerat servermiljön, t.ex. databasen och webbservern, bör du köra [distributionsverktyg för statiska vyfiler](../cli/static-view-file-deployment.md) för att skriva statiska vyfiler till `pub/static` katalog. Detta förbättrar prestandan genom att tillhandahålla alla nödvändiga statiska filer vid distributionen i stället för att tvinga Commerce-programmet att dynamiskt leta reda på och kopiera (materialisera) statiska filer vid behov under körningen.

Vissa fält, till exempel avsnitten om avancerad systemkonfiguration och utvecklarsystemkonfiguration i Admin, är inte tillgängliga i produktionsläge. Du kan till exempel _inte_ aktivera eller inaktivera cachetyper med Admin. Du kan aktivera och inaktivera cachetyper _endast_ med [kommandorad](../cli/manage-cache.md#config-cli-subcommands-cache-en).

I produktionsläge:

- Filer i statisk vy hanteras endast från cacheminnet
- Fel och undantag loggas i filsystemet och visas aldrig för användaren
- Vissa konfigurationsfält i Admin är inte tillgängliga

## Underhållsläge

The _underhåll_ Läget begränsar eller förhindrar åtkomst till en plats under förbättringar, uppdateringar och konfigurationsåtgärder. Som standard dirigeras besökarna om till ett standardvärde `Service Temporarily Unavailable` sida.

Du kan skapa en [anpassad underhållssida](../../upgrade/troubleshooting/maintenance-mode-options.md), aktivera och inaktivera underhållsläge manuellt och konfigurera underhållsläge så att besökare från auktoriserade IP-adresser kan visa butiken normalt. Se [aktivera och inaktivera underhållsläge](../../installation/tutorials/maintenance-mode.md) i _Installationshandbok_.

Om du använder Commerce på molninfrastruktur körs Commerce-programmet i underhållsläge under distributionsfasen. När distributionen har slutförts återgår Commerce-programmet till att köras i produktionsläge. Se [Distributionskopplingar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html#phase-5%3A-deployment-hooks) i _Guide för Commerce on Cloud Infrastructure_.

I underhållsläge:

- Webbplatsbesökare omdirigeras till en standard `Service Temporarily Unavailable` page
- The `var/` katalogen innehåller `.maintenance.flag` fil
- Du kan begränsa besökaråtkomst baserat på IP-adresser
