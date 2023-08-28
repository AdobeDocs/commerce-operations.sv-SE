---
title: Bästa praxis för undantagshantering
description: Lär dig de rekommenderade metoderna för att logga undantag när du utvecklar Adobe Commerce-projekt.
feature: Best Practices
role: Developer
source-git-commit: 94d37b6a95cae93f465daf8eb96363a198833e27
workflow-type: tm+mt
source-wordcount: '571'
ht-degree: 0%

---


# Bästa praxis för undantagshantering

Om ett undantag inte skrivs till `exception.log` filen med undantagsmodellen som kontext, känns den inte igen och analyseras korrekt i New Relic eller annan monolog-kompatibel logglagring för PSR-3. Loggning av endast en del av undantaget (eller loggning av det till fel fil) leder till produktionsfel när undantag förbises.

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

Den här metoden sparar automatiskt `$e->getMessage` till loggmeddelandet och `$e` till kontexten, efter [PSR-3-kontextstandard](https://www.php-fig.org/psr/psr-3/#13-context). Detta görs i `\Magento\Framework\Logger\Monolog::addRecord`.

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

Nedgradera undantag genom att följa följande [PSR-3-kontextstandard](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->debug($e->getMessage(), ['exception' => $e]);
}
```

### ![korrigera](../../../assets/yes.svg) Loggning kommer alltid först

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

Logga meddelanden och hela undantagsspårningen genom att följa [PSR-3-kontextstandard](https://www.php-fig.org/psr/psr-3/#13-context).

```php
try {
    $this->productRepository->getById($sku);
} catch (Exception $e) {
    $this->logger->critical($e->getMessage(), ['exception' => $e, 'trace' => $e->getTrace()]);
}
```

## Felaktig undantagshantering

I följande exempel visas felaktig undantagshantering.

### ![felaktig](../../../assets/no.svg) Logga in före loggning

Logik före loggning kan leda till ett annat undantag eller ett allvarligt fel, som förhindrar att undantaget loggas och bör ersättas med [korrekt exempel](#correct-logging-always-comes-first).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    $this->alternativeProcedure();
    $this->logger->critical($e);
}
```

### ![felaktig](../../../assets/no.svg) Tom `catch`

Tom `catch` -block kan vara ett tecken på oavsiktlig ljudavstängning och bör ersättas med [korrekt exempel](#correct-mute-signals).

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

### ![felaktig](../../../assets/no.svg) Logga meddelanden och spåra till olika loggfiler

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

Åtgärda problemet genom att ersätta koden enligt de korrekta exemplen i [Skriv till undantagsloggen](#correct-write-to-the-exception-log) eller [Nedgraderingsundantag](#correct-downgrade-exceptions).

### ![felaktig](../../../assets/no.svg) Nedgradera undantag utan sammanhang

Undantaget nedgraderas till ett fel, vilket innebär att ett objekt inte kan skickas, utan bara en sträng, vilket innebär att `getMessage()`. Detta gör att spårningen försvinner och bör ersättas med de korrekta exemplen som visas i [Skriv till undantagsloggen](#correct-write-to-the-exception-log) eller [Nedgraderingsundantag](#correct-downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->error($e->getMessage());
}
```

### ![felaktig](../../../assets/no.svg) Logga endast meddelandet i undantagsloggen

I stället för att skicka objektet `$e`, endast `$e->getMessage()` har skickats. Detta gör att spårningen försvinner och bör ersättas med de korrekta exemplen som visas [Skriv till undantagsloggen](#correct-write-to-the-exception-log) eller [Nedgraderingsundantag](#correct-downgrade-exceptions).

```php
try {
    $this->productRepository->getById($sku);
} catch (\Exception $e) {
    $this->logger->critical($e->getMessage());
}
```

### ![felaktig](../../../assets/no.svg) Saknas `// phpcs:ignore Magento2.CodeAnalysis.EmptyBlock.DetectedCatch`

Utelämnar `phpcs:ignore` Detta utlöser en varning i PHPCS och bör inte skicka din CI. Detta bör ersättas med rätt exempel som visas i [Stäng av signaler](#correct-mute-signals).

```php
try {
    $this->productRepository->deleteById($sku);
} catch (NoSuchEntityException $e) {
    // Product already removed
}
```
