---
title: Infrastrukturtekniker i molnet
description: Ta en närmare titt på samlingen av tekniklösningar som Adobe använder för Adobe Commerce i molninfrastruktur.
exl-id: de1b3a64-d32b-455f-bdb0-ad883dedd6d4
feature: Cloud
source-git-commit: c737a8e902c960c933e54e2521107475bb1e5a22
workflow-type: tm+mt
source-wordcount: '128'
ht-degree: 0%

---


# Technologies

Adobe Commerce i molninfrastruktur använder flera programlösningar för att stödja plattformen. Se följande avsnitt i _Molnguide_ för mer information:

- [Miljöarkitektur för proffs](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/pro-architecture.html#production-technology-stack)
- [Arkitektur för startmiljö](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/architecture/starter-architecture.html#production-and-staging-technology-stack)

## Funktioner och fördelar

- Tre dedikerade instanser i ett virtuellt privat moln (VPC) med en elastisk belastningsutjämnare över tre separata tillgänglighetszoner eller datacentraler.
- Högre återhämtningsförmåga mot händelser som kan göra att en enda instans misslyckas. Exempel: ett avbrott i en hel tillgänglighetszon eller ett datacenter för AWS.
- Nollställ skalning av driftsavbrott i hela stacken, inklusive webb, cachning, sökning och databas.
