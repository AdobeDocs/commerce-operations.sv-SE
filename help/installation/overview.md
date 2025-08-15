---
title: Lokal installationsöversikt
description: Förstå installationsprocessen för lokal driftsättning av Adobe Commerce.
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: 7cc77a204d2a3c0773e6a0ab60e57e6e35f12091
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 3%

---


# Lokal installationsöversikt

På den här sidan finns en översikt över hur du installerar Adobe Commerce på din egen infrastruktur. Installationsprocessen innebär att du konfigurerar servermiljön, skaffar den programvara och de autentiseringsuppgifter som krävs samt kör installationskommandot.

Du kan installera Adobe Commerce på cirka 30 till 60 minuter. Den tid som krävs för att konfigurera servermiljön innan installationen varierar dock beroende på din erfarenhet och vilken teknik du väljer.

>[!TIP]
>
>Du bör ha mellanliggande tekniska kunskaper och serveråtkomst för att kunna fortsätta.

Installationen skapar en fullt fungerande Adobe Commerce-butik med både en [kundriktad butik](https://experienceleague.adobe.com/en/docs/commerce-admin/start/storefront/storefront) och en [administrativ panel](https://experienceleague.adobe.com/en/docs/commerce-admin/start/admin/admin). Du måste ha dina databasinloggningsuppgifter, domäninformation och autentiseringsnycklar klara innan du kan påbörja processen.

## Arbetsflöde

I följande diagram visas de viktigaste stegen som krävs för att installera Adobe Commerce i lokala miljöer:

![Så här fungerar installationen](../assets/installation/on-premises-install.drawio.svg)

### Konfigurera servermiljön

Installera och konfigurera PHP, webbserver, databas och sökmotor enligt [förutsättningarna](prerequisites/overview.md).

### Hämta autentiseringsnycklar

Generera nya [autentiseringsnycklar](prerequisites/authentication-keys.md) (eller kopiera befintliga nycklar) från Commerce Marketplace för att få åtkomst till Adobe Commerce Composer-paket.

### Skaffa Adobe Commerce

Hämta med [Composer](prerequisites/commerce.md) (rekommenderas) eller klona från GitHub för utvecklingsbidrag.

Om du vill bidra till Magento Open Source-kodbasen eller anpassa programmet [klonar](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) GitHub-databasen. Den här metoden kräver att du känner till både GitHub och Composer.

### Installera programmet

Kör installationskommandot med din specifika konfiguration. Fullständiga exempel finns i [snabbstarten](composer.md).

>[!NOTE]
>
>Om stegen misslyckas på grund av att nödvändig programvara inte är korrekt konfigurerad kan du granska [förutsättningarna](prerequisites/overview.md).

### Verifiera installationen

[Testa](next-steps/verify.md) din storefront och admin-panel för att se till att allt fungerar som det ska.

## Vanliga installationsproblem

- **Behörighetsfel**: Kontrollera att filsystemet har rätt ägarskap och behörigheter
- **Databasanslutningsfel**: Verifiera databasautentiseringsuppgifter och nätverksanslutning
- **Fel i autentiseringsnyckel**: Bekräfta att dina Commerce Marketplace-nycklar är giltiga och aktiva
- **Minnesbegränsningar**: Kontrollera att PHP-minnesallokeringen är tillräcklig (minst 2 GB rekommenderas)
