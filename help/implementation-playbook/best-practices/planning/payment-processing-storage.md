---
title: Bästa tillvägagångssätt för betalningshantering och lagring
description: Lär dig hur du på ett säkert sätt hanterar och lagrar betalningsinformation
role: Developer
feature: Best Practices
exl-id: 635f38d3-0199-4d96-ba75-9edd0cb94b5c
source-git-commit: db0fce79b22d409e8d639b959dc5a04693e72659
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# Bästa metoder för betalningshantering och lagring

En av de viktigaste principerna för att upprätthålla [PCI-kompatibilitet](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-pci.html) är att ha en strategi för att hantera och lagra kreditkortsbetalningar korrekt.

Det är **strängt förbjudet** att lagra kortinnehavardata i Adobe Commerce, vilket kan vara ett brott mot dina skyldigheter som handlare enligt PCI-DSS (Payment Card Industry Data Security Standard). Mer information om modellen för delat ansvar och riktlinjer för affärsförpliktelser finns i [Adobe Commerce Shared Responsibility Model Guide](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibilities-guide.pdf) på Adobe Trust Center.

Följ de bästa metoderna nedan för att se till att du hanterar betalningsinformation på din e-handelsplats. Mer information om bästa säkerhetspraxis finns i [Skydda din webbplats och infrastruktur](../launch/security-best-practices.md).

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

* Adobe Commerce i molninfrastruktur
* Adobe Commerce lokalt

## Skydda uppgifter om kortinnehavare

Om det behövs lagring av kortinnehavardata ska kortinnehavardata lagras utanför Adobe Commerce med lagringsskydd. Genom att ha lagringskontroller för betalningsinformation, som kreditkortsinnehavarens uppgifter, kan du förhindra bedrägerier och andra potentiella säkerhetsfrågor. I linje med andra PCI-standarder är det första försvaret att ha skydd på plats. Vissa metoder som rekommenderas för att förbättra skyddet av lagrade data är kryptering, trunkering, tokenisering, envägshash och maskering.

Skyddet för kryptografiska nycklar är avgörande för dataskyddsstrategier. Det är viktigt att ha kunniga och pålitliga förvarare som övervakar nycklarna.

Slutligen måste ett primärt kontonummer (PAN) vara oläsbart under lagring, till exempel maskerat med `XXX`. Detta inkluderar flyttbara lagringsmedier och säkerhetskopieringsmedia som flash-enheter, USB och externa hårddiskar samt granskningsloggar.

## Kryptera överföring av kortinnehavardata

Skydda data under överföring är avgörande för att skydda betalningsinformation, t.ex. kortinnehavardata. När denna information överförs via öppna nätverk kan den bli mer sårbar för säkerhetsfrågor.

### Använd säkra överföringsprotokoll

Överför kortinnehavaruppgifter med hjälp av säkra överföringsprotokoll och överföringsmetoder, inklusive

* Betrodda nycklar och certifikat
* Säkra överföringsprotokoll som TLS, SSH eller VPN
* Asymmetriska algoritmer i kryptering
* Tokenisering, maskering och penetrationstestning med överföring och visning av PAN-enheter
* Begränsa åtkomsten till kortinnehavarens data
* Tillgång till känslig information bör begränsas på behovsanpassad grund och endast ges till den auktoriserade personal som har ett affärsbehov

Den rekommenderade metoden för att hantera kortinnehavardata är att tokenisera data i stället för att lagra dem. Tokenisera kortet med en viss betaltjänstleverantör och lagra token, korttyp och krypterat förfallodatum. Du kan använda denna token som inloggningsuppgifter för framtida bruk eftersom den är unik endast för varje handlare. Eftersom variabeln är unik, om det finns ett säkerhetsproblem, är variabeln ogiltig vilket hjälper till att förhindra bedräglig aktivitet.

## Ytterligare information

Om du letar efter rekommenderade betalningslösningar från Adobe bör du överväga [Adobe Payment Services](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html).
