---
title: Bästa tillvägagångssätt för att ändra PHP-kod från kärnan och tredje part
description: Lär dig hur och när du ska ändra Adobe Commerce och tredjeparts PHP-kod.
role: Developer, Architect
feature: Best Practices
last-substantial-update: 2023-12-8
source-git-commit: ab02552939d595627f0de83b8508c7cd21777642
workflow-type: tm+mt
source-wordcount: '1747'
ht-degree: 0%

---

# Bästa tillvägagångssätt för att ändra eller åsidosätta PHP-kod från kärnan och tredje part

I det här dokumentet beskrivs de effektivaste strategierna när det uppstår behov av att ändra funktionaliteten, resultatet eller indata för kod som du inte har skapat eller inte har direkt kontroll över. Med andra ord, kärnkod och tredjepartskod. Det här dokumentet fokuserar främst på PHP-kod i serverdelen.

## Metoder för att ändra kod

När du ändrar kod är det viktigt att tänka på omfattningen av dina ändringar. Ändringarnas&quot;omfång&quot; avser hur omfattande effekterna av kodändringarna är. Det bästa sättet är att basera beslutet om hur den slutliga implementeringen ska slutföras baserat på det alternativ som har minsta utrymme och minsta resursanvändning. Ju mer omfattande kodåsidosättningarna är, desto mer avviker ett utvecklingsteam från Adobe Commerce kärnfunktioner, vilket ökar sannolikheten för fel och gör det ännu svårare att underhålla kodbasen i framtiden.

### Lappa

En patch är en fil som innehåller instruktioner om att direkt ändra kod i en fil som inte är direkt kontrollerad av utvecklingsteamet. Det här är ett alternativ som vanligtvis bör betraktas som en sista utväg när det inte finns några andra alternativ. Patchar är avsedda att vara en tillfällig lösning. Om du måste skapa ett plåster bör du som regel ta ut plåstret med en mer permanent lösning inom de följande 2-4 veckorna. 

Patchar bryts lätt. Om filerna som korrigeringsmålet ska uppdateras gör det ofta att korrigeringen slutar fungera. Det beror på att en korrigeringsfil innehåller radnummer och kolumnnummer som specifikt anger vad som ska ändras av korrigeringen. Om något inte stämmer överens med vad som förväntades för korrigeringen, upphör det att gälla och koden bryts.

```bash
diff --git a/vendor/magento/module-quote/Model/QuoteManagement.php b/vendor/magento/module-quote/Model/QuoteManagement.php
index 51b68411d40..ac4a3468322 100644
--- a/vendor/magento/module-quote/Model/QuoteManagement.php
+++ b/vendor/magento/module-quote/Model/QuoteManagement.php
@@ -424,8 +424,9 @@ class QuoteManagement implements CartManagementInterface
                 }
             }
             $quote->setCustomerIsGuest(true);
-            $groupId = $customer ? $customer->getGroupId() : GroupInterface::NOT_LOGGED_IN_ID;
-            $quote->setCustomerGroupId($groupId);
+            $quote->setCustomerGroupId(
+                $quote->getCustomerId() ? $customer->getGroupId() : GroupInterface::NOT_LOGGED_IN_ID
+            );
         }
  
         $remoteAddress = $this->remoteAddress->getRemoteAddress();
```

#### Vad som kan ändras med en patch

Vad som helst. Alla tecken i en målfil kan ändras. Patchar är inte begränsade till någon viss filtyp eller kodspråk. Vanligtvis använder du en patch för att skapa målfiler i `vendor` katalog. 

#### När ska en patch användas

Om du inser att det inte finns något annat alternativ. Om leverantören till exempel ännu inte har publicerat en korrigering för koden kan du använda en korrigering för att temporärt åtgärda problemet medan du väntar på en permanent lösning.

#### Nackdelar

Patchar bryts lätt. Så fort målkoden ändras slutar lagningen att fungera. De är endast avsedda att vara en kortsiktig lösning.

### Inställningar

En inställning är ett koncept som utvecklats i Adobe Commerce. Det är i stort sett en ersättning för PHP-klassen.

Adobe Commerce-plattformen använder en&quot;objekthanterare&quot; för att instansiera PHP-klasser eftersom den inte instansierar PHP-klasser med det nya nyckelordet, som är fallet i traditionella PHP-program. I stället korsrefererar objekthanteraren namnet på den PHP-klass som ska instansieras mot en kompilerad konfiguration för att avgöra om någon modul har deklarerat en inställning för den ursprungliga klassen. Om en inställning för PHP-klassen hittas instansierar objekthanteraren i stället den angivna klassen.

Observera att (vanligtvis) den nya PHP-klassen som ersätter den ursprungliga PHP-klassen utökar/ärver från den ursprungliga PHP-klassen. Detta görs av några skäl:

- För att säkerställa att beroendeinjen/typograferingen följs. Annars inträffar ett allvarligt fel och programmet avbryts.
- För att möjliggöra minimal kodskrivning. Om den ursprungliga PHP-klassen innehåller tio metoder, men du bara behöver åsidosätta en metod, kan du vanligtvis ändra en metod ensam och låta de andra nio metoderna vara oförändrade. Detta är viktigt för att säkerställa att du inte blockerar uppdateringar av kärnfunktionen eftersom plattformen uppgraderas till nya versioner.

#### Ange en inställning

Det är en ganska enkel process att deklarera en inställning. En enda kodrad måste läggas till i en `di.xml` i en modul. Detta kan göras globalt eller inom vilket Adobe Commerce-område som helst, till exempel `frontend`, `adminhtml`, `graphql`, `webapi_rest`och `crontab`.

```xml
<preference for="Magento\Elasticsearch7\SearchAdapter\Adapter" type="Vendor\Namespace\Adapter\AlgoliaElasticSearch7Adapter"/>
```

```php
<?php

declare(strict_types=1);

namespace Vendor\Namespace\Adapter;

class AlgoliaElasticSearchAdapter extends \Magento\Elasticsearch7\SearchAdapter\Adapter
{
}
```

#### Vad som kan ändras med en inställning

Endast PHP-klasser kan åsidosättas med en inställning. I PHP-klassen kan du ändra publika och skyddade metoder och egenskaper. För offentliga och skyddade metoder kan du åsidosätta metoden helt och hållet eller ändra argumenten som börjar (eller resultatet som kommer från) den ursprungliga överordnade metoden.

Privata metoder kan inte åsidosättas av tekniska skäl. Du kan dock skapa en egen ersättning för den ursprungliga privata metoden. Du kan också ge den ett godtyckligt namn och använda det ursprungliga namnet. Det spelar ingen roll eftersom en privat metod bara finns i den faktiska filen som innehåller den. Om du vill åsidosätta en privat metod måste du åsidosätta eller ändra den publika eller skyddade metoden som anropar den ursprungliga privata metoden och du måste ersätta din egen funktion.

#### När en inställning ska användas

Återigen bör du använda inställningarna när det inte finns något annat alternativ och när du inte kan uppnå ditt mål med beroendeinjicering, plugin-program eller observatör. Ibland behöver du en inställning om du behöver ändra eller åsidosätta privata eller skyddade metoder eller egenskaper. Det bör noteras att inställningarna bör användas sparsamt. De är en ganska&quot;girig&quot; metod för att ändra programmet och du tar på dig ägarskapet för PHP-klassen. Detta kan leda till konflikter med moduler från tredje part och kan blockera uppdateringar av huvudklassen och leda till feldiagnoser. Adobe Commerce-plattformen har tagits fram för att innehålla andra sätt att ändra den underliggande koden med mindre utrymme.

#### Nackdelar

Inställningar är ett bra sätt att ändra kod och bör bara användas när andra alternativ inte finns. Inställningar kan ofta leda till konflikter inom kodbasen och ännu värre är att de kan blockera viktiga uppdateringar som sker vid plattformsuppgraderingar. 

### Observer

En observatör är en händelseavlyssnare som finns i många program, plattformar, bibliotek och kodningsspråk. Konceptet är inte unikt för Adobe Commerce. Observatörer har bakats in i plattformen sedan Magento 1-dagarna och anses vara ett primärt val när det gäller att ändra kärnkod och tredjepartskod. 

Huvudkodbasen och eventuella tredjepartsmoduler kan skicka en händelse på en vald plats i koden. Observatören, som deklareras i en `events.xml` och lyssnar efter den skickade händelsen per namn, kan arbeta på global nivå eller begränsas till ett Adobe Commerce-område, till exempel `frontend`, `adminhtml`, `graphql`, `webapi_rest`och `crontab`.

#### Deklarera en observatör

Observatörer kan konfigureras på en global eller områdesspecifik `events.xml` -fil.

```xml
    <event name="sales_model_service_quote_submit_before">
        <observer name="set_reward_flag_order" instance="Adobe\RewardAdjustments\Observer\SetOrderRewardFlag" />
    </event>
```

```php
<?php

declare(strict_types=1);

namespace Adobe\RewardAdjustments\Observer;

use Magento\Framework\Event\ObserverInterface;
use Magento\Framework\Event\Observer;
use Magento\Quote\Model\Quote;
use Magento\Sales\Api\Data\OrderInterface;

class SetOrderRewardFlag implements ObserverInterface
{
    /**
     * @param Observer $observer
     * @return void
     */
    public function execute(Observer $observer)
    {
        $event = $observer->getEvent();
        /* @var $order OrderInterface */
        $order = $event->getOrder();
        /** @var $quote Quote $quote */
        $quote = $event->getQuote();

        // do something to the order and/or quote object here
    }
}
```

#### Vad som kan ändras med en observatör

Observatörer kan bara tillämpa PHP-kod inom Adobe Commerce. Du kan bara ändra specifika data och objekt som skickas med händelseutsändning.

#### När en observatör ska användas

När det finns tillgängligt! Om observatörerna var mer allmänt tillgängliga och flexibla skulle observatörerna få det två största stället i listan. Observatörer har mindre bearbetningskostnader än plugin-program, de är mindre tillgängliga och mindre flexibla.

#### Nackdelar

Även om observatörer är ett utmärkt sätt att snurra och ändra kod, måste utskicket av händelserna läggas till i kärnkoden eller tredjepartskoden för att koden ska kunna avlyssna. Detta gör att konceptet med att använda observatörer är lite begränsat. Du är begränsad till händelser som en utvecklare har haft för avsikt att inkludera i koden.

En annan begränsande faktor för observatörer är också att den skickade händelsen bara ger tillgång till specifika data och objekt som utvecklaren bestämde sig för att skicka med händelsen.

### Plugin

Ett plugin-program är ett flexibelt koncept som introducerats i Adobe Commerce. Du kan hämta, ersätta och ändra alla offentliga PHP-metoder. Med plugin-program kan du ändra argumenten som går in i en metod innan målmetoden körs, ändra resultatet efter att målmetoden har körts eller helt ersätta målmetoden. Du kan ändra många metoder i en PHP-målklass i en enda plugin-fil. Du kan även använda `$subject` argument för att köra alla publika metoder som finns i den PHP-riktade klassen.

#### Deklarera ett plugin-program

Plugin-program kan konfigureras på en global eller områdesspecifik `di.xml` -fil.

```xml
    <type name="Magento\Catalog\Api\CategoryRepositoryInterface">
        <plugin name="Adobe\CatalogAdjustments\Plugin\CategoryRepositoryPlugin" type="Adobe\CatalogAdjustments\Plugin\CategoryRepositoryPlugin"/>
    </type>
```

```php
<?php

declare(strict_types=1);

namespace Adobe\CatalogAdjustments\Plugin;

class CategoryRepositoryPlugin
{
    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param int $categoryId
     * @param int $storeId
     *
     * @return array
     */
    public function beforeGet($subject, $categoryId, $storeId = null): array
    {
        // modify the $categoryId or $storeId arguments or perform some other functionality prior to execution of the `get` method
        return [$categoryId, $storeId];
    }

    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param \Closure $origMethod
     * @param int $categoryId
     * @param int $storeId
     *
     * @return \Magento\Catalog\Api\Data\CategoryInterface
     */
    public function aroundGet($subject, $origMethod, $categoryId, $storeId = null): \Magento\Catalog\Api\Data\CategoryInterface
    {
        // here you can do something before calling the original method
        $result = $origMethod($categoryId, $storeId);
        // here you can do something after calling the original method
        // you can also NOT call the original method at all and instead, substitute our own functionality

        return $result;
    }

    /**
     * @param \Magento\Catalog\Api\CategoryRepositoryInterface $subject
     * @param \Magento\Catalog\Api\Data\CategoryInterface $result
     * @param int $categoryId
     * @param int $storeId
     *
     * @return \Magento\Catalog\Api\Data\CategoryInterface
     */
    public function afterGet($subject, $result, $categoryId, $storeId = null): \Magento\Catalog\Api\Data\CategoryInterface
    {
        // here you modify the result produced by the original `get` function or you can execute some other functionality
        // note that you also have access to the original function arguments. it's too late to modify them, but if needed, they are available for reading

        return $result;
    }
}
```

#### Vad som kan ändras med ett plugin-program

Den här funktionen är bara tillgänglig för PHP-målklasser. Du kan ändra indata eller utdata för en offentlig metod och du kan använda ett plugin-program för att aktivera andra funktioner. Om flera plugin-program har samma PHP-klass som mål kan du ange en sorteringsordning för körning av plugin-program så att plugin-programmet kan köras före eller efter andra plugin-program.

#### När ett plugin-program ska användas

När beroendeersättning inte är tillgänglig. Plugin-program används ofta i hela kärnkodbasen, tredjepartskoden, och kan användas ofta i din egen, anpassade kod. När du måste ändra funktioner som inte ägs eller styrs av din egen kod är det oftast en plugin som är rätt väg.

#### Nackdelar

Det går inte att ändra skyddade metoder eller egenskaper. Bearbetningskostnaderna är högre än för en observatör. Det är inte ett argument för att inte använda plugin-program. Skillnaden är enkel. Men det är något bra att tänka på.

### Beroendeersättning

Beroendeinjektion är ett objektorienterat standardkodningskoncept där du skickar dina nödvändiga beroenden till en klass med konstruktorn. Adobe Commerce-plattformen tar dock ett steg längre genom att ge flera sätt att ersätta beroenden med XML. I princip, beroendeersättning. Beroendeersättning passar inte för alla situationer, men gör det möjligt att skriva kod så lite som möjligt, har låg belastning och du kan endast målinrikta exakta kodbitar på ett begränsat sätt. Du kan ändra privata och skyddade metoder med beroendeersättning.

#### Så här använder du beroendeersättning

Beroendeersättning kan göras globalt eller områdesspecifikt.

```php
<?php

class SomeClass
{
    public function __construct(
        private readonly AllowedCountries $allowedCountriesReader
    ) {}

    /**
     * Check is address allowed for store
     *
     * @param AddressInterface $address
     * @param int|null $storeId
     * @return bool
     */
    private function isAddressAllowedForWebsite(AddressInterface $address, $storeId): bool
    {
        $allowedCountries = $this->allowedCountriesReader->getAllowedCountries(ScopeInterface::SCOPE_STORE, $storeId);

        return in_array($address->getCountryId(), $allowedCountries);
    }
}
```

```php
<?php

use Magento\Store\Model\ScopeInterface;

class OverrideAllowedCountries extends AllowedCountries
{
    /**
     * Retrieve all allowed countries for scope or scopes
     *
     * @param string $scope
     * @param string|null $scopeCode
     * @return array
     * @since 100.1.2
     */
    public function getAllowedCountries(
        $scope = ScopeInterface::SCOPE_WEBSITE,
        $scopeCode = null
    ) {
        // do some stuff here
        // you can call the original method or override it completely
        
        return $something;
    }
}
```

```xml
<?xml version="1.0"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="urn:magento:framework:ObjectManager/etc/config.xsd">
    <type name="Vendor\Namespace\SomeClass">
        <arguments>
            <argument name="allowedCountriesReader" xsi:type="object">OverrideAllowedCountries</argument>
        </arguments>
    </type>
</config>
```

När du har utfört de här stegen har du ändrat beteendet för en privat metod.

#### Vad som kan ändras med beroendeersättning

Offentliga, skyddade och privata metoder kan ändras med beroendeersättning. Precis som med ett plugin-program kan du ändra argumenten som ska användas, helt ersätta funktionen helt och hållet eller ändra utdata för funktionen.

#### Använd beroendeersättning

Detta är ett bra första alternativ när det faktiskt skulle uppnå det önskade målet, förutsatt att inget för komplext måste göras för att implementera.

#### Nackdelar

Inte många. Den är inte användbar i alla situationer. Den största nackdelen är att du måste utöka den ursprungliga klassen som innehåller de funktioner du vill ändra. Det strider mot principen om&quot;Komposition över arv&quot;.
