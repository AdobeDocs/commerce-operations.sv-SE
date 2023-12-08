---
title: Systemkrav
description: Använd den här referensen för att identifiera nödvändiga programvaruberoenden som har testats med Adobe Commerce och Magento Open Source.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 8b9e4de2799532e4654fce63d856c2d301025f09
workflow-type: tm+mt
source-wordcount: '788'
ht-degree: 0%

---

# Systemkrav

Nedan sammanfattas programvaruberoenden och tjänster som testats för Adobe Commerce och Magento Open Source.

Det finns vissa skillnader i beroendena för Commerce på molninfrastrukturen. Tjänstversion och kompatibilitetsstöd för Adobe Commerce i molninfrastruktur bestäms av tjänster som testas och distribueras i molnmiljöer, och skiljer sig ibland från versioner som stöds av Adobe Commerce lokala distributioner. Elasticsearch 7.17 stöds till exempel för Commerce 2.4.4 för anläggningsdistributioner, men OpenSearch 1.2 stöds för Commerce 2.4.4 i molninfrastruktur.

I följande tabeller visas versioner av tredjepartsprogramvaruberoenden som Adobe har testat med specifika utgåvor av Adobe Commerce och Magento Open Source.

Adobe stöder endast den kombination av systemkrav som beskrivs i följande tabeller. 2.4.5 har till exempel testats fullt ut med MariaDB 10.4. Adobe rekommenderar att du uppgraderar till MariaDB 10.4 innan du uppgraderar till 2.4.5.

>[!BEGINTABS]

>[!TAB Commerce on Cloud]

The [Commerce on Cloud-mall](https://github.com/magento/magento-cloud) innehåller en standardkonfiguration för tjänster som är kompatibla med en viss Commerce-version.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

Tjänsterna och versionerna definieras i [den `services.yaml` fil](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml). Följande är standardtjänstkonfigurationen för Commerce 2.4.6 i molninfrastruktur:

```yaml
mysql:
    type: mysql:10.6
    disk: 5120

redis:
    type: redis:7.0

opensearch:
    type: opensearch:2
    disk: 1024
```

Se [Konfigurera tjänster](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) i _Commerce on Cloud Infrastructure_ guide.

>[!TAB Lokal handel]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## PHP-inställningar

Det finns särskilda PHP-konfigurationsinställningar, till exempel `memory_limit` inställning, vilket kan hjälpa dig att undvika vanliga problem när du använder Adobe Commerce och Magento Open Source. Se [Nödvändiga PHP-inställningar](prerequisites/php-settings.md).

Mer information om konfigurering av molnet finns i [PHP-inställningar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html) i _Commerce on Cloud Infrastructure_ guide.

### PHP OPcache

Du bör verifiera att [PHP OPcache](https://www.php.net/manual/en/intro.opcache.php) har aktiverats av prestandaskäl. OPcache är aktiverat i många PHP-distributioner. The `opcache` tillägg installeras som standard i Commerce on Cloud-infrastrukturen.

Kontrollera att PHP-cachen är installerad om du vill se en premesis. Mer information finns i [PHP-inställningar](prerequisites/php-settings.md). Du kan även få specifik vägledning om prestandainställningar i programvarurekommendationerna för [PHP-inställningar](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html#php-settings) i _Bästa praxis för prestanda_ guide.

Om du måste installera OPcache separat, se [PHP OPcache-dokumentation](https://www.php.net/manual/en/opcache.setup.php).

### PHP-processkontroll

{{php-process-control}}

### PHPUnit

PHPUnit (som kommandoradsverktyg) 9.0.0

### PHP-tillägg

The [Installationsanvisningar för PHP](prerequisites/php-settings.md) innehåller ett steg för att installera dessa tillägg.

>[!TIP]
>
>PHP-tillägg i molninfrastrukturen finns på [Aktivera PHP-tillägg](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html#enable-extensions) i _Commerce on Cloud Infrastructure_ guide.

>[!BEGINTABS]

>[!TAB Commerce on Cloud]

Följande tabell visar vilka PHP-tillägg som stöds när du distribuerar Adobe Commerce på molnplattformen.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Lokal handel]

{{$include /help/_includes/templated/php-extensions.md}}

Se [officiell PHP-dokumentation](https://www.php.net/manual/en/extensions.php) för installationsinformation.

>[!ENDTABS]

## Diverse

I det här avsnittet beskrivs stöd och kompatibilitet för alla andra typer av obligatoriska och valfria program.

>[!NOTE]
>
>Följande krav gäller den senaste 2.4.x-korrigeringsversionen av Adobe Commerce och Magento Open Source. I tillämpliga fall ges vägledning om infrastruktur i Commerce on Cloud.

### Webbläsare

Storefront och Admin:

- Microsoft Edge (senaste och föregående större version)
- Firefox (senaste och föregående större version, alla operativsystem)
- Krom (senaste och föregående större version, alla operativsystem)
- Safari (senaste och föregående större version; endast macOS)
- Safari Mobile för iPad 2, iPad Mini, iPad med Retina-skärm (iOS 12 eller senare) för datorbutiker
- Safari Mobile för iPhone 6 eller senare; iOS 12 eller senare, för mobilbutiker
- Chrome for mobile (latest and previous major version [Android™ 4 eller senare] för mobilbutiker)

### E-postserver

MTA (Mail Transfer Agent) eller SMTP-server. Commerce on Cloud-infrastrukturen använder [SkickaGrid-e-posttjänst](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html).

### Minne

Uppgradering av program och tillägg från Commerce Marketplace och andra källor kan kräva upp till 2 GB RAM-minne. Om du använder ett system med mindre än 2 GB RAM skapar du en [växlingsfil](https://support.magento.com/hc/en-us/articles/360032980432); annars kan uppgraderingen misslyckas.

### Operativsystem (Linux x86-64)

Linux-distributioner, till exempel RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian och liknande. Microsoft Windows och macOS stöds inte.

Adobe Commerce och Magento Open Source kräver följande systemverktyg för vissa åtgärder:

- [[!DNL bash]](https://www.gnu.org/software/bash/)
- [[!DNL gzip]](https://www.gzip.org/)
- [[!DNL lsof]](https://linux.die.net/man/8/lsof)
- [[!DNL mysql]](https://www.mysql.com/)
- [[!DNL mysqldump]](https://dev.mysql.com/doc/refman/8.0/en/mysqldump.html)
- [[!DNL nice]](https://linux.die.net/man/1/nice)
- [[!DNL php]](https://www.php.net/)
- [[!DNL sed]](https://www.gnu.org/software/sed/manual/sed.html)
- [[!DNL tar]](https://linux.die.net/man/1/tar)

### SSL

- Ett giltigt säkerhetscertifikat krävs för HTTPS.
- Självsignerade SSL-certifikat stöds inte.
- TLS-krav (Transport Layer Security) - PayPal och `repo.magento.com` båda kräver TLS 1.2 eller senare.

Information om Commerce on Cloud-infrastruktur finns på [Snabb konfiguration](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) i _Commerce on Cloud Infrastructure_ guide.

### Xdebug

För Adobe Commerce och Magento Open Source använder du [php_xdebug 2.5.x](https://xdebug.org/download) eller senare (endast utvecklingsmiljöer; kan ha en negativ effekt på prestandan).

Information om Adobe Commerce i molnet finns på [Konfigurera Xdebug](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html) i _Commerce on Cloud Infrastructure_ guide.

>[!NOTE]
>
>Det finns ett känt problem med `xdebug` som kan påverka installationer av Adobe Commerce eller Magento Open Source eller få tillgång till butiken eller administratören efter installationen. Se [Känt fel som påverkar `xdebug` installation](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html) i _Knowledge Base för Commerce Support_.
