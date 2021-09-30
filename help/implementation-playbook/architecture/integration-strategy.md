---
title: Integreringsstrategi för Adobe Commerce
description: Granska integreringsstrategier och alternativ för implementeringen av Adobe Commerce.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '518'
ht-degree: 0%

---


# Integreringsstrategi för Adobe Commerce

Möjligheten att integrera er plattform är&quot;icke-förhandlingsbar&quot;. Företagen vill att deras e-handelsplattformar ska vara tillgängliga från en mängd olika kontaktytor och vara sömlöst integrerade i deras tekniksystem, särskilt deras ERP. Anpassningsbarhet, global skalbarhet och prisvärdhet spelar också en viktig roll vid köp av färdiga plattformar.

En helhetsintegrering för både butiks- och backend-system stöds av prestandan för GraphQL-API:er, omfattande REST-API:er och batchfilimport mellan Adobe Commerce och andra system eller tjänster.

API:t för GraphQL för Adobe Commerce ger omfattande täckning för butiker som du kan använda för att integrera med andra butiker, bland annat:

- Digital Experience platforms (DXPs) som Adobe Experience Manager och Bloomreach
- CMS-system (Content Management System) som Drupal och WordPress
- Modern anpassad butiksapplikation som Adobe Commerce, PWA Studio och Vue Storefront

GraphQL ger ett effektivt, kanalspecifikt svar, ingen överhämtning av data och en smidig driftsättning av nya kontaktytpunkter. Det väljs också ofta för integrering med försäljningskanaler som mobilappar, POS, IoT, sociala kanaler och butikskanaler som Facebook, Google, Instagram, WeChat och TikTok.

Adobe Commerce REST API innehåller omfattande funktioner för systemkonfiguration och datahantering, inklusive produkt och katalog. kundvagn, offert och utcheckning, kunder, konton och företag, och beställningar och returer. REST-API:er stöder massåtgärder, olika autentiseringslägen och detaljerad auktorisering, så REST-API:er väljs ofta för integrering med företagssystem, inklusive:

- ERP-system (Enterprise resource planning) som SAP
- Produktinformationshanteringssystem (PIM) som Akeneo
- CRM-system som Salesforce
- Orderhanteringssystem som MOM, Manhattan och SAP
- WMS (Warehouse Management System) eller tredjepartslogistik (3PL) som Oracle, NetSuite och SAP WM
- Konfigurera, Pris, Offert (CPQ) som SalesforceCPQ
- Digital Asset Management (DAM), t.ex. Adobe DAM.

Batchfilimport är också ett bra alternativ för att integrera företagssystem som ERP och PIM, eftersom dessa data inte ändras särskilt ofta och du ofta får bättre prestanda vid schemalagd filimport. Batchfilsimporten väljs därför oftast för gruppdatasynkronisering varje dag/vecka och månatliga fullständiga datasynkroniseringar, medan REST API:er väljs för stegvis synkronisering av dataändringar, vilket ger bättre prestanda. Detta betraktas också som ett schemalagt jobb, men kan utföras ofta - eventuellt var 15:e minut till 1 timme - beroende på företagets behov.

## Integreringsalternativ

Adobe Commerce erbjuder tre flexibla integreringsalternativ:

- Direkt integrering mellan system och system med färdiga anslutningar. Vissa system kanske redan har Adobe Commerce-tillägg på Commerce Marketplace eller på sin egen webbplats.

- System-till-system-integrering via anpassad mellanvara. Den anpassade mellanprogramslösningen används för mappning, översättning och hantering av processdata.

- System-till-system-integrering via iPaaS (Integration Platform-as-a-Service), även kallat EAI (Enterprise Application Integration Platform), som Mulesoft, Boomi och Software AG.

![Integreringsalternativ för Adobe Commerce](../../assets/playbooks/integration-options.svg)

Även om integreringar i realtid vanligtvis önskas är det inte nödvändigt för vissa scenarier. Adobe Commerce stöder direkt RabbitMQ som meddelandebuss för att aktivera asynkrona processer, vilket rekommenderas för vissa data som inte behöver utväxlas i realtid, utan istället för att uppdateras med batchfilsutbyte eller REST-batchdataprocess-API för asynkron bearbetning.
