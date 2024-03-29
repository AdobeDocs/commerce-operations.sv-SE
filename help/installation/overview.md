---
title: Lokal installationsöversikt
description: Läs om installationsprocessen för lokal driftsättning av Adobe Commerce och Magento Open Source.
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '166'
ht-degree: 0%

---

# Lokal installationsöversikt

>[!NOTE]
>
>I följande diagram finns en översikt på hög nivå över _**lokal**_ installationer av Adobe Commerce och Magento Open Source:

![Så här fungerar installationen](../assets/installation/install-diagram-24.svg)

Det allmänna installationsflödet är följande:

1. Konfigurera servermiljön.

   Installera nödvändig programvara, inklusive PHP, Apache, MySQL och sökmotorn. Se [systemkrav](system-requirements.md) för mer information.

1. Hämta [autentiseringsnycklar](prerequisites/authentication-keys.md) till databasen för Commerce Composer.

1. Skaffa Adobe Commerce eller Magento Open Source.

   * (Rekommenderas) Få [Metapaket för disposition](composer.md) för att hantera moduler och deras beroenden.

   * Om du vill bidra till Magento Open Source-kodbasen eller anpassa programmet [klona](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) GitHub-databasen. Den här metoden kräver att du känner till både GitHub och Composer.

1. Installera programmet med kommandoraden.

   Om steget misslyckas på grund av att nödvändig programvara inte är korrekt konfigurerad kan du granska [krav](prerequisites/overview.md).

1. [Verifiera](next-steps/verify.md) genom att visa din butik och administratören.
