---
title: Testning
description: AB-testning och driftsättningstestning är vanliga för e-handelsprojekt och bidrar till att säkerställa högkvalitativa webbplatser.
source-git-commit: 226f1925d9ca628c94b67a86888084a21cd7e336
workflow-type: tm+mt
source-wordcount: '212'
ht-degree: 0%

---


# Testning

Testning är en viktig del av utvecklingslivscykeln.

## A/B-tester

![Ikon för AB-testning](../../assets/playbooks/a-b-testing.png)

A/B-testning är processen att jämföra två olika versioner av webbplatsen för att se skillnaden i prestanda.

När du har skapat webbplatsen kan du använda A/B-testning för att testa vilka ord, fraser, bilder och innehåll som är mest effektiva för att öka konverteringsgraden. Till exempel A/B-testar en grön CTA-knapp och en röd CTA-knapp för att förstå vilka färger kunderna föredrar.

Som regel rekommenderar vi att du utför A/B-tester två gånger per år på större releaser, funktioner och frontoptimeringar.

## Distributionstestning

![Ikon för distributionstestning](../../assets/playbooks/deployment-testing.png)

Målet med driftsättningstestning för att verifiera att alla byggen, ändringar, design och laster fungerar som förväntat på produktionsplatsen. Distributionstestning är viktigt eftersom det är den sista kontrollen innan webbplatsen startar och kunderna får se webbplatsen och funktionaliteten.

Du bör göra distributionstestning i en staging-miljö (icke-produktionsmiljö) innan du startar programmet och åtgärda eventuella buggar som kan hindra kunderna från att checka ut.

Dessutom bör du testa efter varje release i produktionsmiljön för att säkerställa att det är enkelt att lägga till i varukorgen och göra transaktioner.
