---
title: Logggränssnitt
description: Kom igång med loggningsgränssnittet.
feature: Configuration, Logs
exl-id: fdb1b431-405a-4c32-aff1-9e50bf0a2c90
source-git-commit: 991bd5fb34a2ffe61aa194ec46e2b04b4ce5b3e7
workflow-type: tm+mt
source-wordcount: '111'
ht-degree: 0%

---

# Logggränssnitt

Om du vill börja arbeta med en logger måste du skapa en instans av `\Psr\Log\LoggerInterface`. Med det här gränssnittet kan du anropa följande funktioner för att skriva data till loggfiler:

- [alert()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L43)
- [critical()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L55)
- [debug()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L111)
- [Emergency()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L30)
- [error()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L66)
- [info()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L101)
- [log()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L122)
- [notice()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L89)
- [warning()](https://github.com/php-fig/log/blob/master/src/LoggerInterface.php#L79)

Ett sätt att göra detta beskrivs i exemplet [Loggdatabasaktivitet](../logs/database-activity.md).

Ett annat sätt är:

```php
class SomeModel
 {
     private $logger;

     public function __construct(\Psr\Log\LoggerInterface $logger)
     {
         $this->logger = $logger;
     }

     public function doSomething()
     {
         try {
             //do something
         } catch (\Exception $e) {
             $this->logger->critical('Error message', ['exception' => $e]);
         }
     }
 }
```

Exemplet ovan visar att `SomeModel` tar emot ett `\Psr\Log\LoggerInterface`-objekt med hjälp av konstruktorinjektion. Om ett fel inträffar i en metod `doSomething` loggas den till metoden `critical` (`$this->logger->critical($e);`).

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424) definierar åtta loggnivåer (felsökning, information, meddelanden, varning, fel, kritisk, varning och nödsituation).
