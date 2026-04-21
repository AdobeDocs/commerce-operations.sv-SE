---
title: Schema för patchrelease
description: Läs när Adobe planerar att släppa nya patchar och säkerhetskorrigeringar för Adobe Commerce.
exl-id: ae1e09cd-966f-44a3-9e4d-b90bb838429d
source-git-commit: 0f46bdfd0afbca07e0d60e995ee9426f5408671d
workflow-type: tm+mt
source-wordcount: '380'
ht-degree: 0%

---


# Schema för patchrelease

Adobe strävar hela tiden efter att hitta rätt balans mellan att göra produktuppgraderingar enkla och förutsägbara samtidigt som man levererar förbättringar till tidiga användare snabbare (se [versionspolicy](versioning-policy.md)).

Syftet med schemat är att ange datum när Adobe planerar att meddela att [korrigeringar](versioning-policy.md#patch-release) har släppts för varje rad i Adobe Commerce PHP-huvudprogrammet som stöds. Patch-versioner är möjligheter att uppgradera kärnkodbasen för att hålla plattformen säker, tillförlitlig och effektiv.

>[!NOTE]
>
>Mer information om nya funktioner, molninfrastruktur och utökningsmöjligheter finns i [versionsdokumentationen för Adobe Commerce Services](https://experienceleague.adobe.com/en/docs/commerce/user-guides/release-information/release-notes-all).

Förutom de schemalagda kvalitets-, säkerhets- och betatestarna på den här sidan ger Adobe tillgång till [enskilda korrigeringsfiler](versioning-policy.md#individual-patch) via [kvalitetskorrigeringsverktyget](../tools/quality-patches-tool/usage.md). Med verktyget kan du tillämpa, återställa och visa allmän information om alla enskilda korrigeringsfiler som är tillgängliga för den installerade versionen av Adobe Commerce.

Adobe Commerce patch-releaser släpps baserat på följande riktlinjer:

- **Isolerad säkerhetspatchningsfil** - Enskilda, icke-kumulativa [säkerhetspatchningsfiler ](versioning-policy.md#isolated-security-patch-file) frigörs separat för att möjliggöra snabbare åtgärder och införlivas i nästa fullständiga säkerhetskorrigering. Om du vill använda en isolerad säkerhetskorrigeringsfil måste kunderna finnas på den senaste säkerhetspatchversionen (den senaste -p-versionen) för den versionslinje som stöds, eftersom isolerade säkerhetskorrigeringar endast testas mot den versionen.

- **Säkerhetsuppdateringar** - [Säkerhetsuppdateringar](versioning-policy.md#security-patch-release) släpps årligen för alla [supportade](lifecycle-policy.md) versionsrader. Dessa korrigeringar innehåller alla tidigare släppta säkerhets-, kompatibilitets- och kvalitetsuppdateringar.  Adobe kan vid behov släppa ytterligare säkerhetsuppdateringar, men det är inte säkert.

- **Lappa** - En fullständig [patch](versioning-policy.md#patch-release) för Adobe Commerce 2.4.x LTS-versionsrad (3-årig supportperiod) släpps årligen (maj).

- **Alpha-korrigeringar**-One [alpha patch](versioning-policy.md#alpha-patch-release) för Adobe Commerce 2.4.x LTS släpps årligen.

- **Beta-korrigeringar** - En [betatestning](versioning-policy.md#beta-patch-release) för Adobe Commerce 2.4.x LTS-versionsrad släpps årligen.

Mer information finns i följande bild:

<!-- The SVG source for the following image is located here: /help/assets/release/release-calendar.drawio.svg -->

![Versionskalender för Adobe Commerce 2026](../assets/release/release-calendar.png)


## Utgivningsmeddelandekanaler

Adobe meddelar sina kunder om nya patchar via följande kanaler:

- [Adobe säkerhetsbulletiner och -anvisningar](https://helpx.adobe.com/security/security-bulletin.html#magento)
- E-post
- Varningar i produkten

>[!NOTE]
>
> Releasedatum för varje mindre version, korrigeringsfil och säkerhetsrelease samt datum för slutet av den vanliga supporten finns i [Releaserade versioner](https://experienceleague.adobe.com/en/docs/commerce-operations/release/versions).
