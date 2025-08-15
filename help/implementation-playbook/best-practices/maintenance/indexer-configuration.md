---
title: Bästa praxis för konfiguration av indexerare
description: Underhåll och optimera webbplatsens prestanda genom att följa vedertagna standarder för indexerarkonfiguration.
role: Admin, User
feature: Best Practices
exl-id: b35806f9-4bc6-407e-bedd-5ce3f09c1b9f
source-git-commit: 29168544e3a33b874b104f308bd53cb475ac2638
workflow-type: tm+mt
source-wordcount: '320'
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
- Ställ in indexerarna på _[!UICONTROL Update on Schedule]_&#x200B;för stora webbplatser och webbplatser med frekventa uppdateringar och stor trafik. Se [Indexhantering](https://experienceleague.adobe.com/sv/docs/commerce-admin/systems/tools/index-management#change-the-index-mode).
- Följ de [bästa metoderna](../../../performance/configuration.md) för prestanda när du hanterar index.

>[!IMPORTANT]
>
>Indexerarens [!DNL Customer Grid]-beteende ändrades i 2.4.8:
>
>- **Före 2.4.8**: [!DNL Customer Grid]-indexeraren kan bara indexeras om med alternativet [!UICONTROL Update on Save] och stöder inte alternativet [!UICONTROL Update by Schedule].
>- **2.4.8 och senare**: [!DNL Customer Grid]-indexeraren har stöd för både [!UICONTROL Update on Save]- och [!UICONTROL Update by Schedule]-lägen, och standardvärdet är [!UICONTROL Update by Schedule].

## Ytterligare information

- [Indexhantering för administratörer](../../../configuration/cli/manage-indexers.md#configure-indexers)
- [Indexhantering med Magento CLI](https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/cli/manage-indexers.html?lang=sv-SE)
- [Indexeringsöversikt för utvecklare](https://developer.adobe.com/commerce/php/development/components/indexing/)
