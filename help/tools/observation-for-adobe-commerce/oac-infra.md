---
title: Fliken  [!DNL Infra]
description: Fliken  [!DNL Infra] isolerar problem och orsaker till infrastrukturproblem.
exl-id: 45f24177-3264-4848-99bc-951be32c1f7b
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# Fliken [!DNL Infra]

Fliken **[!DNL Infra]** isolerar problem och orsaker till infrastrukturproblem. Dessutom beskrivs de ramar du kan se på fliken.

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![Tjänstvarningar](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

Diagrammet **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** visar de tjänstaviseringar som samlats in av infrastrukturagenten [!DNL New Relic]. Detta visar omstarter av tjänster, som ofta är kopplade till distributioner.

## [!UICONTROL Inode usage by mount]

![Inodanvändning av montering](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

Bildrutan **[!UICONTROL Inode usage by mount]** visar [!DNL inode]-användning genom montering över den valda tidsramen. Även om det kan finnas mycket ledigt lagringsutrymme, kommer det att saknas tillgängligt lagringsutrymme om [!DNL inodes] tar slut för en nod. Om du tar bort filer (särskilt små) frigörs både utrymme och [!DNL inodes] blir tillgänglig.

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![Vyn vCPU-nivå över tidslinjen GREATER 2 veckor](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

Bildrutan **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** visar en vCPU-nivåvy över den valda tidsramen på mer än två veckor. Den här bildrutan tittar på antalet vCPU:er som har tilldelats programnamnet [!DNL New Relic] som visas.

## [!UICONTROL vCPU tier view over timeline]

![Vyn vCPU-nivå över tidslinjen](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

Bildrutan **[!UICONTROL vCPU tier view over timeline]** visar vCPU-nivåvy över den valda tidsramen på mer än 24 timmar. Den här bildrutan tittar på antalet vCPU:er som har tilldelats programnamnet [!DNL New Relic] som visas. Den visar både klusteruppstorlekar och nedstorlekar.

## [!UICONTROL vCPU tier view over timeline BY NODE]

![Vyn vCPU-nivå över tidslinjen av NODE](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

Bildrutan **[!UICONTROL vCPU tier view over timeline BY NODE]** visar vCPU-nivåvyer över den valda tidsramen per nod. Den här bildrutan är användbar när du vill identifiera förlust av noder eller när noderna är storleksanpassade eller nedstorleksändrade. Vyn över CPU-nivå över tidslinjen VIA NODE, ska titta på tidslinjen mindre än 24 timmar.

## [!UICONTROL Instance details]

![Instansinformation](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

Tabellen **[!UICONTROL Instance details]** visar instansinformation för varje [!DNL New Relic]-program.

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![ingen responsiv-nod](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

Bildrutan **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** visar noder som inte svarar under en tidsperiod.
