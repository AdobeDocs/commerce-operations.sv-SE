---
title: Bästa praxis för rapportkonfiguration
description: Optimera webbplatsens prestanda genom att ta bort rapportmodulen om du inte använder den.
role: Admin
feature: Best Practices, Configuration
exl-id: 8c991b8a-affb-4a9e-9383-671f595ff89e
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '121'
ht-degree: 0%

---

# Bästa tillvägagångssätt för rapportkonfiguration

Om ditt företag inte behöver funktioner för rapportering eller dynamiska kundsegment inaktiverar du funktionen [Rapporter](https://experienceleague.adobe.com/sv/docs/commerce-admin/config/general/reports) för att förbättra butikens prestanda.

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

- Adobe Commerce i molninfrastruktur
- Adobe Commerce lokalt

## Inaktivera rapportering

Om du inte använder Rapporter eller dynamiska kundsegment inaktiverar du rapportfunktionen.

1. Gå till **Lagrar** > **Inställningar** > **Konfiguration** > **Allmänt** > **Rapporter** från Admin.
1. Under **Allmänna alternativ** anger du **Aktivera rapporter** till *Nej*.
1. Rensa cacheminnet genom att köra `php bin/magento cache:flush` eller i administratören under **System** > **Verktyg** > **Cachehantering**.

## Ytterligare information

- [Generera rapporter i Adobe Commerce](https://experienceleague.adobe.com/sv/docs/commerce-admin/start/reporting/reports-menu)
- [Kundens dynamiska segment](https://experienceleague.adobe.com/sv/docs/commerce-admin/customers/segments/customer-segments)
