---
title: '"Den [!UICONTROL Infra] tab"'
description: The [!UICONTROL Infra] tabben isolerar problem och orsaker till infrastrukturproblem.
source-git-commit: b0d80d97f60b24bc801063dc484f3a495cf0a036
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---


# The [!UICONTROL Infra] tab

The **[!UICONTROL Infra]** tabben isolerar problem och orsaker till infrastrukturproblem. Dessutom beskrivs de ramar du kan se på fliken.

## [!UICONTROL Service Alerts – Infrastructure Alerts by Application name]

![Tjänstvarningar](../../assets/tools/observation-for-adobe-commerce/service-alerts.jpg)

The **[!UICONTROL Service Alerts – Infrastructure Alerts by Application name]** graf visar de servicemeddelanden som samlats in av [!DNL New Relic] infrastrukturagent. Detta visar omstarter av tjänster, som ofta är kopplade till distributioner.

## [!UICONTROL Inode usage by mount]

![Inodanvändning vid montering](../../assets/tools/observation-for-adobe-commerce/inode-usage-mount.jpg)

The **[!UICONTROL Inode usage by mount]** bildrutan visar hur noden används vid montering över den valda tidsramen. Även om det kan finnas mycket lagringsutrymme utan kostnad, så visar det sig att det inte finns något tillgängligt lagringsutrymme om noden får slut på noder. Om du tar bort filer (särskilt små filer) frigörs både utrymme och så att det blir möjligt att ta bort noder.

## [!UICONTROL vCPU tier view over timeline GREATER 2 weeks]

![Vy över CPU-nivå över tidslinjen GREATER 2 veckor](../../assets/tools/observation-for-adobe-commerce/vCPU-tier.jpg)

The **[!UICONTROL vCPU tier view over timeline GREATER 2 weeks]** bildrutan visar vyn vCPU-nivå över den valda tidsramen på mer än två veckor. Den här bildrutan tittar på antalet vCPU:er som tilldelats till [!DNL New Relic] programnamn visas.

## [!UICONTROL vCPU tier view over timeline]

![Vy över CPU-nivå över tidslinjen](../../assets/tools/observation-for-adobe-commerce/vcpu-tier-24.jpg)

The **[!UICONTROL vCPU tier view over timeline]** bildrutan visar vyn för vCPU-nivå över den valda tidsramen på mer än 24 timmar. Den här bildrutan tittar på antalet vCPU:er som tilldelats till [!DNL New Relic] programnamn visas. Den visar både klusteruppstorlekar och nedstorlekar.

## [!UICONTROL vCPU tier view over timeline BY NODE]

![Vy över processornivå över tidslinjen av NODE](../../assets/tools/observation-for-adobe-commerce/infra_by_node.png)

The **[!UICONTROL vCPU tier view over timeline BY NODE]** bildrutan visar vyer av vCPU-nivån över den valda tidsramen per nod. Den här bildrutan är användbar när du vill identifiera förlust av noder eller när noderna är storleksanpassade eller nedstorleksändrade. Vyn över CPU-nivå över tidslinjen VIA NODE, ska titta på tidslinjen mindre än 24 timmar.

## [!UICONTROL Instance details]

![Instansinformation](../../assets/tools/observation-for-adobe-commerce/instance-details.jpg)

The **[!UICONTROL Instance details]** tabellen visar instansinformation för varje [!DNL New Relic] program.

## [!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]

![non-responsive-node](../../assets/tools/observation-for-adobe-commerce/non-responsive-node.jpg)

The **[!UICONTROL Logging, if there is a broken line for a node, it indicates non-responsive node during that time period]** bildrutan visar noder som inte svarar under en tidsperiod.