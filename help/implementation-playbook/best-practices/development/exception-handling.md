---
title: Bästa praxis för undantagshantering
description: Lär dig de rekommenderade metoderna för att logga undantag när du utvecklar Adobe Commerce-projekt.
feature: Best Practices
role: Developer
exl-id: e7ad685b-3eaf-485b-8ab1-702f2e7ab89e
source-git-commit: 4bf8dd5c5320cc9a34cfaa552ec5e91d517d3617
workflow-type: tm+mt
source-wordcount: '565'
ht-degree: 0%

---

# Bästa praxis för undantagshantering

Om ett undantag inte skrivs till filen `exception.log` med undantagsmodellen som kontext, känns det inte igen och analyseras korrekt i New Relic eller andra PSR-3 monolog-kompatibla logglager. Loggning av endast en del av undantaget (eller loggning av det till fel fil) leder till produktionsfel när undantag förbises.

## Korrigera undantagshantering

I följande checklista finns exempel som visar hur du hanterar undantag korrekt.

### ![korrigera](../../../assets/yes.svg) Skriv till undantagsloggen

Skriv till undantagsloggen med följande mönster, oavsett ytterligare åtgärder, såvida det inte finns någon tvingande anledning att inte göra det.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
}
```

Detta arbetssätt sparar automatiskt `$e->getMessage` i loggmeddelandet och objektet `$e` i kontexten, enligt [PSR-3-kontextstandarden](https://www.php-fig.org/psr/psr-3/#13-context). Detta görs i `\Magento\Framework\Logger\Monolog::addRecord`.

### ![korrigera](../../../assets/yes.svg) Stäng av signaler

Stäng av signaler genom att inte logga undantag som ingår i det avsedda operationsflödet. Ingen uppföljningsåtgärd krävs när undantaget påträffas, så det behöver inte loggas och analyseras när det inträffar. Lägg till en kommentar som anger orsaken till att signalerna hörs och att det är avsiktligt. Kombinera med `phpcs:ignore`.

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) { // phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch
    // Product already removed
}
```

### ![korrigera](../../../assets/yes.svg) Nedgraderingsundantag

Nedgradera undantag genom att följa [PSR-3-kontextstandarden](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->debug($e->getMessage(), ['exception' => $e]);
}
```

### ![korrekt](../../../assets/yes.svg) Loggning kommer alltid först

Loggning kommer alltid först i koden för att förhindra fall där ett annat undantag eller ett allvarligt fel inträffar innan loggen skrivs.

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e);
    $this->alternativeProcedure();
}
```

### ![korrigera](../../../assets/yes.svg) Loggmeddelanden och hela undantagsspårningen

Logga meddelanden och hela undantagsspårningen genom att följa [PSR-3-kontextstandarden](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e->getMessage(), ['exception' => $e, 'trace' => $e->getTrace()]);
}
```

## Felaktig undantagshantering

I följande exempel visas felaktig undantagshantering.

### ![felaktig](../../../assets/no.svg) Logic före loggning

Logik före loggning kan leda till ett annat undantag eller ett allvarligt fel, som förhindrar att undantaget loggas och bör ersättas med [korrekt exempel](#logging-always-comes-first).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    $this->alternativeProcedure();
    $this->logger->critical($e);
}
```

### ![inkorrekt](../../../assets/no.svg) Tom `catch`

Tomma `catch`-block kan vara ett tecken på oavsiktlig avstängning och bör ersättas med [korrekt exempel](#mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
}
```

### ![felaktig](../../../assets/no.svg) Dubbel lokalisering

Om det fångade lokaliserade undantaget inte är översatt än löser du problemet på den plats där undantaget kastas första gången.

```php
try {
    $this->productRepository->getById($sku);
} catch (LocalizedException $e) {
    throw new LocalizedException(__($e->getMessage()));
}
```

### ![felaktiga](../../../assets/no.svg) Logga meddelanden och spåra till olika loggfiler

Följande kod loggar stackspårningen felaktigt för ett undantag som en sträng till en loggfil.

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
    $this->logger->debug($e->getTraceAsString());
}
```

Den här metoden infogar radbrytningar i meddelandet, som inte är kompatibelt med PSR-3. Undantaget, inklusive stackspårning, måste vara en del av meddelandekontexten för att säkerställa att den sparas korrekt med meddelandet i New Relic eller annan PSR-3-monologgkompatibel logglagring.

Åtgärda problemet genom att ersätta koden enligt de korrekta exemplen i [Skriv till undantagsloggen](#write-to-the-exception-log) eller [Nedgradera undantag](#downgrade-exceptions).

### ![felaktigt](../../../assets/no.svg) Nedgradera undantag utan kontext

Undantaget nedgraderas till ett fel, som inte tillåter att ett objekt skickas, utan bara en sträng, alltså `getMessage()`. Detta gör att spårningen går förlorad och bör ersättas med rätt exempel som visas i [Skriv till undantagsloggen](#write-to-the-exception-log) eller [Nedgradera undantag](#downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
}
```

### ![felaktigt](../../../assets/no.svg) Logga endast meddelandet i undantagsloggen

I stället för att skicka objektet `$e` skickas bara `$e->getMessage()`. Detta gör att spårningen går förlorad och bör ersättas med de korrekta exemplen som visas i [Skriv till undantagsloggen](#write-to-the-exception-log) eller [Nedgraderingsundantag](#downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->critical($e->getMessage());
}
```

### ![felaktigt](../../../assets/no.svg) Saknas `// phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch`

Om du utelämnar raden `phpcs:ignore` utlöses en varning i PHPCS och din CI ska inte skickas. Detta bör ersättas med rätt exempel som visas i [ljudsignaler](#mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    // Product already removed
}
```
