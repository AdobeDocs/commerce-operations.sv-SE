---
title: Cloud Infrastructure-miljöer
description: Använd rätt miljöer för rätt användningsområden.
exl-id: 0c36145f-8de2-45e5-9050-9acbc9fb6100
feature: Cloud
source-git-commit: 94d7a57dcd006251e8eefbdb4ec3a5e140bf43f9
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---

# Miljö

Adobe Commerce i molninfrastruktur Pro-arkitekturen stöder miljöer som du kan använda för att utveckla, testa och lansera din butik. Varje miljö innehåller en databas och en webbserver. De fyra miljöer som Adobe Commerce utnyttjar är:

- **Integrering**—Har en enda miljögren och du kan skapa upp till fyra ytterligare miljögrenar. Detta tillåter högst fem aktiva grenar som distribueras till behållare av typen Platform-as-a-Service (PaaS).

- **Mellanlagring**—Tillhandahåller en enda miljögren som distribueras till dedikerade behållare för infrastruktur som en tjänst (IaaS).

- **Produktion**—Tillhandahåller en enda miljögren som distribueras till dedikerade behållare för infrastruktur som en tjänst (IaaS).

- **Global mallsida**—Tillhandahåller en huvudgren som distribuerats till behållare av typen Platform-as-a-Service (PaaS).

![Bild som visar relationen mellan Adobe Commerce molnmiljöer](../../../assets/playbooks/environment-diagram.svg)

## Git-grenar

Integreringsmiljön innehåller en enda basintegreringsgren med din Adobe Commerce-kod som distribuerats till behållare för Platform-as-a-Service (PaaS).

Adobe Commerce i molninfrastrukturmiljöer har stöd för en flexibel, kontinuerlig integreringsprocess. Börja med att klona integrationsgrenen till den lokala projektmappen. Skapa en ny gren, eller flera grenar, för att utveckla nya funktioner, konfigurera ändringar och lägga till tillägg. Med en utvecklad kodgren och motsvarande konfigurationsfiler är dina kodändringar klara att sammanfogas med integrationsgrenen för mer omfattande testning.

![Bild som visar den Git-baserade förgreningsstrategin för Adobe Commerce molnmiljöer](../../../assets/playbooks/branching-diagram.svg)
