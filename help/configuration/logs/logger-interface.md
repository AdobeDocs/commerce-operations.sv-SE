---
title: Logggränssnitt
description: Kom igång med loggningsgränssnittet.
source-git-commit: f489c3e68c91c6f2e16bff233cf59472ed684b5c
workflow-type: tm+mt
source-wordcount: '186'
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

Ett sätt att göra detta beskrivs i [Loggdatabasaktivitet](../logs/database-activity.md) exempel.

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

Exemplet nedan visar att `SomeModel` får ett `\Psr\Log\LoggerInterface` objekt med konstruktorinjektion. I en metod `doSomething`, om ett fel inträffar, loggas den på en metod `critical` (`$this->logger->critical($e);`).

[RFC 5424](https://datatracker.ietf.org/doc/html/rfc5424) definierar åtta loggnivåer (felsökning, info, notifiering, varning, fel, kritisk, varning och nödsituation).
