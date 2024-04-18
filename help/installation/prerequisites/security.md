---
title: Lokal installationssäkerhet
description: Lär dig hur du kan förbättra säkerhetspositionen för din Adobe Commerce-installation lokalt.
feature: Install, Security
exl-id: 56724a72-c64d-44d4-a886-90d97ae5fb6d
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 0%

---

# Lokal installationssäkerhet

[Förbättrade säkerhetsfunktioner i Linux (SELinux)](https://selinuxproject.org/page/Main_Page) ger CentOS- och Ubuntu-administratörer bättre åtkomstkontroll över sina servrar. Om du använder SELinux *och* Apache måste initiera en anslutning till en annan värd. Du måste köra de kommandon som beskrivs i det här avsnittet.

>[!NOTE]
>
>Adobe har ingen rekommendation om SELinux; du kan använda det för ökad säkerhet om du vill. Om du använder SELinux måste du konfigurera det korrekt, annars kan Adobe Commerce fungera oförutsägbart. Om du väljer att använda SELinux bör du kontakta en resurs som [CentOS wiki](https://wiki.centos.org/HowTos/SELinux) för att skapa regler som möjliggör kommunikation.

## Förslag om installation med Apache

Om du väljer att aktivera SELinux kan det uppstå problem när du kör installationsprogrammet, såvida du inte ändrar *säkerhetskontext* av vissa kataloger enligt följande:

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/app/etc
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/var
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/media
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/pub/static
```

```bash
chcon -R --type httpd_sys_rw_content_t <magento_root>/generated
```

Föregående kommandon fungerar bara med webbservern Apache. På grund av olika konfigurationer och säkerhetskrav garanterar vi inte att dessa kommandon fungerar i alla situationer. Mer information finns i:

* [huvudsida](https://linux.die.net/man/8/httpd_selinux)
* [Server-Lab](https://www.serverlab.ca/tutorials/linux/web-servers-linux/configuring-selinux-policies-for-apache-web-servers/)

## Aktivera kommunikation mellan servrar

Om Apache och databasservern finns på samma värd använder du följande kommando om du tänker använda integreringar som använder `curl` (ex. Paypal och USPS).
Så här aktiverar du Apache för att initiera en anslutning till en annan värd med SELinux aktiverat:

1. Använd följande kommando för att avgöra om SELinux är aktiverat:

   ```bash
   getenforce
   ```

   `Enforcing` visas för att bekräfta att SELinux körs.

   * CentOS: `setsebool -P httpd_can_network_connect=1`
   * Ubuntu: `setsebool -P apache2_can_network_connect=1`

## Öppnar portar i brandväggen

Beroende på dina säkerhetskrav kan du behöva öppna port 80 och andra portar i brandväggen. På grund av den känsliga nätverkssäkerheten rekommenderar Adobe starkt att du rådfrågar IT-avdelningen innan du fortsätter. Nedan följer några förslag på referenser:

* Ubuntu: [Dokumentationssida för Ubuntu](https://help.ubuntu.com/community/IptablesHowTo)
* CentOS: [CentOS How-to](https://wiki.centos.org/HowTos%282f%29Network%282f%29IPTables.html).
