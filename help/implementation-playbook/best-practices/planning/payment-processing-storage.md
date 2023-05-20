---
title: Bästa tillvägagångssätt för betalningshantering och lagring
description: Lär dig hur du på ett säkert sätt hanterar och lagrar betalningsinformation
role: Developer
feature-set: Commerce
feature: Best Practices
exl-id: 635f38d3-0199-4d96-ba75-9edd0cb94b5c
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# Bästa metoder för betalningshantering och lagring

En av de viktigaste principerna för att upprätthålla [PCI-kompatibilitet](https://experienceleague.adobe.com/docs/commerce-admin/start/compliance/payments/compliance-pci.html) har en strategi för att hantera och lagra kreditkortsbetalningar på rätt sätt.

Att lagra kortinnehavardata i Adobe Commerce är **strikt förbjudet** och det kan vara ett brott mot dina skyldigheter som handlare enligt PCI-DSS (Payment Card Industry Data Security Standard). Mer information om vår modell för delat ansvar och riktlinjer för handlares skyldigheter finns i vår [guide för delat ansvar för Adobe Commerce](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-shared-responsibility-guide.pdf) på Adobe Trust Center.

Vi rekommenderar att du följer de bästa metoderna nedan för att säkerställa att du hanterar betalningsinformation på din e-handelsplats. Mer information om de effektivaste strategierna för säkerhet finns i våra [guide om bästa praxis för säkerhet för Adobe Commerce](https://www.adobe.com/content/dam/cc/en/trust-center/ungated/whitepapers/experience-cloud/adobe-commerce-best-practices-guide.pdf) på Adobe Trust Center

## Berörda produkter och versioner

[Alla versioner som stöds](../../../release/versions.md) av:

* Adobe Commerce i molninfrastruktur
* Adobe Commerce lokalt

## Skydda uppgifter om kortinnehavare

Om det behövs lagring av kortinnehavardata ska kortinnehavardata lagras utanför Adobe Commerce med lagringsskydd. Genom att ha lagringskontroller för betalningsinformation, som kreditkortsinnehavarens uppgifter, kan du förhindra bedrägerier och andra potentiella säkerhetsfrågor. I linje med andra PCI-standarder är det första försvaret att ha skydd på plats. Vissa metoder som rekommenderas för att förbättra skyddet av lagrade data är kryptering, trunkering, tokenisering, envägshash och maskering.

Skyddet för kryptografiska nycklar är avgörande för dataskyddsstrategier. Det är viktigt att ha kunniga och pålitliga förvarare som övervakar nycklarna.

Slutligen måste ett primärt kontonummer (PAN) vara oläsbart under lagring (t.ex. maskerat såsom XXX). Detta inkluderar flyttbara lagringsmedier och säkerhetskopieringsmedia som flash-enheter, USB och externa hårddiskar samt granskningsloggar.

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

Den rekommenderade metoden för att hantera kortinnehavardata är att inte lagra det primära kontonumret (PAN) utan att tokenisera kortet med en viss betalbehandlare och lagra token, korttyp och krypterat förfallodatum. Du kan använda denna token som inloggningsuppgifter för framtida bruk eftersom den är unik endast för varje handlare. Eftersom variabeln är unik och det uppstår ett säkerhetsproblem, blir variabeln ogiltig vilket förhindrar bedräglig aktivitet

## Ytterligare information

Om du letar efter rekommenderade betalningslösningar från Adobe bör du överväga [Betalningstjänster för Adobe](https://experienceleague.adobe.com/docs/commerce-merchant-services/payment-services/overview.html).
