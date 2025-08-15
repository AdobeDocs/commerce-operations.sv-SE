---
title: Bästa praxis för Git-förgreningar
description: Lär dig mer om olika förgreningsstrategier för källkodshantering.
feature: Best Practices
role: Developer
exl-id: 7d7736e8-7023-4315-9965-71866b0be5c3
source-git-commit: 823498f041a6d12cfdedd6757499d62ac2aced3d
workflow-type: tm+mt
source-wordcount: '306'
ht-degree: 0%

---

# Bästa praxis för Git-förgreningar

Source-kod genomgår flera stabilitetsfaser under utvecklingsprocessen:

- Aktiv utveckling
- Inledande kodintegrering
- Kodintegrering för kvalitetssäkring (QA)
- Kodintegrering för slutanvändaraccepttestning (UAT)
- Slutlig kodintegrering för produktionsreleaser

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce på plats

## Filialhantering

Varje utvecklingsfas ska ha en motsvarande gren i Git för att spåra kodändringar och underlätta distributionsprocessen:

- **Aktivitetsgren** - Där utvecklare implementerar sina individuella kodändringar när de implementerar specifika uppgifter, som funktioner och felkorrigeringar.
- **Utvecklingsgren** - Där flera utvecklare sammanfogar ändringar från sina enskilda aktivitetsgrenar till en enda utvecklingsgren för automatiserad integreringstestning. Den här grenen distribueras till en utvecklingsmiljö.
- **QA-gren** - Där utvecklare sammanfogar ändringar när utvecklingen är klar och koden har genomgått all automatisk integrationstestning och kodgranskning. Denna gren distribueras till QA-miljön för manuell QA-testning.
- **Stabil/UAT-gren** - Där kod sammanfogas efter att manuell QA-testning har godkänts. Den här grenen distribueras till en UAT-miljö för testning av användargodkännande.
- **Produktions-/lanseringsgren** - Där kod sammanfogas efter att den har passerat UAT. Den här grenen distribueras till produktion för en release.

>[!TIP]
>
>Adobe Commerce i molninfrastrukturprojekt innehåller specifika grenar som motsvarar olika miljöer. Se [Pro-projektarbetsflödet](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-develop-deploy-workflow.html?lang=sv-SE) och [Startprojektarbetsflödet](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/starter-develop-deploy-workflow.html?lang=sv-SE) i _molnhandboken_.

## Avdelningsstrategier

Det finns flera förgreningsstrategier som du kan använda. Välj en strategi som fungerar bäst för utvecklingsteamet och komplexiteten i projektet.

Mer information finns i följande externa resurser:

- [Förgreningsarbetsflöden](https://git-scm.com/book/en/v2/Git-Branching-Branching-Workflows)
- [Distribuerade arbetsflöden](https://git-scm.com/book/en/v2/Distributed-Git-Distributed-Workflows)
- [Mönster för att hantera källkodsgrenar](https://martinfowler.com/articles/branching-patterns.html)
- [En Git-förgreningsmodell som lyckades](https://nvie.com/posts/a-successful-git-branching-model/)
- [GitHub-flöde](https://docs.github.com/en/get-started/quickstart/github-flow)
- [GitLab-flöde](https://about.gitlab.com/blog/2023/07/27/gitlab-flow-duo/)
