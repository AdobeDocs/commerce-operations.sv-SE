---
title: Bästa praxis för tillägg
description: Lär dig hur du undviker prestandaproblem som orsakas av Adobe Commerce-tillägg från tredje part.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 510f2d4cdaec1034cb04a01fab0948c4261c6d10
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---


# Bästa praxis för tillägg

Adobe Commerce tredjepartstillägg (moduler) kan orsaka olika problem som kan påverka butikens prestanda negativt. Du kan undvika de här problemen genom att följa de bästa metoderna:

- Hämta och köpa tillägg från tredje part från en betrodd källa, som [Commerce Marketplace](https://marketplace.magento.com/extensions.html).
- Uppdatera alla tillägg från tredje part till den senaste versionen.
- Om du inte kan uppdatera tillägg från tredje part bör du använda andra tillägg.
- När du planerar en uppgradering till en ny version av Adobe Commerce kontrollerar du att installerade tillägg från tredje part är kompatibla med den nya versionen och uppgraderar tilläggen om det behövs.

>[!NOTE]
>
> Alla tillägg som är tillgängliga på Adobe Commerce Marketplace krävs för att bibehålla kompatibiliteten med nya Commerce-versioner. Se [Versionskompatibilitet](https://developer.adobe.com/commerce/marketplace/guides/sellers/compatibility/releases/).

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Ytterligare information

- [Bästa tillvägagångssätt för planering av uppgraderingar](../../../upgrade/prepare/best-practices.md)
- Använda tillägg från tredje part med Adobe Commerce i molninfrastrukturen
   - [Teknik och krav - Utveckling och testning](https://devdocs.magento.com/cloud/requirements/cloud-requirements.html#cloud-req-devtest)
   - [Varför testa fullt ut i Integration and Staging?](https://devdocs.magento.com/cloud/live/live.html#whytest)
