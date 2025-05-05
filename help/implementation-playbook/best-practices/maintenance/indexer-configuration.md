---
title: Bästa praxis för konfiguration av indexerare
description: Underhåll och optimera webbplatsens prestanda genom att följa vedertagna standarder för indexerarkonfiguration.
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '296'
ht-degree: 0%

---

# Bästa tillvägagångssätt för indexerarkonfiguration

Om du vill optimera och underhålla platsprestanda granskar och uppdaterar du indexerarkonfigurationen med hjälp av de bästa prestandametoderna som beskrivs i den här artikeln.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Ange att indexerare ska uppdateras i ett schema

Adobe Commerce har två typer av indexeringslägen: [!UICONTROL Update on Save] och [!DNL Update on Schedule].

- **[!UICONTROL Update on Save]**-läget uppdaterar index omedelbart när katalogen eller andra data ändras. Om en Admin-användare till exempel lägger till nya produkter i en kategori omindexeras kategoriproduktindexet omedelbart när uppdateringen sparas.

- **[!UICONTROL Update on Schedule]**-läget lagrar information om datauppdateringar, och omindexeringsåtgärder och indexuppdateringar hanteras av ett cron-jobb som körs i bakgrunden med schemalagda intervall. Kronijobbet utför inte alltid en indexering varje gång det körs. Den indexeras bara om det finns nya poster i indexerarens ändringsloggar (det finns t.ex. en eftersläpning i indexerarna).

Att ha en stor butik med flera administratörer som arbetar i bakgrunden eller har många import- och exportfunktioner utlöser ofta indexuppdateringar. Om platsindexkonfigurationen är inställd på läget [!UICONTROL Update on Save] försämras databasprestanda ofta vid omindexering, vilket försämrar webbplatsens prestanda och orsakar långa förseningar i omindexeringsprocessen, särskilt för stora butiker.

Så här maximerar du webbplatsens prestanda:

- Granska indexkonfigurationen.
- Ställ in indexerarna på _[!UICONTROL Update on Schedule]_&#x200B;för stora webbplatser och webbplatser med frekventa uppdateringar och stor trafik. Se [Indexhantering](https://experienceleague.adobe.com/en/docs/commerce-admin/systems/tools/index-management#change-the-index-mode).
- Följ de [bästa metoderna](../../../performance/configuration.md) för prestanda när du hanterar index.

>[!IMPORTANT]
>
>[!DNL Customer Grid] kan bara indexeras om med alternativet [!UICONTROL Update on Save]. Indexet stöder inte alternativet `Update by Schedule`.

## Ytterligare information

- [Indexhantering för administratörer](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Indexhantering med Magento CLI](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html)
- [Indexeringsöversikt för utvecklare](https://developer.adobe.com/commerce/php/development/components/indexing/)
