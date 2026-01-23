---
title: Bästa praxis för tillägg
description: Lär dig hur du undviker prestandaproblem som orsakas av Adobe Commerce-tillägg från tredje part.
role: Admin
feature: Best Practices, Extensions
exl-id: 95d2c7bf-fd2f-4c98-8293-96d69b86341f
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '193'
ht-degree: 0%

---

# Bästa praxis för tillägg

Adobe Commerce tredjepartstillägg (moduler) kan orsaka olika problem som kan påverka butikens prestanda negativt. Du kan undvika de här problemen genom att följa de bästa metoderna:

- Utveckla dina Commerce-integreringar och anpassningar med [utbyggbarhet som inte har bearbetats](https://developer.adobe.com/commerce/extensibility/) så långt det är möjligt för att underlätta underhåll och uppgradering.
- Hämta och köp tillägg från tredje part från en betrodd källa, som [Commerce Marketplace](https://commercemarketplace.adobe.com//extensions.html).
- Uppdatera alla tillägg från tredje part till den senaste versionen.
- Om du inte kan uppdatera tillägg från tredje part bör du använda andra tillägg.
- När du planerar en uppgradering till en ny version av Adobe Commerce kontrollerar du att installerade tillägg från tredje part är kompatibla med den nya versionen och uppgraderar tilläggen om det behövs.

>[!NOTE]
>
> Alla tillägg som är tillgängliga på Adobe Commerce Marketplace krävs för att bibehålla kompatibiliteten med nya Commerce-utgåvor. Se [Versionskompatibilitet](https://developer.adobe.com/commerce/marketplace/guides/sellers/compatibility/releases/).

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Ytterligare information

- [Bästa tillvägagångssätt för planering av uppgraderingar](../../../upgrade/prepare/best-practices.md)
- Använda tillägg från tredje part med Adobe Commerce i molninfrastrukturen
   - [Teknik och krav - Utveckling och testning](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/develop/overview#cloud-req-devtest)
   - [Varför ska du testa fullständigt i Integrering och mellanlagring?](https://experienceleague.adobe.com/sv/docs/commerce-cloud-service/user-guide/launch/overview#why-test-fully-in-integration-staging-and-production)
