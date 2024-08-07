---
title: Bästa praxis för uppgradering av checklista
description: Lär dig hur du skapar och använder en checklista för uppgradering för att planera din Adobe Commerce uppgraderingsstrategi.
role: Leader
feature: Best Practices
exl-id: c9b644fa-290c-4f33-b5a7-19f7122ff08e
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# Bästa praxis för uppgradering av checklista

Använd checklistan under årliga och kvartalsvisa samtal med ert e-handelsteam. Många företag arbetar med årliga budgetar och färdplaner. Under dessa årliga diskussioner är det av största vikt att du talar om din plattforms hälsa, riktning och uppgraderingsstrategi för året, tillsammans med hur den passar in i företagets övergripande mål och nyckeltal. Under kvartalsvisa konversationer måste du se till att årsplanen som du har skapat fortfarande är i linje med din nuvarande situation eller pivot om så inte är fallet. Målet med checklistan för Upgrade Plan är att hjälpa er att planera och schemalägga Adobe Commerce-uppgraderingar för att säkerställa en lyckad uppgraderingsprocess under året. Denna checklista är avsedd att användas av följande målgrupper för årlig planering och kvartalsvis granskning:

- Director/IT-chef
- eCommerce Manager
- Solution Partner / Consultant

>[!NOTE]
>
>En detaljerad beskrivning av de tekniska stegen för att uppgradera finns i [Fullständiga uppgraderingskrav](../../../upgrade/prepare/prerequisites.md) i användardokumentationen.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Mål

▢ Granska aktuella KPI:er och justera efter behov.

## Tillägg och anpassningar

▢ Granska alla aktuella tillägg och anpassningar och se till att de fortfarande behövs baserat på verksamhetskrav.

▢ Överväg att ersätta tillägg som inte har god erfarenhet av att hålla sig uppdaterad med Adobe Commerce-versioner.

## Team

▢ Se till att ni har rätt team på plats med rätt Adobe Commerce-certifieringar och kompetenser.

## Budget och timing

▢ Använd Adobe Commerce [release schedule](../../../release/schedule.md) för att planera nästa uppgradering och förbereda i förväg.

▢ Diskutera vilken version du tror att du kommer att anta (fullständig eller enbart säkerhetsrelaterad) baserat på förväntade behov.

▢ Avsätta en budget och en teamkapacitet för uppgraderingen.

## Tredjepartsintegreringar

▢ Granska aktuella integreringar från Adobe Commerce och deras underhållsperioder för ett år och överväg att anpassa uppgraderingsarbetet efter ditt underhållsschema.

## Omfattning och driftsättningsplanering

▢ Tidig tillgång

- Partnern deltar i [Beta](../../../release/beta.md)
- Beta release note review.

▢ Godkänn budget, tidslinje, omfattning.

▢ [Kompatibilitetsverktyget för uppgradering](../../../upgrade/upgrade-compatibility-tool/overview.md)

▢ Överväg att använda uppgraderingen för att åtgärda problem som identifieras av [Site Wide Analysis Tool](../../../tools/site-wide-analysis-tool/intro.md).

▢ dokumentberoenden och eventuella ändringar i den tekniska stacken som krävs, till exempel PHP- eller Elastic Search-versioner.

▢ Samla projektteamet med Adobe Commerce certifieringar.

▢ Skapa kommunikationsplan för intressenter.

Underhållsperiod för ▢ om driftstopp förväntas.

▢ Granska och godkänn teststrategin. Överväg att använda Adobe Commerce [testramverk](https://developer.adobe.com/commerce/testing/) eller en tredjepartsserie för automatisering.

▢ Bekräfta att alla tillägg och anpassningar är kompatibla.

▢ Granska och uppdatera spelboken efter start. Den används om problem upptäcks under eller efter uppgraderingen.

## Driftsättning av Post

▢ Övervaka webbplatsen för att hitta problem - prestanda, orderhantering, analyser och annat.

▢ Utför en Adobe Commerce [säkerhetssökning](https://account.magento.com/scanner/dashboard/) eller annan tredjepartssökning och granska potentiella säkerhetsproblem.

▢ Utför en retroaktiv översikt med alla intressenter och dokumentera vad som gick bra, vad som inte gick bra och hur du skulle förbättra.

▢ Ändra din plan för nästa uppgradering med lärdomar.
