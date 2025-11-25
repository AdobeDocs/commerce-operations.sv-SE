---
title: Lokal installationsöversikt
description: Läs om installationsprocessen för Adobe Commerce lokalt. Upptäck serverkrav, konfigurationssteg och bästa praxis för driftsättning.
exl-id: a9f5b241-d05d-462c-8c7f-479a264c988f
source-git-commit: 84a20012a81278cc95587ec14281b05330261687
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---


# Lokal installationsöversikt

På den här sidan finns en översikt över hur du installerar Adobe Commerce på din egen infrastruktur. Installationsprocessen innebär att du konfigurerar servermiljön, skaffar den programvara och de autentiseringsuppgifter som krävs samt kör installationskommandot.

Du kan installera Adobe Commerce lokalt på cirka 30 till 60 minuter. Den tid som krävs för att konfigurera servermiljön innan installationen varierar dock beroende på din erfarenhet och vilken teknik du väljer.

>[!TIP]
>
>Du bör ha mellanliggande tekniska kunskaper och serveråtkomst för att kunna fortsätta.

Installationen skapar en fullt fungerande Adobe Commerce-butik med både en [kundriktad butik](https://experienceleague.adobe.com/sv/docs/commerce-admin/start/storefront/storefront) och en [administrativ panel](https://experienceleague.adobe.com/sv/docs/commerce-admin/start/admin/admin). Du måste ha dina databasinloggningsuppgifter, domäninformation och autentiseringsnycklar klara innan du kan påbörja processen.

## Handläggaransvar

Med Adobe Commerce lokalt kan du vara värd för och hantera din egen infrastruktur, inklusive servrar, värdmiljöer och systemunderhåll. Adobe ger särskilt stöd för Commerce centrala program:

- Tillgång till produktuppdateringar och korrigeringar
- Säkerhetsuppdateringar för att åtgärda säkerhetsluckor
- Omfattande dokumentation som hjälper dig att hantera och optimera din egen lösning

Ni har full kontroll över er miljö, vilket ger större anpassning och flexibilitet, men ni ansvarar för att säkerställa infrastrukturens prestanda, säkerhet och skalbarhet. Du ansvarar till exempel för följande:

- Utformning, implementering, konfiguration, underhåll, felsökning och prestandatestning för alla Adobe Commerce på lokala system.
   - Servrar, operativsystem, databaser, [!DNL PHP], sökning, cachelagring, helsidescache och leveransnätverk för innehåll. Vanliga teman kan omfatta (men inte begränsat till) [!DNL Nginx/Apache], [!DNL PHP], [!DNL MySQL/MariaDB], [!DNL Redis], [!DNL Elasticsearch/OpenSearch], [!DNL RabbitMQ], [!DNL Varnish], [!DNL DNS], [!DNL SSL/TLS certificates] och alla [!DNL CDN] som används.
- Kapacitetsplanering, automatisk skalning, klustring, säkerhetskopiering, katastrofåterställning
- Alla produkt- och kunddata, design, konfiguration och installation, program- och databasunderhåll, koddistribution, versionsuppgraderingar och korrigeringsprogram
- Övervakning och varningar via APM/loggning/varningar (till exempel [!DNL New Relic], [!DNL Datadog], [!DNL ELK])
- Säkerhetsuppdatering för operativsystem, [!DNL PHP], databas, maskinvaruhärdning och uppdateringar

## Arbetsflöde

I följande diagram visas de viktigaste stegen som krävs för att installera Adobe Commerce i lokala miljöer:

![Så här fungerar installationen](../assets/installation/on-premises-install.drawio.svg)

### Konfigurera servermiljön

Installera och konfigurera PHP, webbserver, databas och sökmotor enligt [förutsättningarna](prerequisites/overview.md).

### Hämta autentiseringsnycklar

Generera nya [autentiseringsnycklar](prerequisites/authentication-keys.md) (eller kopiera befintliga nycklar) från Commerce Marketplace för att få åtkomst till Adobe Commerce Composer-paket.

### Skaffa Adobe Commerce

Hämta med [Composer](prerequisites/commerce.md) (rekommenderas) eller klona från GitHub för utvecklingsbidrag.

Om du vill bidra till Magento Open Source-kodbasen eller anpassa programmet [klonar](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository) GitHub-databasen. Den här metoden kräver att du känner till både GitHub och Composer.

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
