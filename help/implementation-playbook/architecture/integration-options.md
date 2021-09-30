---
title: Integreringsalternativ för Adobe Commerce
description: Utforska dina alternativ för att integrera andra system med implementeringen av Adobe Commerce.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '581'
ht-degree: 0%

---


# Typical integration points and dataflows

Det finns två huvudstrategier för integreringar och dataflöden, som är mycket lika men har en viktig skillnad.

## Monolitisk

I följande diagram beskrivs en monolitisk metod som använder Adobe Commerce som både backend-system och storefront-program:

![Monolitdiagram för Adobe Commerce](../../assets/playbooks/integration-monolith.svg)

## Headless

I följande diagram beskrivs en headless-metod som använder Adobe Commerce som backend-system integrerat med en DXP/CMS/anpassad applikation som storefront-applikation:

![Diagram utan rubrik för Adobe Commerce](../../assets/playbooks/integration-headless.svg)

Den enda skillnaden mellan det monolitiska och det headless-baserade tillvägagångssättet är integrering av butiker, vilket påverkar användarupplevelsen för kunderna. Monolithic använder Adobe Commerce storefront direkt för att integrera med tredjepartstjänster, medan headless är beroende av sin egen butik för att anpassa och integrera med samma tjänster. Vissa tjänster som betalning och enkel inloggning (SSO) behöver både butiks- och Adobe Commerce-anpassning för att slutföra integreringsflödet.

## Tredjepartssystem

Vissa populära tjänster har redan utökade möjligheter att stödja lösningar för Adobe Commerce eller populära butikslösningar som PWA Studio, Adobe Experience Manager och Vue Storefront, som finns på deras utökade marknadsplats eller från andra tredjepartswebbplatser. Even if there is no existing extension, the effort to implement the integration between Adobe Commerce and other headless storefronts are similar. Alla tredjepartstjänster har vanligtvis dokument som förklarar hur de kan integreras med dem. Dessa tjänster är bara några exempel. olika länder och marknader kan ha olika val.

## Företagsintegreringar

För företagssystemintegrationer, som också vanligtvis kallas backend-integrationer, påverkas dataflödet. Med utgångspunkt i olika affärstyper och behov kan programmet använda tre olika integreringsalternativ, som vi redan har infört.

Produktobligatoriska data som SKU, lager och baspriser kommer vanligtvis från ERP, medan försäljningspriserna vanligtvis hanteras av varje försäljningskanal (till exempel Adobe Commerce) eller CPQ (B2B eller privat försäljning). Eftersom obligatoriska produktdata (utom lager) inte ändras särskilt ofta är det bästa sättet att använda schemalagda batchuppdateringar via REST API eller bulkfilsimport. För lager är det bästa sättet att ha en fullständig daglig uppdatering för produktlager som delas med olika försäljningskanaler för att undvika överförsäljning. Dessutom har ni stegvisa förändringar från ERP inom 24 timmar.

Produktkataloger, metadata och marknadsföringsmaterial kan hanteras separat av varje försäljningskanal (till exempel Adobe Commerce) eller från en central PIM. Eftersom metadata inte ändras så ofta är det bästa sättet att använda schemalagda batchuppdateringar via REST API eller bulkfilsimport.

Beställningsdata omfattar beställnings-, offert- (B2B), leverans-, retur- och utbytesdata som vanligtvis hanteras från ett centraliserat OMS- och WMS-system. Beställningsdata ska synkroniseras så snart som möjligt, så REST API är vanligtvis det bästa alternativet. För bättre prestanda bör du överväga att minska antalet API-anrop. För orderstatus, leveranser, retur och datautbyte bör du överväga att schemalägga REST-API:er för batchuppdatering i timmar eller minuter.

B2B data is usually managed from a centralized CRM. Ett realtids-API används för att verifiera befintliga kunder och skapa nya kunder. För B2B kan det krävas fler API:er för att synkronisera olika anställda, grupper och prislistor mellan Adobe Commerce och CRM eller CPQ.

Det finns andra systemintegreringar som eDM för e-postmarknadsföring och affärsintelligens för affärsdataanalys, som vanligtvis görs antingen via REST API eller export/import av filer, som vanligtvis stöds av befintliga tillägg.
