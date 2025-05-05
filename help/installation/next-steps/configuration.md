---
title: Konfigurera programmet
description: Lär dig mer om den konfiguration efter installation som krävs för Adobe Commerce lokala distributioner.
feature: Install, Configuration
exl-id: b1808664-10ec-4147-8251-a99f8b58f4be
source-git-commit: a28dad04dac23075234a6ac3c2b362d125c9d981
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Konfigurera programmet

Nu när du har installerat Adobe Commerce måste du konfigurera det. I det här avsnittet finns några rekommenderade konfigurationsinställningar.

## Konfigurera cron

UNIX-uppgiftsschemaläggaren, cron, är viktig för programmets dagliga åtgärder. Det schemalägger saker som omindexering, nyhetsbrev, e-post och webbplatskartor. En *crontab* är en cron-konfiguration.

Du måste installera Adobe Commerce-tjänster på *crontab*, annars fungerar inte vissa kärnfunktioner (och vissa tillägg från tredje part) korrekt.

Mer information om cron, inklusive hur du tar bort en crontab och kör cron från kommandoraden, finns i [Konfigurera och kör cron](../../configuration/cli/configure-cron-jobs.md).

## Säkerhetsinställningar och rekommendationer

Efter installationen rekommenderar vi följande:

* Se till att filägarskap och behörigheter är korrekt inställda
* Vi rekommenderar starkt att [ändrar standardadministratörs-URI](../tutorials/admin-uri.md) från `admin` till något annat
* Kontrollera att [`X-Frame-Option` HTTP-huvudet ](../../configuration/security/xframe-options.md) är korrekt inställt.
* Vidta försiktighetsåtgärder mot serveröverskridande skriptning (XSS) genom att [skydda dina mallar](https://developer.adobe.com/commerce/php/development/security/cross-site-scripting/)

Om du har installerat genom att [klona GitHub-databasen](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) kontrollerar du att du bara inkluderar de filer och mappar som krävs för produktionsmiljön när du distribuerar programmet. Filer och mappar som inte behövs kan medföra säkerhetsrisker.

## Aktivera omskrivning av Apache-servern

Om du använder webbservern Apache måste du aktivera serveromskrivningar för att sidorna ska visas korrekt. I annat fall visas sidor utan format och andra problem.

[Avsnitt om omskrivning av Apache-servern](../prerequisites/web-server/apache.md#apache-rewrites-and-htaccess)

## Cachelagring i en miljö med flera webnoder

Om du har flera webbnoder kan du *inte* använda programmets standardfilcachning eftersom det inte finns någon synkronisering mellan webbnoder. Aktiviteten på en webbnod skrivs med andra ord endast till den webbnodens filsystem. Efterföljande aktivitet, om den utförs på en annan webbnod, kan resultera i att onödiga filer skrivs eller att fel kan uppstå.

Använd i stället [Redis](../../configuration/cache/config-redis.md) som både standardcache och sidcache.

## Serverinställningar

I det här avsnittet beskrivs kortfattat inställningar som vi rekommenderar att du tar hänsyn till för servern som programmet körs på. Vissa av dessa inställningar är inte direkt relaterade till programmet. De visas endast som förslag.

### Loggrotation

Med UNIX-verktyget `logrotate` kan du administrera system som genererar ett stort antal loggfiler. Det möjliggör automatisk rotation, komprimering, borttagning och utskick av loggfiler. Varje loggfil kan hanteras varje dag, varje vecka, varje månad eller när loggfilen överskrider en angiven storlek.

Mer information finns i följande:

* [HowTo: The ultimate log rotate command tutorial with ten ten examples](https://www.thegeekstuff.com/2010/07/logrotate-examples)
* [Stackutbyte](https://unix.stackexchange.com/questions/85662/how-to-properly-automatically-manually-rotate-log-files-for-production-rails-app)
* [`logrotate` huvudsida ](https://linuxconfig.org/logrotate-8-manual-page)

>[!AVAILABILITY]
>
>Följande tillgänglighetsinformation gäller för Adobe Commerce i projekt för molninfrastruktur:
>
>* Startmiljöer har ingen loggrotation.
>
>* Du kan inte konfigurera loggrotation i Pro Integration-miljöer. Du måste implementera en anpassad lösning/skript och [konfigurera ditt cron](https://experienceleague.adobe.com/sv/docs/commerce-on-cloud/user-guide/configure/app/properties/crons-property) så att skriptet körs efter behov.

### Ställ in iptables-regler för att möjliggöra för olika tjänster att kommunicera

Oavsett om du har en server eller många måste du öppna portar i brandväggen för att kunna kommunicera med tjänster. Om du till exempel använder sökmotorn Solr med Adobe Commerce måste du aktivera den för att kommunicera med webbservern. Om du har flera webbnoder måste du aktivera dem för att kunna kommunicera med varandra.

Mer information:

* Ubuntu: [Ubuntu-dokumentationssida](https://help.ubuntu.com/community/IptablesHowTo).
* CentOS: [CentOS How-to](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html).

### Förbättrade säkerhetsregler för Linux (SELinux)

Vi har ingen rekommendation om du ska använda SELinux, men om du använder det måste du konfigurera tjänster så att de kommunicerar med varandra på ungefär samma sätt som att konfigurera iptables.

Mer information:

* Ubuntu: [Debian-handbok](https://debian-handbook.info/browse/stable/sect.selinux.html)
* CentOS: [CentOS wiki](https://wiki.centos.org/HowTos/SELinux)

### Konfigurera en e-postserver

Adobe Commerce kräver en e-postserver. Vi rekommenderar inte en viss server, men du kan försöka med något av följande:

* Postfix för CentOS ([Självstudiekurs om digitala oceaner](https://www.digitalocean.com/community/tutorials/how-to-install-postfix-on-centos-6), [CentOS-dokumentation](https://www.centos.org))
* Postfix för Ubuntu ([Självstudiekurs om digitala oceaner](https://www.digitalocean.com/community/tutorials/how-to-install-and-setup-postfix-on-ubuntu-14-04), [Ubuntu-dokumentation](https://help.ubuntu.com/community/MailServer))

### Förfina sökmotorn för bättre prestanda:

Elasticsearch eller OpenSearch krävs för alla installationer från och med 2.4.0.

* [Installera och konfigurera sökmotorn](../../configuration/search/overview-search.md)

### Konfigurera en meddelandekö

Sedan version 2.3.0 har Adobe Commerce tagit med funktioner för meddelandekö. I tidigare versioner är den endast tillgänglig för Adobe Commerce.

* [[!DNL RabbitMQ]](../../configuration/queues/message-queue-framework.md)

## Endast inställningar för Adobe Commerce

Du kan bara konfigurera följande om du använder Adobe Commerce:

* [Dela databaser för utcheckning, orderhantering och andra databastabeller](../../configuration/storage/multi-master.md)
