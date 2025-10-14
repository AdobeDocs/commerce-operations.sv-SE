---
title: Åtkomst till [!DNL Cloud Automation Patching Service (CAPS)]
description: Lär dig hur du kommer åt och använder  [!DNL Cloud Automation Patching Service (CAPS)]
hide: true
hidefromtoc: true
source-git-commit: ca388bd78affd4def19a5539d8529f2563d35e8c
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Åtkomst till [!DNL Cloud Automation Patching Service (CAPS)]

## Förutsättningar

[!DNL CAPS] använder den rollbaserade åtkomstkontrollen från Adobe Commerce Cloud. Din åtkomstnivå i molnkonsolen avgör vad du kan göra med [!DNL CAPS].

### Vem kan använda [!DNL CAPS]

* **Projektadministratör** - Kan tillämpa eller återställa korrigeringar i alla miljöer
* **Medarbetare** - Kan tillämpa eller återställa korrigeringsfiler i sina tilldelade miljöer
* **Visningsprogrammet** - Det går bara att visa projektet och miljöerna, inga åtgärder tillåts

### Hur man begär åtkomst till ett projekt

Om du inte ser några projekt i användargränssnittet för [!DNL CAPS] måste du begära åtkomst från rätt person:

* Kontakta kontoägaren eller projektadministratören för projektet
* De ger dig lämplig roll via molnkonsolen
* När du har beviljats åtkomst kan du logga in på molnkonsolen för att använda [!DNL CAPS]

>[!NOTE]
>
>[!DNL CAPS] följer samma behörighetsmodell som Adobe Commerce Cloud, så din åtkomstnivå i molnkonsolen avgör vad du kan göra med [!DNL CAPS].

## Åtkomst till [!DNL CAPS]

CAPS-verktyget finns på kontrollpanelen för verktyget för webbplatsövergripande analys på [https://supportinsights.adobe.com/commerce/](https://supportinsights.adobe.com/commerce/). Under fliken Patching Automation (Korrigeringsautomatisering) kan du välja projekt och miljö.

1. Gå till verktyget för webbplatsövergripande analys på [https://supportinsights.adobe.com/commerce/](https://supportinsights.adobe.com/commerce/).
1. Klicka på fliken [!UICONTROL Patching Automation] i gränssnittet.
1. Välj det projekt och den miljö där du vill använda korrigeringar.
1. Granska tillgängliga korrigeringsfiler och deras kompatibilitetsstatus.
1. Markera de korrigeringsfiler som ska användas eller återställas.

## Åtkomst till produktionsmiljö

För produktionsmiljöer gäller ytterligare skyddsåtgärder:

* **Underhållsläge** - Måste vara aktiverat
* **Kronjobb** - Måste inaktiveras
* **Bekräftelsedialogrutan** - Måste slutföras innan du fortsätter

>[!IMPORTANT]
>
>Patchering av produktionsmiljön kräver lämpliga förberedelser och säkerhetsåtgärder för att förhindra oavsiktliga avbrott.

## Relaterade ämnen

* [Introduktion till CAPS](intro.md)
* [Arbetsflöde](workflow.md)
* [God praxis](best-practices.md)
* [Felsökning](troubleshooting.md)
