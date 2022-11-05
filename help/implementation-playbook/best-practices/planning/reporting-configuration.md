---
title: Bästa praxis för rapportkonfiguration
description: Optimera webbplatsens prestanda genom att ta bort rapportmodulen om du inte använder den.
role: Admin
feature: Best Practices
feature-set: Commerce
source-git-commit: 85f9355d0e8c704be3760334b07414d3e15b3b97
workflow-type: tm+mt
source-wordcount: '133'
ht-degree: 0%

---


# Bästa tillvägagångssätt för rapportkonfiguration

Om ditt företag inte behöver funktioner för rapportering eller dynamiska kundsegment inaktiverar du [Rapportfunktioner](https://docs.magento.com/user-guide/configuration/general/reports.html) för att förbättra butikens prestanda.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Inaktivera rapportering

Om du inte använder Rapporter eller dynamiska kundsegment inaktiverar du rapportfunktionen.

1. Navigera från administratören till **Lager** > **Inställningar** > **Konfiguration** > **Allmänt** > **Rapporter**.
1. Under **Allmänna alternativ**, ange **Aktivera rapporter** till *Nej*.
1. Töm cacheminnet genom att köra `php bin/magento cache:flush` eller i Admin under **System** > **verktyg** > **Cachehantering**.

## Ytterligare information

- [Generera rapporter i Adobe Commerce](https://docs.magento.com/user-guide/reports.html)
- [Kunddynamiska segment](https://docs.magento.com/user-guide/marketing/customer-segments.html)