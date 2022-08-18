---
title: Översikt över meddelandeköer
description: Läs om meddelandeköramverket och hur det fungerar med Adobe Commerce och Magento Open Source.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---


# Översikt över meddelandeköer

MQF (Message Queue Framework) är ett system som tillåter en [modul](https://glossary.magento.com/module) för att publicera meddelanden till köer. Det definierar också de konsumenter som ska ta emot meddelandena asynkront. MQF använder [KaninMQ](https://www.rabbitmq.com) som meddelandeförmedlare, som tillhandahåller en skalbar plattform för att skicka och ta emot meddelanden. Den innehåller även en mekanism för att lagra olevererade meddelanden. RabbitMQ baseras på specifikationen Advanced Message Queuing Protocol (AMQP) 0.9.1.

Följande diagram visar Message Queue Framework:

![Message Queue Framework](../../assets/configuration/mq-framework.png)

- A [utgivare](https://glossary.magento.com/publisher-subscriber-pattern) är en komponent som skickar meddelanden till ett utbyte. Det vet vilket utbyte som ska publiceras och formatet på de meddelanden som skickas.

- Ett utbyte tar emot meddelanden från utgivare och skickar dem till köer. Även om RabbitMQ har stöd för flera typer av utbyten används endast ämnesutbyten. Ett ämne innehåller en routningsnyckel, som innehåller textsträngar avgränsade med punkter. Formatet för ett ämnesnamn är `string1.string2`: till exempel `customer.created` eller `customer.sent.email`.

   Med förmedlaren kan du använda jokertecken när du anger regler för vidarebefordrande meddelanden. Du kan använda en asterisk (`*`) att ersätta _en_ en sträng eller ett nummertecken (`#`) om du vill ersätta 0 eller fler strängar. Till exempel: `customer.*` skulle filtrera på `customer.create` och `customer.delete`, men inte `customer.sent.email`. Men `customer.#` skulle filtrera på `customer.create`,  `customer.delete`och `customer.sent.email`.

- En kö är en buffert som lagrar meddelanden.

- En konsument får meddelanden. Den vet vilken kö som ska användas. Den kan mappa behandlare av meddelandet till en viss kö.

Ett grundläggande meddelandekösystem kan också konfigureras utan att RabbitMQ används. I det här systemet finns en MySQL [adapter](https://glossary.magento.com/adapter) lagrar meddelanden i databasen. Tre databastabeller (`queue`, `queue_message`och `queue_message_status`) kan hantera arbetsbelastningen för meddelandekön. Kronjobb säkerställer att konsumenterna kan ta emot meddelanden. Denna lösning är inte särskilt skalbar. RabbitMQ ska användas när det är möjligt.