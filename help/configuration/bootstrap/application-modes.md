---
title: Programlägen
description: Commerce kan fungera i olika lägen beroende på dina behov. Visa en detaljerad lista över tillgängliga programlägen.
exl-id: a2a71f43-682f-4fa4-940a-1f6a4d441c41
source-git-commit: c415c3427f513255b9d4ebe1d24ba4024df21928
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 0%

---

# Programlägen

Du kan köra Commerce-programmet i något av följande _lägen_:

| Lägesnamn | Beskrivning | Molnsupport |
| ------------------------ | ------------------- | ------------- |
| [standard](#default-mode) | Distribuera och kör Commerce-programmet på en enda server utan att ändra inställningarna. _Inte_ optimerad för produktion. | no |
| [utvecklare](#developer-mode) | Perfekt för utveckling när du utökar eller anpassar Commerce. | no |
| [produktion](#production-mode) | Distribuera och kör Commerce-programmet i ett produktionssystem. | Ja |
| [underhåll](#maintenance-mode) | Förhindra åtkomst till en webbplats när du utför uppdateringar och konfigurationer. | Ja |

Mer information om hur du ändrar åtgärdslägen manuellt finns i [Ange åtgärdsläge](../cli/set-mode.md).

## Molnsupport

På grund av det skrivskyddade filsystemet finns det en strikt restriktion mot att ändra lägen i fjärrmolnmiljöer, och det kan inte åsidosättas av Adobe Commerce Support. Försök inte ändra lägen genom att ändra filen `app/etc/env.php` eftersom filen som baseras på flera konfigurationskällor skrivs över av paketet `ece-tools`.

Adobe Commerce i molninfrastrukturen kör automatiskt programmet i _underhållsläge_ under en distribution, vilket gör att webbplatsen är offline tills distributionen är klar. I annat fall förblir programmet i _produktions_-läge. Se [Distributionsprocess](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/process.html?lang=sv-SE#deploy-phase) i guiden _Commerce om molninfrastruktur_.

Om du använder Cloud Docker för Commerce som ett utvecklingsverktyg kan du distribuera ditt molninfrastrukturprojekt i en Docker-miljö i _developer_ -läge, men prestanda blir långsammare på grund av ytterligare filsynkroniseringsåtgärder. Se [Distribuera Docker-miljön](https://developer.adobe.com/commerce/cloud-tools/docker/deploy/#launch-mode) i guiden _Cloud Docker för Commerce_.


## Standardläge

Med _standardläget_ kan du distribuera Commerce-programmet på en enda server utan att ändra några inställningar. Standardläget är dock inte optimerat för produktion på grund av de statiska filernas negativa prestandapåverkan. Att skapa statiska filer och cacha dem har större prestandapåverkan än att generera dem med verktyget för att skapa statiska filer.

I standardläge:

- Undantag skrivs till loggfiler i stället för att visas
- Statiska visningsfiler cachelagras
- Döljer anpassade rubriker för `X-Magento-*` HTTP-begäran och svar

Commerce används i standardläge om inget annat läge anges.

## Utvecklarläge

Du bör använda läget _developer_ för att utöka och anpassa Commerce-programmet. Statiska vyfiler cachelagras inte, men skrivs på begäran till katalogen `pub/static`.

I utvecklarläge:

- Aktiverar [automatisk kodkompilering](../cli/code-compiler.md) och utökad felsökning
- Ohanterade undantag visas i webbläsaren
- Systeminloggningen `var/report` är utförlig
- Ett undantag genereras i felhanteraren i stället för att loggas
- Ett undantag genereras när en händelseprenumerant inte kan anropas
- Visar anpassade rubriker för `X-Magento-*` HTTP-begäran och svar

>[!NOTE]
>
>Det här läget stöds inte i Adobe Commerce Cloud-miljön och Adobe Commerce Support kan inte underlätta ändring av programläge.

## Produktionsläge

Läget _production_ är bäst för distribution av Commerce-programmet till ett produktionssystem. När du har optimerat servermiljön, t.ex. databasen och webbservern, bör du köra distributionsverktyget [för statiska vyfiler](../cli/static-view-file-deployment.md) för att skriva statiska vyfiler till katalogen `pub/static`. Detta förbättrar prestandan genom att tillhandahålla alla nödvändiga statiska filer vid distributionen i stället för att tvinga Commerce-programmet att dynamiskt leta reda på och kopiera (materialisera) statiska filer vid behov under körningen.

Vissa fält, till exempel avsnitten om avancerad systemkonfiguration och utvecklarsystemkonfiguration i Admin, är inte tillgängliga i produktionsläge. Du _kan till exempel inte_ aktivera eller inaktivera cachetyper med Admin. Du kan aktivera och inaktivera cachetyperna _only_ med kommandoraden [3&rbrace;.](../cli/manage-cache.md#config-cli-subcommands-cache-en)

I produktionsläge:

- Filer i statisk vy hanteras endast från cacheminnet
- Fel och undantag loggas i filsystemet och visas aldrig för användaren
- Vissa konfigurationsfält i Admin är inte tillgängliga

## Underhållsläge

_underhållsläget_ begränsar eller förhindrar åtkomst till en plats under förbättringar, uppdateringar och konfigurationsåtgärder. Som standard dirigerar webbplatsen om besökare till en `Service Temporarily Unavailable`-standardsida.

Du kan skapa en [anpassad underhållssida](../../upgrade/troubleshooting/maintenance-mode-options.md), manuellt aktivera och inaktivera underhållsläge och konfigurera underhållsläge så att besökare från auktoriserade IP-adresser kan visa butiken normalt. Se [aktivera och inaktivera underhållsläge](../../installation/tutorials/maintenance-mode.md) i _installationshandboken_.

Om du använder Commerce i molninfrastruktur körs Commerce-programmet i underhållsläge under distributionsfasen. När distributionen har slutförts återgår Commerce-programmet till att köras i produktionsläge. Se [Distributionskopplingar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/deploy/best-practices.html?lang=sv-SE#phase-5%3A-deployment-hooks) i _guiden för Commerce om molninfrastruktur_.

I underhållsläge:

- Webbplatsbesökare omdirigeras till en standardsida på `Service Temporarily Unavailable`
- Katalogen `var/` innehåller filen `.maintenance.flag`
- Du kan begränsa besökaråtkomst baserat på IP-adresser
