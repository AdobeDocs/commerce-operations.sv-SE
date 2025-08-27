---
title: Systemkrav
description: Använd den här referensen för att identifiera nödvändiga programvaruberoenden som har testats med Adobe Commerce-utgåvor.
exl-id: 008c9edc-7d72-403c-847f-0e3b77bbb197
source-git-commit: 8ada5da7907325490cfe0953ec43db61899b152e
workflow-type: tm+mt
source-wordcount: '814'
ht-degree: 0%

---

# Systemkrav

Nedan sammanfattas programvaruberoenden och tjänster som testats för Adobe Commerce.

Det finns vissa skillnader i beroendena för Commerce i molnet. Tjänstversion och kompatibilitetsstöd för Adobe Commerce i molnet avgörs av tjänster som testas och distribueras till molnmiljöer, och skiljer sig ibland från versioner som stöds av Adobe Commerce lokala distributioner. Exempel: Elasticsearch 7.17 stöds för Commerce 2.4.4 för anläggningsdistributioner, men OpenSearch 1 stöds för 2.4.4 Adobe Commerce i molnet.

>[!NOTE]
>
>Systemkraven gäller endast för lanserade versioner av Adobe Commerce. Versioner för Beta eller tidig åtkomst ingår inte. Läs [versionsinformationen](../release/release-notes/overview.md) om du vill veta mer om de senaste versionerna av Adobe Commerce.

I följande tabeller visas versioner av tredjepartsprogramvaruberoenden som Adobe har testat med specifika Adobe Commerce-utgåvor.

Adobe stöder bara den kombination av systemkrav som beskrivs i följande tabeller. 2.4.5 har till exempel testats fullt ut med MariaDB 10.4. Adobe rekommenderar att du uppgraderar till MariaDB 10.4 innan du uppgraderar till 2.4.5.

Adobe rekommenderar att du uppgraderar RabbitMQ-versionerna stegvis för att säkerställa en smidig uppgraderingsprocess och förhindra driftsättningsfel. Om du till exempel uppgraderar från version 3.8 till 4.1 bör du först uppgradera från 3.8 till 3.9, från 3.9 till 3.10 och så vidare. Du bör uppgradera till version 4.1 först efter version 3.13.

>[!BEGINTABS]

>[!TAB Commerce i molnet]

[Commerce i molnmallen](https://github.com/magento/magento-cloud) innehåller en standardkonfiguration för tjänster som är kompatibla med en viss Commerce-version.

{{$include /help/_includes/templated/cloud-requirements-table.md}}

Tjänsterna och versionerna definieras i [filen `services.yaml`](https://github.com/magento/magento-cloud/blob/master/.magento/services.yaml). Följande är standardtjänstkonfigurationen för Commerce 2.4.6 i molninfrastrukturen:

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

Se [Konfigurera tjänster](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/service/services-yaml.html) i guiden _Commerce om molninfrastruktur_.

>[!TAB Commerce lokalt]

{{$include /help/_includes/templated/system-requirements-table.md}}

>[!ENDTABS]

## PHP-inställningar

Det finns särskilda PHP-konfigurationsinställningar, till exempel inställningen `memory_limit`, som kan hjälpa dig att undvika vanliga problem när du använder Adobe Commerce. Se [Nödvändiga PHP-inställningar](prerequisites/php-settings.md).

Mer information om molnkonfiguration finns i [PHP-inställningar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html) i guiden _Commerce om molninfrastruktur_.

### PHP OPcache

Du bör verifiera att [PHP OPcache](https://www.php.net/manual/en/intro.opcache.php) har aktiverats av prestandaskäl. OPcache är aktiverat i många PHP-distributioner. Tillägget `opcache` installeras som standard i Commerce i molninfrastrukturen.

Kontrollera att PHP OPcache är installerat och se [PHP-inställningar](prerequisites/php-settings.md) om du vill veta var du befinner dig. Mer information om prestandainställningar finns i programvarurekommendationerna för [PHP-inställningar](https://experienceleague.adobe.com/docs/commerce-operations/performance-best-practices/software.html#php-settings) i guiden _Bästa metoder för prestanda_.

Om du måste installera OPcache separat, se [dokumentationen för PHP OPcache](https://www.php.net/manual/en/opcache.setup.php).

### PHP-processkontroll

{{php-process-control}}

### PHPUnit

PHPUnit v9 (som kommandoradsverktyg).

### PHP-tillägg

Installationsanvisningarna för [PHP](prerequisites/php-settings.md) innehåller ett steg för att installera dessa tillägg.

>[!TIP]
>
>Information om PHP-tillägg i molninfrastrukturen finns i [Aktivera PHP-tillägg](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure/app/php-settings.html#enable-extensions) i guiden _Commerce om molninfrastruktur_.

>[!BEGINTABS]

>[!TAB Commerce i molnet]

Följande tabell visar vilka PHP-tillägg som stöds när du distribuerar Adobe Commerce på molnplattformen.

{{$include /help/_includes/templated/php-extensions-cloud.md}}

>[!TAB Commerce lokalt]

{{$include /help/_includes/templated/php-extensions.md}}

Mer installationsinformation finns i [den officiella PHP-dokumentationen](https://www.php.net/manual/en/extensions.php).

>[!ENDTABS]

## Diverse

I det här avsnittet beskrivs stöd och kompatibilitet för alla andra typer av obligatoriska och valfria program.

>[!NOTE]
>
>Följande krav gäller den senaste 2.4.x-korrigeringsversionen av Adobe Commerce. När det är relevant tillhandahålls vägledning om infrastrukturen i Commerce i molnet.

### Webbläsare

Storefront och Admin:

- Microsoft Edge (senaste och föregående större version)
- Firefox (senaste och föregående större version, alla operativsystem)
- Chrome (senaste och föregående större version, alla operativsystem)
- Safari (senaste och föregående större version; endast macOS)
- Safari för iOS (senaste och föregående större version, för storefront)
- Chrome för Android (senaste och föregående större version, för storefront)

### E-postserver

MTA (Mail Transfer Agent) eller SMTP-server. Commerce i molninfrastrukturen använder e-posttjänsten [SendGrid](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/project/sendgrid.html).

### Minne

Uppgradering av program och tillägg från Commerce Marketplace och andra källor kan kräva upp till 2 GB RAM. Om du använder ett system med mindre än 2 GB RAM skapar du en [utbytesfil](https://support.magento.com/hc/en-us/articles/360032980432). I annat fall kan uppgraderingen misslyckas.

### Operativsystem (Linux x86-64)

Linux-distributioner, till exempel RedHat Enterprise Linux (RHEL), CentOS, Ubuntu, Debian och liknande.

Microsoft Windows och macOS stöds **inte**.

Adobe Commerce kräver följande systemverktyg för vissa åtgärder:

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
- TLS-krav (Transport Layer Security) - PayPal och `repo.magento.com` kräver båda TLS 1.2 eller senare.

Information om Commerce molninfrastruktur finns i [Snabb konfiguration](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/cdn/setup-fastly/fastly-configuration.html) i guiden _Commerce om molninfrastruktur_.

### Xdebug

För Adobe Commerce använder du [php_xdebug 2.5.x](https://xdebug.org/download) eller senare (endast utvecklingsmiljöer; kan ha en negativ effekt på prestanda).

Information om Adobe Commerce i molnet finns i [Konfigurera Xdebug](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/test/debug.html) i guiden _Commerce om molninfrastruktur_.

>[!NOTE]
>
>Det finns ett känt fel med `xdebug` som kan påverka Adobe Commerce-installationer eller åtkomst till butiken eller administratören efter installationen. Se [Känt fel som påverkar `xdebug` installation](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/known-issues-that-affect-installation.html) i _Commerce Support Knowledge Base_.


<!-- Last updated from includes: 2025-08-26 16:56:07 -->
