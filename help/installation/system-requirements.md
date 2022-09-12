---
title: Systemkrav
description: Använd den här referensen för att identifiera nödvändiga programvaruberoenden som har testats med Adobe Commerce och Magento Open Source.
source-git-commit: f6f438b17478505536351fa20a051d355f5b157a
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---


# Systemkrav

I den här tabellen visas versioner av tredjepartsprogramvaruberoenden som Adobe har testat med specifika versioner av Adobe Commerce och Magento Open Source. Adobe stöder endast den kombination av systemkrav som beskrivs i följande tabell.

Exempelvis testas 2.4.3 fullständigt med MariaDB 10.4. Adobe rekommenderar att du uppgraderar till MariaDB 10.4 innan du uppgraderar till 2.4.3.

{{$include /help/_includes/system-requirements-table.md}}

## Diverse

I det här avsnittet beskrivs stöd och kompatibilitet för alla andra typer av obligatoriska och valfria program.

>[!NOTE]
>
>Följande krav gäller den senaste 2.4.x-korrigeringsversionen av Adobe Commerce och Magento Open Source.

### E-postserver

MTA (Mail Transfer Agent) eller SMTP-server

### Operativsystem (Linux x86-64)

Linux-distributioner, till exempel RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian och liknande. Microsoft Windows och macOS stöds inte.

### PHP-tillägg

>[!NOTE]
>
>The [Installationsanvisningar för PHP](prerequisites/php-settings.md) innehåller ett steg för att installera dessa tillägg.

{{$include /help/_includes/php-extensions.md}}

Se [officiell PHP-dokumentation](https://php.net/manual/en/extensions.php) för installationsinformation.

### PHP OPcache

Vi rekommenderar att du kontrollerar att [PHP OPcache](https://php.net/manual/en/intro.opcache.php) har aktiverats av prestandaskäl. OPcache är aktiverat i många PHP-distributioner. Om du vill verifiera om det är installerat kan du läsa [PHP-dokumentation](prerequisites/php-settings.md).

Om du måste installera det separat, se [PHP OPcache-dokumentation](https://php.net/manual/en/opcache.setup.php).

### PHP-inställningar

Vi rekommenderar speciella PHP-konfigurationsinställningar, t.ex. `memory_limit`som kan undvika vanliga problem när du använder Adobe Commerce och Magento Open Source.

Mer information finns i [Nödvändiga PHP-inställningar](prerequisites/php-settings.md).

### PHPUnit

PHPUnit (som kommandoradsverktyg) 9.0.0

### RAM

Uppgradering av program och tillägg från Commerce Marketplace och andra källor kan kräva upp till 2 GB RAM. Om du använder ett system med mindre än 2 GB RAM rekommenderar vi att du skapar en [växlingsfil](https://support.magento.com/hc/en-us/articles/360032980432); annars kan uppgraderingen misslyckas.

### Systemberoenden

Adobe Commerce och Magento Open Source kräver följande systemverktyg för vissa åtgärder:

- [bash](https://www.gnu.org/software/bash/)
- [gzip](https://www.gzip.org/)
- [lsof](https://linux.die.net/man/8/lsof)
- [mysql](https://www.mysql.com/)
- [mysqldump](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)
- [trevlig](https://linux.die.net/man/1/nice)
- [php](https://www.php.net/)
- [används](https://www.gnu.org/software/sed/manual/sed.html)
- [tar](https://linux.die.net/man/1/tar)

### SSL

- Ett giltigt [säkerhetscertifikat](https://glossary.magento.com/security-certificate) krävs för HTTPS.
- Självsignerade SSL-certifikat stöds inte.
- TLS-krav (Transport Layer Security) - PayPal och `repo.magento.com` båda kräver TLS 1.2 eller senare.

### Webbläsare som stöds

Storefront och Admin:

- Microsoft Edge (senaste och föregående större version)
- Firefox (senaste och tidigare större version; valfritt operativsystem)
- Chrome (senaste och tidigare större version) valfritt operativsystem)
- Safari (senaste och tidigare större version); endast macOS)
- Safari Mobile för iPad 2, iPad Mini, iPad med Retina-skärm (iOS 12 eller senare) för datorbutiker
- Safari Mobile för iPhone 6 eller senare; iOS 12 eller senare, för mobilbutiker
- Chrome for mobile (latest and previous major version [Android 4 eller senare] för mobilbutiker)

### Xdebug

[php_xdebug 2.5.x](https://xdebug.org/download) eller senare (endast utvecklingsmiljöer), kan ha en negativ effekt på prestandan)

>[!NOTE]
>
>Det finns ett känt problem med `xdebug` som kan påverka installationer av Adobe Commerce eller Magento Open Source eller få tillgång till butiken eller administratören efter installationen. Mer information finns i [Känt problem med xdebug](https://support.magento.com/hc/en-us/articles/360034242212).
