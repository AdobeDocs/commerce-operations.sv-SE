---
title: The [!UICONTROL [!DNL RabbitMQ]], flik
description: Läs mer om [!UICONTROL [!DNL RabbitMQ]] flik för [!DNL Observation for Adobe Commerce].
exl-id: c5370c30-fed8-4f45-89c3-ef0d6ad41a89
feature: Configuration, Observability
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# The [!UICONTROL [!DNL RabbitMQ]] tab

The **[!UICONTROL [!DNL RabbitMQ]]** har information som är fokuserad på [!DNL RabbitMQ] signaler.

## [!UICONTROL [!DNL RabbitMQ] Infrastructure events]

![[!DNL RabbitMQ] Infrastrukturhändelser](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-1.jpeg)

The **[!UICONTROL [!DNL RabbitMQ] Infrastructure events]** bildruta visar infrastrukturshändelser som innehåller [!DNL RabbitMQ] som inträffade under den valda tidsramen:

* `%Response [error] for node [rabbit@host1]: unexpected http response from%`) as `unexpected_resp_node1`
* `%Response [error] for node [rabbit@host2]: unexpected http response from%`) as `unexpected_resp_node2`
* `%Response [error] for node [rabbit@host3]: unexpected http response from%`) as `unexpected_resp_node3`
* `%Response [error] for node [rabbit@host3]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host3": context deadline exceeded%`) as `node3_timeout_exceeded`
* `%Response [error] for node [rabbit@host1]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host1": context deadline exceeded%`) as `node1_timeout_exceeded`
* `%Response [error] for node [rabbit@host2]: Get "http://localhost:15672/api/healthchecks/node/rabbit@host2": context deadline exceeded%`) as `node2_timeout_exceeded`
* `%401 Unauthorized%`) as `401_unauth`
* `%401 Unauthorized%`) as `401_unauth`
* `%Service restarted: rabbitmq-server%`) as `rmq_service_restart`
* `%Response [failed] for node [rabbit@host1]: nodedown%`) as `rmq_node1_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) as `rmq_node2_down`
* `%Response [failed] for node [rabbit@host2]: nodedown%`) as `rmq_node2_down`
* `%Entity modified: exchange/bindings.destination%`) as `rmq_entity_modified`
* `%Entity modified: exchange/bindings.destination%`) as `rmq_entity_modified`
* `%Entity modified: queue/exclusive%`) as `rmq_entity_created_q_exclusive` `%Entity modified: queue/auto_delete%`) as `rmq_entity_q_delete`
* `%Entity modified: queue/durable%`) as `rmq_entity_modified_q_durable`
* `%Entity modified: version/management%`) as `rmq_entity_modified_ver_mgt`
* `%Entity modified: version/management%`) as `rmq_entity_modified_ver_mgt`

## [!UICONTROL [!DNL RabbitMQ] service start/stop signals]

![[!DNL RabbitMQ] start- och stoppsignaler](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-2.jpeg)

Den här bildrutan visas [!DNL RabbitMQ] start-/stoppsignaler för tjänsten som inträffade under den valda tidsramen:

* `%RabbitMQ is asked to stop...%`) as `rabbitmq_stop`
* `%Starting RabbitMQ%`) as `rabbitmq_start`

## [!UICONTROL [!DNL RabbitMQ] errors]

![[!DNL RabbitMQ] fel](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-3.jpeg)

Den här bildrutan visas [!DNL RabbitMQ] fel som inträffade under den valda tidsramen:

* `%exit with reason {case_clause,timeout} and stacktrace {rabbit_mgmt_wm_healthchecks%}` as `exit_timeout`
* `%client unexpectedly closed TCP connection%`) as `client_closed_tcp_conn`
* `%at undefined exit with reason shutdown in context shutdown_error%`) as `undef_exit`
* `%Connection attempt from disallowed node%`) as `disallowed_node`
* `%closing AMQP connection%`) as `rmq_err_amqp_conn`

## [!UICONTROL [!DNL RabbitMQ] node status]

![[!DNL RabbitMQ] nodstatus](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-4.jpeg)

* `%rabbit on node rabbit@host1 down%`) as `rmq_node1_down`
* `%rabbit on node rabbit@host2 down%`) as `rmq_node2_down`
* `%rabbit on node rabbit@host3 down%`) as `rmq_node3_down`
* `%rabbit on node rabbit@host1 up%`) as `rmq_node1_up`
* `%rabbit on node rabbit@host2 up%`) as `rmq_node2_up`
* `%rabbit on node rabbit@host3 up%`) as `rmq_node3_up`

## [!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]

![[!DNL RabbitMQ] Status för sammanfattning på hög nivå per kö](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-5.jpeg)

The **[!UICONTROL [!DNL RabbitMQ] Message High-Level Summary status by Queue]** diagram visar antalet publicerade meddelanden i [!DNL RabbitMQ] kön för den valda tidsramen.

## [!UICONTROL [!DNL RabbitMQ] Message Detail Summary]

![[!DNL RabbitMQ] Sammanfattning av meddelandedetaljer](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-6.jpeg)

* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) as `queue_err`
* `%report.ERROR: Cron Job consumers_runner has an error: NOT_FOUND - no queue%`) as `queue_err`
* `%authenticated and granted access to vhost%`) as `auth`
* `%closing AMQP connection%`) as `close_conn`

## [!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]

![[!DNL RabbitMQ] Köförbrukning MB](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-7.jpeg)

The **[!UICONTROL [!DNL RabbitMQ] Queue Consumption MB]** diagram visar hur många byte som används av varje [!DNL RabbitMQ] kön över den valda tidsramen.

## [!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]

![[!DNL RabbitMQ] Publicerade meddelanden per kö](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-8.jpeg)

The **[!UICONTROL [!DNL RabbitMQ] Published Messages by Queue]** diagram visar hur många byte som används av varje [!DNL RabbitMQ] kön över den valda tidsramen.

## [!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]

![[!DNL RabbitMQ] Publicerat meddelandeflöde efter kö](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-9.jpeg)

The **[!UICONTROL [!DNL RabbitMQ] Published Message Throughput by Queue]** diagram visar det genomsnittliga antalet publicerade meddelanden per sekund för varje [!DNL RabbitMQ] kön över den valda tidsramen.

## [!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]

![[!DNL RabbitMQ] Totalt meddelandeflöde efter kö](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-10.jpeg)

The **[!UICONTROL [!DNL RabbitMQ] Total Message Throughput by Queue]** diagram visar det genomsnittliga totala antalet meddelanden per sekund för varje [!DNL RabbitMQ] kön över den valda tidsramen.

## [!UICONTROL [!DNL RabbitMQ] Consumers by Queue]

![[!DNL RabbitMQ] Konsumenter efter kö](../../assets/tools/observation-for-adobe-commerce/rabbitmq-tab-11.jpeg)

The **[!UICONTROL [!DNL RabbitMQ] Consumers by Queue]** diagram visar det genomsnittliga totala antalet konsumenter per [!DNL RabbitMQ] kön över den valda tidsramen.
