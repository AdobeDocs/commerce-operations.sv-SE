---
title: Cloud Infrastructure-miljöer
description: Använd rätt miljöer för rätt användningsområden.
source-git-commit: 748c302527617c6a9bf7d6e666c6b3acff89e021
workflow-type: tm+mt
source-wordcount: '221'
ht-degree: 0%

---


# Miljö

Adobe Commerce on cloud infrastructure Pro-arkitekturen stöder miljöer som du kan använda för att utveckla, testa och starta din butik. Varje miljö innehåller en databas och en webbserver. De fyra miljöer som Adobe Commerce utnyttjar är:

- **Integrering** - Ger en enda gren av miljön och du kan skapa upp till fyra ytterligare grenar av miljön. Detta tillåter högst fem aktiva grenar som distribueras till behållare av typen Platform-as-a-Service (PaaS).

- **Mellanlagring** - Tillhandahåller en enda miljögren som distribueras till dedikerade behållare för infrastruktur som en tjänst (IaaS).

- **Produktion** - En enda miljögren som distribueras till dedikerade behållare för infrastruktur som en tjänst (IaaS).

- **Global Överordnad** - Tillhandahåller en överordnad gren som distribuerats till behållare för Platform-as-a-Service (PaaS).

![Diagram som visar relationen mellan Adobe Commerce-molnmiljöer](../../../assets/playbooks/environment-diagram.svg)

## Git-grenar

Integreringsmiljön erbjuder en enda basintegreringsgren som innehåller din Adobe Commerce-kod som distribuerats till paaS-behållare (Platform-as-a-Service).

Adobe Commerce i molninfrastrukturmiljöer stöder en flexibel, kontinuerlig integreringsprocess. Börja med att klona integrationsgrenen till den lokala projektmappen. Skapa en ny gren, eller flera grenar, för att utveckla nya funktioner, konfigurera ändringar och lägga till tillägg. Med en utvecklad kodgren och motsvarande konfigurationsfiler är dina kodändringar klara att sammanfogas med integrationsgrenen för mer omfattande testning.

![Bild som visar den Git-baserade förgreningsstrategin för molnmiljöer i Adobe Commerce](../../../assets/playbooks/branching-diagram.svg)
