---
title: Bästa praxis för konfiguration av indexerare
description: Underhåll och optimera webbplatsens prestanda genom att följa vedertagna standarder för indexerarkonfiguration.
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '280'
ht-degree: 0%

---

# Bästa tillvägagångssätt för indexerarkonfiguration

Om du vill optimera och underhålla platsprestanda granskar och uppdaterar du indexerarkonfigurationen med hjälp av de bästa prestandametoderna som beskrivs i den här artikeln.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Ange att indexerare ska uppdateras i ett schema

Adobe Commerce har två typer av indexeringslägen: [!UICONTROL Update on Save] (standardinställning) och [!DNL Update on Schedule].

- **[!UICONTROL Update on Save]** Läget uppdaterar index omedelbart när katalogen eller andra data ändras. Om en Admin-användare till exempel lägger till nya produkter i en kategori omindexeras kategoriproduktindexet omedelbart när uppdateringen sparas.

- **[!UICONTROL Update on Schedule]** I lagras information om datauppdateringar, och omindexeringsåtgärder och indexuppdateringar hanteras av ett cron-jobb som körs i bakgrunden med schemalagda intervall.

Att ha en stor butik med flera administratörer som arbetar i bakgrunden eller har många import- och exportfunktioner utlöser ofta indexuppdateringar. Om platsindexkonfigurationen är inställd på [!UICONTROL Update on Save] ofta återkommande omindexering försämrar databasens prestanda, vilket saktar ned webbplatsens prestanda och orsakar långa förseningar i omindexeringsprocessen, särskilt för stora butiker.

Så här maximerar du webbplatsens prestanda:

- Granska indexkonfigurationen.
- Ställ in indexerarna på _[!UICONTROL Update on Schedule]_för stora webbplatser och webbplatser med ofta återkommande uppdateringar och stor trafik. Se [Indexhantering](https://docs.magento.com/user-guide/system/index-management.html#change-the-index-mode).
- Följ [bästa praxis](../../../performance/configuration.md) för att hantera index.

>[!IMPORTANT]
>
>The [!DNL Customer Grid] kan bara indexeras om med [!UICONTROL Update on Save] alternativ. Indexet stöder inte `Update by Schedule` alternativ.

## Ytterligare information

- [Indexhantering för administratörer](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Indexhantering med Magento CLI](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [Indexeringsöversikt för utvecklare](https://developer.adobe.com/commerce/php/development/components/indexing/)
