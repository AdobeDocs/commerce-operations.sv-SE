---
title: Metod för projektgenomförande
description: Bekanta dig med hur Adobe Commerce programvaror levereras.
exl-id: 579cd083-8b12-49ff-bc8a-8db1ca588d74
source-git-commit: e76f101df47116f7b246f21f0fe0fa72769d2776
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---

# Metod för projektgenomförande

Nu när du har fått en bättre uppfattning om vilka verktyg som är inblandade kommer vi nu att bryta ned våra leverans- och testprocesser.

## Kontinuerlig integrering

Kontinuerliga integreringsjobb utför automatiskt följande åtgärder:

- Bygg källkoden för att kontrollera kompileringsfel.
- Kör tester när en pull-begäran skapas/uppdateras. För närvarande utförs PHP-enhetstester.

Jobbet skickar sin körningsstatus till pull-begäran. Utvecklare kan visa information om jobbkörningen så att de kan åtgärda eller förbättra befintlig kod.

## Continuous Delivery (CD)

Continuous Delivery (CD) distribuerar omedelbart källkoden till servern när alla tester har slutförts. Utvecklare kan snabbt kontrollera sina funktioner och sedan tilldela uppgiften till kvalitetsteamet för granskning.

När bygget körs på byggsystemet minimeras inte bara driftsättningens driftstopp, utan även belastningen på servern minskas. Därför påverkas inte de QA-aktiviteter som sker på servern lika mycket.

![Infografik för kontinuerlig leverans](../../assets/playbooks/cicd.svg)

CI/CD-processen i det föregående diagrammet kan kortfattat beskrivas på följande sätt:

- Bitbucket är värd för Git-databasen.
- Dockerbilder replikeras från produktionsteknikens stackkonfigurationer.
- Dockerbehållare används för alla utvecklings- och testmiljöer. Andra miljöer kan utnyttja dessa konfigurationer vid behov.
- Utvecklare genomför en utcheckning av den relevanta kodgrenen för varje ny uppgift/biljett.
- För alla allokeringsgrenar:
   - Kör en standardkodsökning.
   - Kör ett kodkompileringstest.
   - Kör en statisk kodsökning (till exempel SonarQube).
- Alla genomsökningsimplementeringar som skickas sammanfogas med målgrenen.
- En ny lanserad tagg skickas till AWS S3 för att underlätta distributionen.
- Den nya driftsättningen utlöses av driftsättningsteamet.
   - Ett distributionsjobb distribuerar det nya paketet till målmiljön.
   - Uppdateringar av databasstrukturen kräver en paus för att ta emot nya förfrågningar från kunden.
- Distributionsprocessen avslutas med ett e-postmeddelande/Slack/Teams som skickas automatiskt av servern till distributionsteamet.
