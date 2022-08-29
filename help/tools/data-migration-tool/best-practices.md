---
title: Bästa tillvägagångssätt för datamigrering
description: Följ de bästa sätten för datamigrering för att säkerställa en lyckad uppgradering från Magento 1 till Magento 2.
source-git-commit: d609c497fdf00c5e5f975a5679b1d072cec4f8a2
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Bästa tillvägagångssätt för datamigrering

I det här avsnittet finns de bästa rekommendationerna för att snabba upp och förenkla din migrering samt riktlinjer för hur lång tid det kan ta.

* **Använd en kopia av databasen från en Magento 1-instans** när du utför migreringstestning. Använd inte produktionsinstansen för din Magento 1-butiksdatabas.

* **Ta bort inaktuella och redundanta data** från din Magento 1-databas före migrering.

Sådana data kan vara loggar, ordercitat, nyligen visade eller jämförda produkter, besökare, händelsespecifika kategorier och kampanjregler.

* **Följ [allmänna regler för lyckad migrering](migrate-data/overview.md#migration-overview)**.

* För att förbättra prestanda **aktivera `direct_document_copy` option** i `config.xml` fil:

   ```xml
   <direct_document_copy>1</direct_document_copy>
   ```

>[!NOTE]
>
>Både Magento 1- och Magento 2-databaser måste finnas på samma MySQL-server och databaskontot måste ha tillgång till båda databaserna.

## Uppskattningar av prestandatestning

Adobe har testat datamigrering på följande system:

* Virtual Box VM, CentOS 6, 2,5 GB RAM, CPU 1 core 2,6 GHz
* Databas med 177 000 produkter, 355 000 order och 214 000 kunder

## Resultat

* Inställningsmigreringstid: ~10 minuter
* Datamigreringstid: ~9 timmar (alla data utom URL-omskrivningar, ~85 % av totala data)
* Uppskattning av driftstopp för webbplatsen: några minuter för att indexera om och ändra DNS-inställningarna. Ytterligare tid krävs för att värma upp sidcachen.
