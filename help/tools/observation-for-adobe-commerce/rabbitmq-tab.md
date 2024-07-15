---
title: Fliken [!UICONTROL [!DNL RabbitMQ]]
description: Läs mer om fliken [!UICONTROL [!DNL RabbitMQ]] i  [!DNL Observation for Adobe Commerce].
exl-id: c5370c30-fed8-4f45-89c3-ef0d6ad41a89
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Fliken [!UICONTROL [!DNL RabbitMQ]]

Fliken **[!UICONTROL [!DNL RabbitMQ]]** innehåller information som är inriktad på [!DNL RabbitMQ] signaler.

## [!UICONTROL [!DNL RabbitMQ] Infrastructure events]

![[!DNL RabbitMQ] Infrastrukturhändelser](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

Bildrutan **[!UICONTROL [!DNL RabbitMQ] Infrastructure events]** innehåller infrastrukturhändelser som innehåller [!DNL RabbitMQ] och som inträffade under den valda tidsramen:

* `%Response [error] for node [rabbit@host1]: unexpected http response from%`) som `unexpected_resp_node1`
* `%Response [error] for node [rabbit@host2]: unexpected http response from%`) som `unexpected_resp_node2`
* `%Response [error] for node [rabbit@host3]: unexpected http response from%`) som `unexpected_resp_node3`
* `%Response [error] for node [rabbit@host3]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host3": context deadline exceeded%`) som `node3_timeout_exceeded`
* `%Response [error] for node [rabbit@host1]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host1": context deadline exceeded%`) som `node1_timeout_exceeded`
* `%Response [error] for node [rabbit@host2]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host2": context deadline exceeded%`) som `node2_timeout_exceeded`
* `%401 Unauthorized%`) som `401_unauth`
* `%401 Unauthorized%`) som `401_unauth`
* `%Service restarted: rabbitmq-server%`) som `rmq_service_restart`
* `%Response [failed] for node [rabbit@host1]: nodedown%`) som `rmq_node1_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) som `rmq_node2_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) som `rmq_node2_down`
* `%Entity modified: exchange/bindings.destination%`) som `rmq_entity_modified`
* `%Entity modified: exchange/bindings.destination%`) som `rmq_entity_modified`
* `%Entity modified: queue/exclusive%`) som `rmq_entity_created_q_exclusive` `%Entity modified: queue/auto_delete%`) som `rmq_entity_q_delete`
* `%Entity modified: queue/durable%`) som `rmq_entity_modified_q_durable`
* `%Entity modified: version/management%`) som `rmq_entity_modified_ver_mgt`
* `%Entity modified: version/management%`) som `rmq_entity_modified_ver_mgt`

## [!UICONTROL [!DNL RabbitMQ] service start/stop signals]

![[!DNL RabbitMQ] start-/stoppsignaler för tjänst ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

I den här bildrutan visas [!DNL RabbitMQ] start-/stoppsignaler för tjänsten som inträffade under den valda tidsbildrutan:

* `%RabbitMQ is asked to stop...%`) som `rabbitmq_stop`
* `%Starting RabbitMQ%`) som `rabbitmq_start`

## [!UICONTROL [!DNL RabbitMQ] errors]

![[!DNL RabbitMQ] fel](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

Den här bildrutan visar [!DNL RabbitMQ] fel som inträffade under den valda tidsbildrutan:

* `%exit with reason {case_clause,timeout} and stacktrace {rabbit_mgmt_wm_healthchecks%}` som `exit_timeout`
* `%client unexpectedly closed TCP connection%`) som `client_closed_tcp_conn`
* `%at undefined exit with reason shutdown in context shutdown_error%`) som `undef_exit`
* `%Connection attempt from disallowed node%`) som `disallowed_node`
* `%closing AMQP connection%`) som `rmq_err_amqp_conn`

## [!UICONTROL [!DNL RabbitMQ] node status]

![[!DNL RabbitMQ]-nodstatus](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* `%rabbit on node rabbit@host1 down%`) som `rmq_node1_down`
* `%rabbit on node rabbit@host2 down%`) som `rmq_node2_down`
* `%rabbit on node rabbit@host3 down%`) som `rmq_node3_down`
* `%rabbit on node rabbit@host1 up%`) som `rmq_node1_up`
* `%rabbit on node rabbit@host2 up%`) som `rmq_node2_up`
* `%rabbit on node rabbit@host3 up%`) som `rmq_node3_up`

## [!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]

![[!DNL RabbitMQ]-meddelande, högnivåsammanfattning, status per kö](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

Diagrammet **[!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]** visar antalet publicerade meddelanden i kön [!DNL RabbitMQ] för den valda tidsramen.

## [!UICONTROL [!DNL RabbitMQ] Message Detail Summary]

![[!DNL RabbitMQ] Sammanfattning av meddelandedetaljer](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) som `queue_err`
* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) som `queue_err`
* `%authenticated and granted access to vhost%`) som `auth`
* `%closing AMQP connection%`) som `close_conn`

## [!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]

![[!DNL RabbitMQ] Köförbrukning MB](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

Diagrammet **[!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]** visar antalet byte som används av varje [!DNL RabbitMQ]-kö under den valda tidsramen.

## [!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]

![[!DNL RabbitMQ] Publicerade meddelanden per kö ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

Diagrammet **[!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]** visar antalet byte som används av varje [!DNL RabbitMQ]-kö under den valda tidsramen.

## [!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]

![[!DNL RabbitMQ] Publicerat meddelandegenomflöde efter kö ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

Diagrammet **[!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]** visar det genomsnittliga antalet publicerade meddelanden per sekund för varje [!DNL RabbitMQ]-kö under den valda tidsramen.

## [!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]

![[!DNL RabbitMQ] Totalt meddelandegenomflöde per kö ](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

Diagrammet **[!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]** visar det genomsnittliga totala antalet meddelanden per sekund för varje [!DNL RabbitMQ]-kö under den valda tidsramen.

## [!UICONTROL [!DNL RabbitMQ] Consumers by Queue]

![[!DNL RabbitMQ] Användare efter kö](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

Diagrammet **[!UICONTROL [!DNL RabbitMQ] Consumers by Queue]** visar det genomsnittliga totala antalet konsumenter för varje [!DNL RabbitMQ]-kö under den valda tidsramen.
