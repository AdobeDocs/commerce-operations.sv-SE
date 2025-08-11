---
title: 'AC-14984: SSL-anslutningsproblem med php-amqplib/php-amqplib ^3.2.0'
description: Använd korrigeringen AC-14984 för att åtgärda Adobe Commerce-problemet där SSL-anslutningen misslyckas och ett fel uppstår när du använder php-amqplib/php-amqplib version ^3.2.0.
feature: System
role: Admin, Developer
type: Troubleshooting
source-git-commit: 2523361a6cc9c21ad682dcd3270680cb28c18e60
workflow-type: tm+mt
source-wordcount: '292'
ht-degree: 0%

---


# AC-14984: SSL-anslutningsproblem med php-amqplib/php-amqplib ^3.2.0

Korrigeringen AC-14984 åtgärdar ett problem där SSL-anslutningen misslyckas med ett fel när `php-amqplib/php-amqplib` version `^3.2.0` används. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.67 har installerats. Patch-ID:t är AC-14984. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p10

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p10 - 2.4.6-p11

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

SSL-anslutningen misslyckas med ett fel när `php-amqplib/php-amqplib` version `^3.2.0` används.

<u>Steg som ska återskapas</u>:

1. Konfigurera SSL-anslutningen i `app/env.php`:

```
'queue' =>
  array (
    'amqp' =>
    array (
      'host' => 'rabbitmq.example.com',
      'port' => '11213',
      'user' => 'magento',
      'password' => 'magento',
      'virtualhost' => '/',
      'ssl' => 'true',
      'ssl_options' => [
        'verify_peer' => true,
        'verify_peer_name' => false
      ],
    ),
  ),
```

1. Kör `bin/magento setup:upgrade` om det är första gången du konfigurerar kön.
1. Kör en kökonsument, till exempel: `bin/magento queue:consumers:start async.operations.all`

<u>Förväntade resultat</u>:

Kökonsumenten startar och bearbetar meddelanden utan fel.

<u>Faktiska resultat</u>:

Ett felmeddelande visas i loggarna:

```
{
  "message": "Invalid frame type 21",
  "context": {},
  "level": "error",
  "level_name": "ERROR",
  "channel": "report",
  "datetime": "2025-05-14T07:00:00.000000+00:00",
  "extra": {},
  "@timestamp": "2025-05-14T07:00:00.000000X",
  "severity": "ERROR",
  "original_level": 400,
  "full_message": "Invalid frame type 21\n#0 /app/vendor/php-amqplib/php-amqplib/PhpAmqpLib/Connection/AbstractConnection.php(651): PhpAmqpLib\\Connection\\AbstractConnection->wait_frame(3.0)\n#1 /app/vendor/php-amqplib/php-amqplib/PhpAmqpLib/Channel/AbstractChannel.php(235): PhpAmqpLib\\Connection\\AbstractConnection->wait_channel(0, 3.0)\n#2 /app/vendor/php-amqplib/php-amqplib/PhpAmqpLib/Channel/AbstractChannel.php(352): PhpAmqpLib\\Channel\\AbstractChannel->next_frame(3.0)\n#3 /app/vendor/php-amqplib/php-amqplib/PhpAmqpLib/Connection/AbstractConnection.php(264): PhpAmqpLib\\Channel\\AbstractChannel->..."
}
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
