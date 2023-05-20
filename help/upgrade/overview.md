---
title: Översikt över uppgraderingsprocessen
description: Läs om hur du genom att uppgradera ditt Adobe Commerce-projekt kan skydda din butik och fungera effektivt.
exl-id: 40bd97ca-6648-40d4-9c61-7d159391976a
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '898'
ht-degree: 0%

---

# Översikt över uppgraderingsprocessen

Det är viktigt att uppgradera Adobe Commerce-projektet för att säkerställa att din butik är säker, PCI-kompatibel och fungerar optimalt. Den här guiden vägleder dig igenom viktiga saker när du förbereder dig för en uppgradering.

Guiden ger en översikt över den typiska uppgraderingsresan för Adobe Commerce och de bästa sätten att följa på den resan. Den beskriver också den tekniska informationen i uppgraderingsprocessen med ett aktuellt exempel och stegvisa instruktioner för uppgradering till den senaste versionen av Adobe Commerce. Det är viktigt att du tittar på Adobe Commerce [publiceringsschema](../release/schedule.md) och börja förbereda för uppgraderingar tidigt. Adobe publicerar lanseringsschemat årligen för att underlätta handlarnas planeringsprocess och rekommenderar att man uppgraderar varje patch-releasecykel. För att vara PCI-kompatibel måste handlarna finnas på den senaste patchen eller säkerhetsuppdateringen.

## Vem är den här guiden till?

Målgruppen för guiden är:

- **E-handelsförvaltare och tekniska direktörer**- Förstå uppgraderingsresan, vikten av att uppgradera regelbundet och hur man bäst planerar och förbereder sig för en uppgradering.
- **Operations- och utvecklingsteam**- Lär dig de tekniska steg som krävs för att uppgradera till den senaste versionen av Adobe Commerce och de verktyg som gör processen enklare, snabbare och mer prisvärd.

## Uppgraderingsprocessen förklaras

En av orsakerna till att du valt Adobe Commerce är:

- En mängd färdiga funktioner
- SaaS-funktioner som erbjuds separat från kärnkoden
- Robusta erbjudanden om Marketplace-tillägg
- Unik möjlighet att tillåta oändlig flexibilitet så att du kan anpassa din webbplats så att den bäst passar ditt företags och dina kunders behov

Fördelen med att vara en mycket utbyggbar och anpassningsbar produkt kan dock ge upphov till potentiella uppgraderingsproblem när anpassningar inte är kodade enligt bästa praxis, vilket leder till högre uppgraderingskostnader än förväntat.

_Så.. varför uppgradera över huvud taget?_

Uppgraderingen ger er möjlighet att hålla er à jour med den snabba och ständigt föränderliga e-handelsindustrin och gör att plattformen kan vara kompatibel med de senaste Adobe Commerce-funktionerna som hjälper er att maximera försäljningen och konverteringarna. Att inkludera uppgraderingar i dina vanliga underhållsplaner är avgörande för att säkerställa att din butik förblir säker, PCI-kompatibel och fungerar med maximal effektivitet.

### Säkerhet

Säkerhet är en av de främsta anledningarna till att uppgradera eftersom 83 % av säkerhetsincidenterna inträffar för inaktuell programvara. Enligt [IBM](https://www.ibm.com/reports/data-breach)är den genomsnittliga kostnaden för en dataöverträdelse 3,86 miljoner dollar - mycket större än vad den kostar att minska denna risk genom uppgradering. Adobe erbjuder två sätt att skydda din butik under året:

- **Patch releases**- Inkludera säkerhets-, prestanda-, kvalitets- och högprioriterade felkorrigeringar.
- **Säkerhetsuppdateringar**- Lägg in korrigeringar och förbättringar som gör webbplatsen säker och enklare att implementera.

### Prestanda

Prestanda är en annan viktig orsak till uppgradering. Enligt [HubSpot](https://blog.hubspot.com/marketing/page-load-time-conversion-rates), har de första fem sekundernas laddningstid en betydande effekt på konverteringsgraden och därefter får varje sekund av fördröjning en -4,4 % effekt. Detta, tillsammans med det faktum att sidhastighet är en ledande SEO-rankningsfaktor, visar varför webbplatsprestanda är en viktig del av din webbplats att underhålla och regelbundet förbättra. Varje patch-release innehåller prestandaförbättringar, så att du kan utnyttja de nya releaserna och behålla företagets konkurrenskraft.

### Fördröjningskostnad

Att fördröja eller fördröja uppgraderingen av plattformen beror ofta på den omedelbara kostnaden. Den verkliga kostnaden för att köra en föråldrad version av en programvara är dock mycket större och kan ha en bestående inverkan på verksamheten.

Det kan verka kontraintuitivt, men att utföra regelbundna plattformsuppdateringar kräver mindre insatser totalt sett än att göra ovanliga uppdateringar på grund av den samlade tekniska skuld som uppstår till följd av försening. Adobe arbetade nyligen med en partner som har en detaljhandlare som brukade göra uppgraderingar sällan och inkonsekvent (årligen eller längre). Genom att förändra hur de närmar sig uppgraderingar och efter att ha följt ett regelbundet uppgraderingssätt som rekommenderas av Adobe under en tolvmånadersperiod, kunde partnern spara sina kunder fyra veckors kumulativ utvecklingstid, arbetsinsats och därmed sammanhängande kostnader. Dessa kostnader kan sedan omdirigeras till initiativ som främjar tillväxt.

När uppdateringarna utförs regelbundet blir ändringarna stegvisa och motsvarande uppgraderingsarbete speglar detta. När plattformsuppdateringar fördröjs under en längre period kan de bli mer involverade. Dessutom kan du använda tillägg från [Adobe Commerce Marketplace](https://marketplace.magento.com/) och andra integreringar med tredje part kan också påverkas. Slutligen förlängs den tid det tar att undersöka, planera och genomföra en försenad uppgradering, vilket ger oundvikliga kostnader.

Några av de allmänna faktorer som påverkar graden av arbete med att uppgradera ditt projekt är bland annat:

| Teknisk komplexitet | Planering och strategi |
|-----------------------------------------------------------|--------------------------------------------------------------|
| Omfattningen av anpassningar | Klarhet i krav, beslut om våglängd och krypande omfång |
| Antal tillägg | Din uppgraderingsfrekvens |
| Antal integreringar med tredje part (OMS, ERP) | Din teststrategi |
| Kodning enligt bästa praxis |  |

Den fortsatta tillväxten inom den digitala e-handeln har ökat trycket på företagen att utvecklas snabbare, oftare och på ett oförutsägbart sätt. Underlåtenhet att hålla jämna steg med och förutse kundernas köpbeteende har lett till lika konkurrensvillkor för även de största, mest etablerade varumärkena. Ni måste kunna leverera robusta, personaliserade upplevelser över alla kontaktytor, utan avbrott i prestanda och drifttid. Ni måste kunna förnya er snabbare, utan begränsningar, för att ligga steget före globala konkurrenter. Genom att uppgradera kan ni framtidssäkra er om er verksamhet och anpassa er till nya dynamiska kundbehov.
