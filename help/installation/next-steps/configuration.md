---
title: Konfigurera programmet
description: Lär dig mer om den konfiguration efter installation som krävs för Adobe Commerce och Magento Open Source lokala distributioner.
source-git-commit: 61638d373408d9a7c3c3a935eee61927acfac7a6
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---


# Konfigurera programmet

Nu när du har installerat Adobe Commerce eller Magento Open Source måste du konfigurera det. I det här avsnittet finns några rekommenderade konfigurationsinställningar.

## Konfigurera cron

UNIX-uppgiftsschemaläggaren, cron, är viktig för programmets dagliga åtgärder. Det schemalägger saker som omindexering, nyhetsbrev, e-post och webbplatskartor. A *crontab* är en cron-konfiguration.

Du måste installera tjänsterna Adobe Commerce och Magento Open Source i *crontab* eller vissa kärnfunktioner (och vissa tillägg från tredje part) fungerar inte korrekt.

Mer information om cron, inklusive hur du tar bort en crontab och kör cron från kommandoraden, finns i [Konfigurera och kör cron](../../configuration/cli/configure-cron-jobs.md).

## Säkerhetsinställningar och rekommendationer

Efter installationen rekommenderar vi följande:

* Se till att filägarskap och behörigheter är korrekt inställda
* Vi rekommenderar [ändra standardadministratörs-URI](../tutorials/admin-uri.md) från `admin` till något annat
* Se till att [`X-Frame-Option` HTTP-huvud](../../configuration/security/xframe-options.md) är korrekt inställd.
* Vidta försiktighetsåtgärder mot serveröverskridande skriptning (XSS) genom att [skydda dina mallar](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)

Om du installerat av [klona GitHub-databasen](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)ska du se till att du bara inkluderar de filer och mappar som behövs för produktionsmiljön när du distribuerar programmet. Filer och mappar som inte behövs kan medföra säkerhetsrisker.

## Aktivera omskrivning av Apache-servern

Om du använder webbservern Apache måste du aktivera serveromskrivningar för att sidorna ska visas korrekt. I annat fall visas sidor utan format och andra problem.

[Avsnitt om omskrivning av Apache-servern](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## Cachelagring i en miljö med flera webnoder

Om du har flera webbnoder *inte* använder programmets standardfilcachning eftersom det inte finns någon synkronisering mellan webbnoder. Aktiviteten på en webbnod skrivs med andra ord endast till den webbnodens filsystem. Efterföljande aktivitet, om den utförs på en annan webbnod, kan resultera i att onödiga filer skrivs eller att fel kan uppstå.

Använd i stället [Redis](../../configuration/cache/config-redis.md) för båda standardvärdena [cache](https://glossary.magento.com/cache) och sidcachen.

## Serverinställningar

I det här avsnittet beskrivs kortfattat inställningar som vi rekommenderar att du tar hänsyn till för servern som programmet körs på. Vissa av dessa inställningar är inte direkt relaterade till programmet. dessa ges endast som förslag.

### Loggrotation

UNIX `logrotate` kan du administrera system som genererar ett stort antal loggfiler. Det möjliggör automatisk rotation, komprimering, borttagning och utskick av loggfiler. Varje loggfil kan hanteras varje dag, varje vecka, varje månad eller när loggfilen överskrider en angiven storlek.

Mer information finns i följande:

* [Använda: Den ultimata självstudiekursen för att rotera logg med tio exempel](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [Stackutbyte](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate` huvudsida](https://linuxconfig.org/logrotate-8-manual-page)

### Ställ in iptables-regler för att göra det möjligt för olika tjänster att kommunicera

Oavsett om du har en server eller många måste du öppna portar i brandväggen för att kunna kommunicera med tjänster. Om du till exempel använder sökmotorn Solr med Adobe Commerce måste du aktivera den för att kommunicera med webbservern. Om du har flera webbnoder måste du aktivera dem för att kunna kommunicera med varandra.

Mer information:

* Ubuntu: [Dokumentationssida för Ubuntu](https://help.ubuntu.com/community/IptablesHowTo).
* CentOS: [CentOS How-to](https://wiki.centos.org/HowTos/Network/IPTables).

### Förbättrade säkerhetsregler för Linux (SELinux)

Vi har ingen rekommendation om du ska använda SELinux; Om du däremot använder den måste du konfigurera tjänster så att de kommunicerar med varandra på ungefär samma sätt som konfigurerar iptables.

Mer information:

* Ubuntu: [Debian-handbok](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS: [CentOS wiki](https://wiki.centos.org/HowTos/SELinux)

### Konfigurera en e-postserver

Adobe Commerce och Magento Open Source kräver en e-postserver. Vi rekommenderar inte en viss server, men du kan försöka med något av följande:

* Postfix för CentOS ([Digital Ocean, genomgång](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6), [CentOS-dokumentation](https://www.centos.org))
* Postfix för Ubuntu ([Digital Ocean, genomgång](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04), [Ubuntu-dokumentation](https://help.ubuntu.com/community/MailServer))

### Förfina sökmotorn för bättre prestanda:

Elasticsearch eller OpenSearch krävs för alla installationer från och med 2.4.0.

* [Installera och konfigurera sökmotorn](../../configuration/search/overview-search.md)

### Konfigurera en meddelandekö

Sedan version 2.3.0 innehåller Adobe Commerce och Magento Open Source funktioner för meddelandekö. I tidigare versioner är den endast tillgänglig för Adobe Commerce.

* [KaninMQ](../../configuration/queues/message-queue-framework.md)

## Endast inställningar för Adobe Commerce

Du kan bara konfigurera följande om du använder Adobe Commerce:

* [Dela databaser för utcheckning, orderhantering och andra databastabeller](../../configuration/storage/multi-master.md)
