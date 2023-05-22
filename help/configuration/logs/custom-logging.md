---
title: Anpassad loggning
description: Lär dig hur du undersöker fel med anpassad loggning.
feature: Configuration, Logs
exl-id: 6c94ebcf-70df-4818-a17b-32512eba516d
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '409'
ht-degree: 0%

---

# Översikt över anpassad loggning

Loggar ger synlighet i systemprocesserna. t.ex. felsökningsinformation som hjälper dig förstå när ett fel inträffade eller vad som ledde till felet.

Det här avsnittet fokuserar på filbaserad loggning, men Commerce ger även flexibilitet att lagra loggar i databasen.

Adobe rekommenderar att centraliserad programloggning används av följande skäl:

- Den gör att loggar kan lagras på en annan server än programservern och minskar I/O-diskåtgärder, vilket förenklar stödet för programservern.

- Det gör databehandlingen effektivare med specialverktyg som [Logstash], [Logplex], eller [flytande]- utan påverkan på en produktionsserver.

   >[!INFO]
   >
   >Adobe rekommenderar eller stöder inte någon särskild loggningslösning.

## PSR-3-kompatibilitet

The [PSR-3-standard][laminas] definierar ett vanligt PHP-gränssnitt för loggning av bibliotek. Det främsta målet för PSR-3 är att tillåta bibliotek att ta emot en `Psr\Log\LoggerInterface` objekt och skriva loggar på ett enkelt och universellt sätt.

Detta gör att implementeringen enkelt kan ersättas utan att du behöver oroa dig för att en sådan ersättning kan bryta programkoden. Det garanterar också att en anpassad komponent fungerar även när loggimplementeringen ändras i en framtida version av systemet.

## Monolog

Commerce 2 följer PSR-3-standarden. Som standard används [Monolog]. Monolog implementeras som en inställning för `Psr\Log\LoggerInterface` i Commerce-programmet [`di.xml`][di].

Monolog är en populär PHP-loggningslösning med ett stort antal hanterare som gör att du kan skapa avancerade loggningsstrategier. Här följer en sammanfattning av hur Monolog fungerar.

A Monolog _loggare_ är en kanal som har en egen uppsättning _hanterare_. Monolog har många hanterare, bland annat:

- Logga in på filer och syslog
- Skicka aviseringar och e-post
- Logga specifika servrar och nätverksloggning
- Inloggningsutveckling (integrering med FireBug och Chrome Logger, bland annat)
- Logga in i databasen

Varje hanterare kan antingen bearbeta indatameddelandet och stoppa spridningen eller skicka kontrollen till nästa hanterare i en kedja.

Loggmeddelanden kan behandlas på många olika sätt. Du kan till exempel lagra all felsökningsinformation i en fil på disken, placera meddelanden med högre loggnivåer i en databas och slutligen skicka meddelanden med loggnivån &quot;critical&quot; via e-post.

Andra kanaler kan ha en annan uppsättning hanterare och logik.

<!-- link definitions -->

[di]: https://github.com/magento/magento2/blob/2.4/app/etc/di.xml#L9
[flytande]: https://www.fluentd.org/
[laminas]: https://docs.laminas.dev/laminas-log/
[Logplex]: https://devcenter.heroku.com/articles/logplex
[Logstash]: https://www.elastic.co/products/logstash
[Monolog]: https://github.com/Seldaek/monolog
