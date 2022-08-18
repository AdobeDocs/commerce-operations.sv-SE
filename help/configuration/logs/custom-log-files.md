---
title: Skriv till anpassad loggfil
description: Lär dig hur du ställer in anpassade loggfiler.
contributor_name: Atwix
contributor_link: https://www.atwix.com/
source-git-commit: 2c12c6ea6e7b6ffeb07bbda17ded34e39de6656a
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 0%

---


# Skriva till en anpassad loggfil

The `Magento\Framework\Logger` -modulen innehåller följande hanterarklasser:

| Klass | Loggfil |
| ----- | -------- |
| [Magento\Framework\Logger\Handler\Base][base] | - |
| [Magento\Framework\Logger\Handler\Debug][debug] | `/var/log/debug.log` |
| [Magento\Framework\Logger\Handler\Exception][exception] | `/var/log/exception.log` |
| [Magento\Framework\Logger\Handler\Syslog][syslog] | - |
| [Magento\Framework\Logger\Handler\System][system] | `/var/log/system.log` |

Du kan hitta dem i `lib/internal/Magento/Framework/Logger/Handler` katalog.

Du kan använda någon av följande metoder för att logga in i en anpassad fil:

- Konfigurera en anpassad loggfil i `di.xml`
- Ställa in en anpassad fil i den anpassade logghanterarklassen

## Konfigurera en anpassad loggfil i `di.xml`

I det här exemplet visas hur du använder [virtuella typer](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html#virtual-types) till logg `debug` meddelanden till en anpassad loggfil i stället för en standard `/var/log/debug.log`.

1. I `di.xml` -fil i modulen, definiera en anpassad loggfil som [virtuell typ](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html#virtual-types).

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomDebug" type="Magento\Framework\Logger\Handler\Base">
       <arguments>
           <argument name="fileName" xsi:type="string">/var/log/payment.log</argument>
        </arguments>
   </virtualType>
   ```

   The `name` värde för `Magento\Payment\Model\Method\MyCustomDebug` måste vara unika.

1. Definiera hanteraren i en annan [virtuell typ](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html#virtual-types) med ett unikt `name`:

   ```xml
   <virtualType name="Magento\Payment\Model\Method\MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
           </argument>
       </arguments>
   </virtualType>
   ```

1. Mata in `MyCustomLogger` [virtuell typ](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html#virtual-types) i `Magento\Payment\Model\Method\Logger` objekt:

   ```xml
   <type name="Magento\Payment\Model\Method\Logger">
       <arguments>
           <argument name="logger" xsi:type="object">Magento\Payment\Model\Method\MyCustomLogger</argument>
       </arguments>
   </type>
   ```

1. Klassen virtual `Magento\Payment\Model\Method\MyCustomDebug` injiceras i `debug` hanteraren för `$logger` -egenskapen i `Magento\Payment\Model\Method\Logger` klassen.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="debug" xsi:type="object">Magento\Payment\Model\Method\MyCustomDebug</item>
   </argument>
   ```

Undantagsmeddelanden loggas in i `/var/log/payment.log` -fil.

## Konfigurera en anpassad loggfil i klassen för logghanterare

I det här exemplet visas hur du använder en anpassad logghanterarklass för att logga `error` meddelanden till en specifik loggfil.

1. Skapa en klass som loggar data. I det här exemplet definieras klassen i `app/code/Vendor/ModuleName/Logger/Handler/ErrorHandler.php`.

   ```php
   <?php
   /**
    * @author Vendor
    * @copyright Copyright (c) 2019 Vendor (https://www.vendor.com/)
    */
   namespace Vendor\ModuleName\Logger\Handler;
   
   use Magento\Framework\Logger\Handler\Base as BaseHandler;
   use Monolog\Logger as MonologLogger;
   
   /**
    * Class ErrorHandler
    */
   class ErrorHandler extends BaseHandler
   {
       /**
        * Logging level
        *
        * @var int
        */
       protected $loggerType = MonologLogger::ERROR;
   
       /**
        * File name
        *
        * @var string
        */
       protected $fileName = '/var/log/my_custom_logger/error.log';
   }
   ```

1. Definiera hanteraren för den här klassen som en [virtuell typ](https://devdocs.magento.com/guides/v2.4/extension-dev-guide/build/di-xml-file.html#virtual-types) i modulen `di.xml` -fil.

   ```xml
   <virtualType name="MyCustomLogger" type="Magento\Framework\Logger\Monolog">
       <arguments>
           <argument name="handlers" xsi:type="array">
               <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
           </argument>
       </arguments>
   </virtualType>
   ```

   `MyCustomLogger` är en unik identifierare.

1. I `type` definierar du klassnamnet där den anpassade logghanteraren matas in. Använd det virtuella typnamnet från föregående steg som argument för den här typen.

   ```xml
   <type name="Vendor\ModuleName\Observer\MyObserver">
       <arguments>
           <argument name="logger" xsi:type="object">MyCustomLogger</argument>
       </arguments>
   </type>
   ```

   Källkod för `Vendor\ModuleName\Observer\MyObserver` klass:

   ```php
   <?php
   /**
    * @author Vendor
    * @copyright Copyright (c) 2019 Vendor (https://www.vendor.com/)
    */
   declare(strict_types=1);
   
   namespace Vendor\ModuleName\Observer;
   
   use Psr\Log\LoggerInterface as PsrLoggerInterface;
   use Exception;
   use Magento\Framework\Event\ObserverInterface;
   use Magento\Framework\Event\Observer;
   
   /**
    * Class MyObserver
    */
   class MyObserver implements ObserverInterface
   {
       /**
        * @var PsrLoggerInterface
        */
       private $logger;
   
       /**
        * MyObserver constructor.
        *
        * @param PsrLoggerInterface $logger
        */
       public function __construct(
           PsrLoggerInterface $logger
       ) {
           $this->logger = $logger;
       }
   
       /**
        * @param Observer $observer
        */
       public function execute(Observer $observer)
       {
           try {
               // some code goes here
           } catch (Exception $e) {
               $this->logger->error($e->getMessage());
           }
       }
   }
   ```

1. Klassen `Vendor\ModuleName\Logger\Handler\ErrorHandler` injiceras i `error` hanteraren för `$logger` -egenskapen i `Vendor\ModuleName\Observer\MyObserver`.

   ```xml
   ...
   <argument name="handlers" xsi:type="array">
       <item name="error" xsi:type="object">Vendor\ModuleName\Logger\Handler\ErrorHandler</item>
   </argument>
   ...
   ```

Undantagsmeddelanden loggas i `/var/log/my_custom_logger/error.log` -fil.

<!-- link definitions -->

[base]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Base.php
[debug]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Debug.php
[exception]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Exception.php
[syslog]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/Syslog.php
[system]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/Logger/Handler/System.php