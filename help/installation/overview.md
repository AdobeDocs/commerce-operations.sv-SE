---
title: Lokal installationsöversikt
description: Förstå installationsprocessen för lokal driftsättning av Adobe Commerce.
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '148'
ht-degree: 7%

---

# Lokal installationsöversikt

>[!NOTE]
>
>I följande diagram visas en översikt på hög nivå över _**lokala**_-installationer av Adobe Commerce:

![Så här fungerar installationen](../assets/installation/install-diagram-24.svg)

Det allmänna installationsflödet är följande:

1. Konfigurera servermiljön.

   Installera nödvändig programvara, inklusive PHP, Apache, MySQL och sökmotorn. Mer information finns i [systemkraven](system-requirements.md).

1. Hämta [autentiseringsnycklar](prerequisites/authentication-keys.md) till Commerce Composer-databasen.

1. Skaffa Adobe Commerce.

   * (Rekommenderas) Hämta [Composer-metapaketet](composer.md) för att hantera moduler och deras beroenden.

   * Om du vill bidra till kodbasen för Magento Open Source eller anpassa programmet [klonar](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) GitHub-databasen. Den här metoden kräver att du känner till både GitHub och Composer.

1. Installera programmet med kommandoraden.

   Om steget misslyckas på grund av att nödvändig programvara inte är korrekt konfigurerad kan du granska [förutsättningarna](prerequisites/overview.md).

1. [Verifiera](next-steps/verify.md) installationen genom att visa butiken och administratören.
