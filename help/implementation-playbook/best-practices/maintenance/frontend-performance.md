---
title: Prestanda för granskningsfronder
description: Identifiera och åtgärda problem som negativt påverkar webbplatsens prestanda genom att använda webbprestandaverktyg för att granska Adobe Commerce butiksverksamhet.
role: Admin, User, Developer
feature: Best Practices
exl-id: bafae565-9d09-4cc0-8507-e89a11dbd915
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '184'
ht-degree: 0%

---

# Bästa tillvägagångssätt för frontend-prestanda

Använd webbprestandaverktyg för att kontrollera frontprestanda i Adobe Commerce butiker.
Dessa verktyg använder olika mätvärden för att ge kraftfulla insikter och rekommendationer för att förbättra onlinebutikens prestanda.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Kontrollera frontprestanda

Så här kontrollerar du hur din webbplatsbutik fungerar i förväg:

1. Granska frontend-prestanda med webbprestandaverktyg som:

   - **[Google Lighthuse](https://web.dev/measure/)** - Lightroom innehåller granskningar av prestanda, tillgänglighet, progressiva webbappar, SEO med mera. Mer information om olika sätt att köra fyr finns i [Översikt över fyr](https://developer.chrome.com/docs/lighthouse/overview).)
   - **[Google PageSpeed Insights](https://pagespeed.web.dev/)** - PageSpeed Insights ger snabbt en detaljerad rapport om orsakerna till långsam webbsidsprestanda tillsammans med rekommendationer om hur den kan åtgärdas.

1. Granska granskningsrapporterna och implementera de rekommendationer som ges för att förbättra butikens prestanda.

## Ytterligare information

- [Indexhantering för administratörer](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Indexhantering med CLI](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html?lang=sv-SE)
- [Indexeringsöversikt för utvecklare](https://developer.adobe.com/commerce/php/development/components/indexing/)
