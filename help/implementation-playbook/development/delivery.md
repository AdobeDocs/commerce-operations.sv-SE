---
title: Project Implementation Methodology
description: Bekanta dig med hur Adobe Commerce kan leverera programvara.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# Metod för projektgenomförande

Nu när du har fått en bättre uppfattning om vilka verktyg som är inblandade kommer vi nu att bryta ned våra leverans- och testprocesser.

## Kontinuerlig integrering

Kontinuerliga integreringsjobb utför automatiskt följande åtgärder:

- Build the source code to check compilation errors.
- Execute tests when a pull request is created/updated. För närvarande utförs PHP-enhetstester.

Jobbet skickar sin körningsstatus till pull-begäran. Utvecklare kan visa information om jobbkörningen så att de kan åtgärda eller förbättra befintlig kod.

## Continuous Delivery (CD)

Continuous Delivery (CD) distribuerar omedelbart källkoden till servern när alla tester har slutförts. Developers can check their functions quickly and then assign the task to the QA team for review.

När bygget körs på byggsystemet minimeras inte bara driftsättningens driftstopp, utan även belastningen på servern minskas. As a result, the QA activities, which are happening on the server, are impacted less.

![Continuous delivery infographic](../../assets/playbooks/cicd.svg)

The CI/CD process in the previous diagram can be briefly described as follows:

- Bitbucket är värd för Git-databasen.
- Docker images are replicated from production technology stack configurations.
- Docker containers are used for all development and testing environments. Other environments could leverage these configurations if needed.
- Developers perform a checkout of the relevant code branch for every new task/ticket.
- För alla allokeringsgrenar:
   - Kör en standardkodsökning.
   - Kör ett kodkompileringstest.
   - Kör en statisk kodsökning (till exempel SonarQube).
- Alla genomsökningsimplementeringar som skickas sammanfogas med målgrenen.
- En ny släppt tagg skickas till AWS S3 för att vara redo för distributionen.
- Den nya driftsättningen utlöses av driftsättningsteamet.
   - Ett distributionsjobb distribuerar det nya paketet till målmiljön.
   - Uppdateringar av databasstrukturen kräver en paus för att ta emot nya förfrågningar från kunden.
- Distributionsprocessen avslutas med ett e-postmeddelande/Slack/Teams som skickas automatiskt av servern till distributionsteamet.
