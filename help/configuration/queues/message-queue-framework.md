---
title: Översikt över meddelandeköer
description: Läs om meddelandeköramverket och hur det fungerar med Adobe Commerce.
exl-id: 21e7bc3e-6265-4399-9d47-d3b9f03dfef6
source-git-commit: 7610a5843b526a765dd35188722b7be8e6051049
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Översikt över meddelandeköer

MQF (Message Queue Framework) är ett system som gör att en modul kan publicera meddelanden till köer. Den definierar också de [konsumenter](consumers.md) som tar emot meddelandena asynkront. MQF har stöd för flera meddelandeförmedlare:

- **[[!DNL RabbitMQ]](https://www.rabbitmq.com)** - Den primära meddelandeförmedlaren, som tillhandahåller en skalbar plattform för att skicka och ta emot meddelanden. Den innehåller en mekanism för att lagra olevererade meddelanden och är baserad på specifikationen Advanced Message Queuing Protocol (AMQP) 0.9.1.
- **[Apache ActiveMQ Artemis](https://activemq.apache.org/components/artemis/)** - En alternativ meddelandeförmedlare som använder STOMP (Simple Text Oriented Messaging Protocol) för tillförlitlig och skalbar meddelandehantering. Introducerat i Adobe Commerce 2.4.5 och senare.

## KaninMQ (AMQP)

Följande diagram visar Message Queue Framework:

![Ramverk för meddelandekö](../../assets/configuration/mq-framework.png)

- En utgivare är en komponent som skickar meddelanden till ett utbyte. Det vet vilket utbyte som ska publiceras och formatet på de meddelanden som skickas.

- Ett utbyte tar emot meddelanden från utgivare och skickar dem till köer. Även om [!DNL RabbitMQ] har stöd för flera typer av utbyten använder Commerce endast ämnesutbyten. Ett ämne innehåller en routningsnyckel, som innehåller textsträngar avgränsade med punkter. Formatet för ett ämnesnamn är `string1.string2`: till exempel `customer.created` eller `customer.sent.email`.

  Med förmedlaren kan du använda jokertecken när du anger regler för vidarebefordrande meddelanden. Du kan använda en asterisk (`*`) om du vill ersätta __-strängen eller ett nummertecken (`#`) om du vill ersätta 0 eller fler strängar. `customer.*` skulle till exempel filtreras på `customer.create` och `customer.delete`, men inte `customer.sent.email`. `customer.#` skulle dock filtreras på `customer.create`, `customer.delete` och `customer.sent.email`.

- En kö är en buffert som lagrar meddelanden.

- En konsument får meddelanden. Den vet vilken kö som ska användas. Den kan mappa behandlare av meddelandet till en viss kö.

## Apache ActiveMQ Artemis (STOMP)

Som ett alternativ till RabbitMQ stöder Adobe Commerce även [Apache ActiveMQ Artemis](https://activemq.apache.org/components/artemis/) som meddelandeansvarig med STOMP (Simple Text Oriented Messaging Protocol).

>[!NOTE]
>
>ActiveMQ Artemis introducerades i Adobe Commerce 2.4.5 och senare.

I följande diagram visas STOMP Framework med ActiveMQ Artemis:

![STOMP Framework](../../assets/configuration/stomp-framework.png)

### STOMP Framework-komponenter

- En **utgivare** är en komponent som skickar meddelanden till ett mål (kö eller ämne). Det vet vilken destination som ska publiceras och formatet på de meddelanden som skickas.

- Ett **mål** i STOMP har en liknande roll som utbyten i AMQP, tar emot meddelanden från utgivare och cirkulerar dem. STOMP använder direkt måladressering med ett hierarkiskt namngivningsmönster som använder punkter: till exempel `customer.created` eller `inventory.updated`.

  Adobe Commerce använder **ANYCAST**-adressläge för STOMP-destinationer, som tillhandahåller leverans av peka-till-punkt-meddelanden. I ANYCAST-läge levereras meddelanden till endast en konsument från en grupp tillgängliga konsumenter, vilket möjliggör belastningsutjämning och arbetsdistribution över flera konsumentinstanser.

- En **kö** är en buffert som lagrar meddelanden. Med ANYCAST-adressering säkerställer kön att meddelanden levereras till endast en konsument, även när flera konsumenter är anslutna till samma destination.

- En **konsument** tar emot meddelanden från destinationer. Den vet vilket mål som ska prenumereras på och kan bearbeta meddelanden med olika bekräftelselägen (auto, client eller client-individual).

## MySQL-adapter (reserv)

Ett grundläggande meddelandekösystem kan också skapas utan att externa meddelandehanterare används. I det här systemet lagrar ett MySQL-kort meddelanden i databasen. Tre databastabeller (`queue`, `queue_message` och `queue_message_status`) hanterar arbetsbelastningen för meddelandekön. Kronjobb säkerställer att konsumenterna kan ta emot meddelanden. Den här lösningen är inte särskilt skalbar. Externa meddelandeförmedlare som [!DNL RabbitMQ] eller Apache ActiveMQ Artemis bör användas när det är möjligt för produktionsmiljöer.

## Relaterad information

För installations- och konfigureringsinstruktioner:

- [Installera och konfigurera RabbitMQ](../../installation/prerequisites/rabbitmq.md)
- [Installera och konfigurera ActiveMQ-artemis](../../installation/prerequisites/activemq.md)
- [Hantera meddelandeköer](manage-message-queues.md)
- [Konsumenter i meddelandekön](consumers.md)
