---
title: Optimera bilder för en mer responsiv webbplats
description: Lär dig hur du optimerar bilder och använder Snabb bildoptimering för att optimera svarstiden på dina Adobe Commerce-sajter.
role: Developer, Admin
feature: Best Practices
feature-set: Commerce
exl-id: ada8b987-97ed-4232-9e1b-7e0a791a0807
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '210'
ht-degree: 0%

---

# Optimera bilder för en mer responsiv webbplats

För distributioner av molninfrastruktur kan du förbättra svarstiden genom att optimera bilder innan du överför dem. Använd sedan Snabb bildoptimering för att snabba upp bildleveransen och förenkla underhållet av bildkällorna.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

Adobe Commerce i molninfrastruktur


## Optimera och komprimera bilder

Innan du överför bilder till dina Commerce-sajter måste du optimera och komprimera dem för att balansera prestanda med visningskvalitet. Detta bidrar till att öka utrymmet och minska sidinläsningstiden.

- PNG-formatet ger bilder i mindre storlek för bilder med stora enfärgade områden.

- JPEG-formatet ger bilder med mindre storlek för alla andra bildtyper. Använd den högsta komprimeringen (utan märkbar försämring). Det är vanligtvis 60 till 80 procent.

## Aktivera och konfigurera snabb bildoptimering

När du har konfigurerat snabbtjänsten för ditt Adobe Commerce Cloud-projekt kan du gå till [Snabb bildoptimering](https://devdocs.magento.com/cloud/cdn/fastly-image-optimization.html) för instruktioner om hur du aktiverar och konfigurerar bildoptimering.

## Ytterligare information

- [Konfigurera snabbt](https://devdocs.magento.com/cloud/cdn/configure-fastly.html)
- [Dåligt optimerade bilder kan leda till prestandaproblem](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/file-storage-low-specific-page-loads-are-slow.html)
