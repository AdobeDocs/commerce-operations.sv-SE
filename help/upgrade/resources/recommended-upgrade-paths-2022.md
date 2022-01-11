---
title: Rekommenderade uppgraderingssökvägar för 2022
description: Läs rekommendationerna om hur du planerar uppgraderingen av Adobe Commerce eller Magento Open Source 2022.
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '936'
ht-degree: 0%

---


# Rekommenderade uppgraderingsalternativ för 2022

En e-handelsimplementering är en utveckling - den är aldrig riktigt färdig. Företaget måste ligga steget före trenderna genom att introducera de senaste funktionerna som håller kunderna engagerade. Med tiden ökar dessa extrafunktioner implementeringens utrymme och komplexitet.

Några av de allmänna faktorer som påverkar arbetsinsatsen för ditt uppgraderingsprojekt är bland annat följande, men är inte begränsade till:

| Teknisk komplexitet | Planering och strategi |
|-----------------------------------------------------------|--------------------------------------------------------------|
| Omfattningen av anpassningar | Klarhet i krav, beslut om våglängd och krypande omfång |
| Antal tillägg | Din uppgraderingsfrekvens |
| Antal integreringar med tredje part (OMS, ERP) | Din teststrategi |
| Kodning enligt bästa praxis |  |

Här följer några av de sökvägar som rekommenderas av Adobe Commerce för att skydda webbplatsen och dess prestanda under hela 2022.

## Uppgradera från version 2.3.0-2.3.6 (alternativ 1)

![](../../assets/upgrade-guide/2.3.0-2.3.6-option1.png)

Du kan gå från vilken 2.3.x-linje som helst till 2.4.3. Ju längre du går utan en uppgradering, desto mer ansträngning går det att gå direkt till 2.4.3 när kodbasen har ändrats mer.

Om du till exempel är på 2.3.4 som släpptes i januari 2020 har du en release som är nästan två år gammal så kodbasen 2.4.3 är mycket större jämfört med 2.3.4. Därför rekommenderar Adobe att du uppgraderar ofta, eftersom arbetsbördan tenderar att bli ännu högre om du förlänger uppgraderingen under en längre period.

När du är klar med 2.4.3 kan du under första kvartalet fortsätta vara säker genom att ta 2.4.3-p2, vilket är en låg insats eftersom det är en lätt säkerhetsrelease. Under tredje kvartalet kan du ta den fullständiga patchen 2.4.5 och ytterligare en lätt säkerhetskorrigering för att vara säker under det fjärde kvartalet. Detta kräver två högeffektiva uppgraderingar före slutet av 2022.

## Uppgradera från version 2.3.0-2.3.6 (alternativ 2)

![](../../assets/upgrade-guide/2.3.0-2.3.6-option2.png)

Du kan också uppgradera från 2.3.x direkt till 2.4.4 i mars 2022. Från och med 2.4.4 kan du sedan ta den lätta säkerhetspatchen i Q3 och sedan uppgradera till version 2.4.5-p1 i Q4, som innehåller alla uppdateringar som fanns i version 2.4.5 och ytterligare säkerhetspatchar.

Tänk på följande när du ska välja mellan dessa två alternativ:

| Alternativ 1: Uppgradera till 2.4.3-p1 eller -p2 | Alternativ 2: Uppgradera till 2.4.4 eller 2.4.4-p1 |
|--------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| 2 viktiga uppgraderingar krävs före slutet av 2022 för att förbli säkra, PCI-kompatibla och få kvalitetssupport | Kräver en betydande uppgradering och en uppgradering med låg medelhög insats före slutet av 2022 för att förbli säker, PCI-kompatibel och få kvalitetssupport |
| Ger dig möjlighet att snabbare komma till en version som stöds av PCI | Du kan ha ett längre fönster tills du kommer till en version som stöder PCI eftersom 2.3-serien når EOL i april 2022 |
| Tidsbedömning: kan vänta med att gå över till en ny PHP-version till senare under året (augusti) | Tidsbedömning: kan börja gå över till en ny PHP-version tidigare under året (mars) |

## Uppgradera från 2.3.7 (alternativ 1)

![](../../assets/upgrade-guide/2.3.7-option1.png)

När du använder den senaste 2.3.7-versionen är du på en linje som bara får säkerhetsreleaser. I Q1 av &quot;22&quot; släpper Adobe den senaste versionen av 2.3, som är 2.3.7-p3, tillsammans med en säkerhetsrelease (2.4.3-p2) och en fullständig version (2.4.4).

Det första alternativet är att ta 2.3.7-p3 och få de senaste säkerhetskorrigeringarna. I augusti kan du ta version 2.4.5. Slutligen kan du under det fjärde kvartalet ta den lätta säkerhetsreleasen som bygger på den fullständiga versionen 2.4.5. I så fall använder du en EOL-version i några månader tills du tar 2.4.5. 2.3.x har dock för närvarande inget stöd för kvalitet och du skulle ha åtgärdat de senaste säkerhetsluckorna.

## Uppgradera från 2.3.7 (alternativ 2)

![](../../assets/upgrade-guide/2.3.7-option2.png)

Det andra alternativet skulle vara att ta version 2.3.7-p3 för att snabbt få de senaste säkerhetskorrigeringarna, eftersom säkerhetspatcharna för den aktuella raden är låga och sedan kan du börja uppgradera till version 2.4.4.

I augusti kunde du sedan ta 2.4.4-p1, vilket skulle vara en lätt säkerhetsrelease, och under Q4 ta 2.4.5-p1, som inkluderar alla uppdateringar som ingår i 2.4.5 och de senaste säkerhetsreleaserna.

Du kan också gå från 2.3.7-p3 till 2.4.4-p1, men observera att 2.4.4-p1 är en&quot;grov lyft&quot; eftersom du i princip får alla uppdateringar som ingår i 2.4.4 och säkerhetsuppdateringarna i 2.4.4-p1. Det är upp till dig och ditt team att bestämma om ni vill starta den här tyngre lyften till 2.4.4-linjen i mars eller augusti.

Tänk på följande när du ska välja mellan dessa två alternativ:

| Alternativ 1: Uppgradera till 2.3.7-p3 och sedan 2.4.5 | Alternativ 2: Uppgradera till 2.3.7-p3 och sedan 2.4.4 |
|--------------------------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------|
| Ta emot de senaste säkerhetsuppdateringarna med säkerhetspatchen med låg insats först | Ta emot de senaste säkerhetsuppdateringarna med säkerhetspatchen med låg insats först |
| 1 stor uppgradering krävs före slutet av 2022 för att förbli säker, PCI-kompatibel och få kvalitetssupport | Kräver en betydande uppgradering och en uppgradering med låg medelhög insats före slutet av 2022 för att förbli säker, PCI-kompatibel och få kvalitetssupport |
| Anta ett längre fönster tills du kommer till en version som stöder PCI eftersom 2.3-serien når EOL i april | Tidsbedömning: kan börja gå över till en ny PHP-version tidigare under året (mars) |
| Tidsinställningar: kan fördröja uppgraderingen till augusti | Tidsinställningar: kan påbörja en uppgradering i mars och sedan få en medelhög uppgradering i oktober |

## Uppgradera från 2.4.0 till 2.4.2

![](../../assets/upgrade-guide/2.4.0-2.4.2.png)

Eftersom du befinner dig på 2.4.0-2.4.2 rekommenderar vi att du uppgraderar till 2.4.4 i Q1. Detta är en ganska stor insats på grund av de stora förändringar i 2.4.4 som orsakas av övergången till PHP 8.1. Resten av uppgraderingarna är dock lägre, så du behöver bara göra en uppgradering på högre nivå 2022.

## Uppgradera från 2.4.3

![](../../assets/upgrade-guide/2.4.3.png)

Eftersom du befinner dig på 2.4.3 är det minst ansträngning att ta 2.4.3-p2 i Q1. Sedan i augusti kan du ta version 2.4.5. Slutligen kan du under det fjärde kvartalet ta den lätta säkerhetsreleasen som bygger på den fullständiga versionen 2.4.5. I det här scenariot utför du bara en uppgradering på högre nivå 2022.
