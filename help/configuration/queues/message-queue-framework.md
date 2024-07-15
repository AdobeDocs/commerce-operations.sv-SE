---
title: Översikt över meddelandeköer
description: Läs om meddelandeköramverket och hur det fungerar med Adobe Commerce.
exl-id: 21e7bc3e-6265-4399-9d47-d3b9f03dfef6
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---

# Översikt över meddelandeköer

MQF (Message Queue Framework) är ett system som gör att en modul kan publicera meddelanden till köer. Den definierar också de [konsumenter](consumers.md) som tar emot meddelandena asynkront. MQF använder [[!DNL RabbitMQ]](https://www.rabbitmq.com) som meddelandeförmedlare, som tillhandahåller en skalbar plattform för att skicka och ta emot meddelanden. Den innehåller även en mekanism för att lagra olevererade meddelanden. [!DNL RabbitMQ] baseras på specifikationen Advanced Message Queuing Protocol (AMQP) 0.9.1.

Följande diagram visar Message Queue Framework:

![Ramverk för meddelandekö](../../assets/configuration/mq-framework.png)

- En utgivare är en komponent som skickar meddelanden till ett utbyte. Det vet vilket utbyte som ska publiceras och formatet på de meddelanden som skickas.

- Ett utbyte tar emot meddelanden från utgivare och skickar dem till köer. Även om [!DNL RabbitMQ] har stöd för flera typer av utbyten använder Commerce endast ämnesutbyten. Ett ämne innehåller en routningsnyckel, som innehåller textsträngar avgränsade med punkter. Formatet för ett ämnesnamn är `string1.string2`: till exempel `customer.created` eller `customer.sent.email`.

  Med förmedlaren kan du använda jokertecken när du anger regler för vidarebefordrande meddelanden. Du kan använda en asterisk (`*`) om du vill ersätta __-strängen eller ett nummertecken (`#`) om du vill ersätta 0 eller fler strängar. `customer.*` skulle till exempel filtreras på `customer.create` och `customer.delete`, men inte `customer.sent.email`. `customer.#` skulle dock filtreras på `customer.create`, `customer.delete` och `customer.sent.email`.

- En kö är en buffert som lagrar meddelanden.

- En konsument får meddelanden. Den vet vilken kö som ska användas. Den kan mappa behandlare av meddelandet till en viss kö.

Ett grundläggande meddelandekösystem kan också konfigureras utan att använda [!DNL RabbitMQ]. I det här systemet lagrar ett MySQL-kort meddelanden i databasen. Tre databastabeller (`queue`, `queue_message` och `queue_message_status`) hanterar arbetsbelastningen för meddelandekön. Kronjobb säkerställer att konsumenterna kan ta emot meddelanden. Den här lösningen är inte särskilt skalbar. [!DNL RabbitMQ] ska användas när det är möjligt.
