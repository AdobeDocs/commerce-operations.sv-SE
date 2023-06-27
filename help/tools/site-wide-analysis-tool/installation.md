---
title: Installationshandbok
description: Använd den här guiden för att installera [!DNL Site-Wide Analysis Tool] för din webbplats
exl-id: ba36dc74-806d-49c5-b4d1-ba53ed4076fb
feature: Configuration, Install
source-git-commit: e83e2359377f03506178c28f8b30993c172282c7
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Installationshandbok

The [!DNL Site-Wide Analysis Tool] tillhandahåller prestandaövervakning, rapporter och rekommendationer i realtid dygnet runt, alla dagar för att säkerställa Adobe Commerce säkerhet och driftsäkerhet vid installation av molninfrastruktur. Här finns också detaljerad information om tillgängliga och installerade korrigeringsfiler, tillägg från tredje part och din Adobe Commerce-installation.

>[!INFO]
>
>Lär dig [aktivera](../site-wide-analysis-tool/access.md) den [!DNL Site-Wide Analysis Tool] och generera rapporter.

Om du har en lokal installation av Adobe Commerce installerar du en agent på din infrastruktur för att använda verktyget. Du behöver inte installera agenten på Adobe Commerce i molninfrastrukturprojekt.

## Agent

The [!DNL Site-Wide Analysis Tool] Agenten låter dig använda [!DNL Site-Wide Analysis Tool] för lokala installationer av Adobe Commerce.

The [!DNL Site-Wide Analysis Tool] Agenten samlar in program- och affärsdata, analyserar dem och ger ytterligare insikter om hur bra din installation är, så att du kan förbättra kundupplevelsen. Den övervakar ditt program och hjälper dig att identifiera problem med prestanda, säkerhet, tillgänglighet och program.

Följande steg krävs för att installera agenten:

1. Kontrollera systemkraven.

1. Konfigurera API-nycklar i [!UICONTROL Commerce Services Connector] tillägg.

1. Installera agenten.

1. Kör agenten.

>[!INFO]
>
>Agenten stöder Adobe Commerce-installationer med flera noder. Installera och konfigurera agenten på varje nod.

## Systemkrav

Din lokala infrastruktur måste uppfylla följande krav innan du installerar agenten:

- Operativsystem

   - [!DNL Linux x86-64] distributioner, som [!DNL Red Hat® Enterprise Linux (RHEL)], [!DNL CentOS], [!DNL Ubuntu], [!DNL Debian]och liknande

  >[!IMPORTANT]
  >
  >Adobe Commerce stöds inte på [!DNL Microsoft Windows] eller [!DNL macOS].

- Adobe Commerce 2.4.1 eller senare

- [!DNL Commerce Services Connector extension]

- PHP CLI

- Bash/shell-verktyg

   - `php`

   - `wget`

   - `awk`

   - `nice`

   - `grep`

   - `openssl`

## [!DNL Commerce Services Connector]

Agenten kräver [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) tillägg som ska installeras på datorn och [konfigurerad](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) med API-nycklar. Kontrollera att tillägget är installerat genom att köra följande kommando:

```bash
bin/magento module:status Magento_ServicesId
```

Om du har installerat tillägget och konfigurerat det med en befintlig API-nyckel för en annan tjänst, **API-nyckeln MÅSTE genereras om** och uppdatera den i Adobe Commerce Admin för agenten.

1. Lägg in webbsajten i [underhållsläge](../../installation/tutorials/maintenance-mode.md).

1. Logga in [account.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671).

   >[!NOTE]
   >
   > Om du har problem med att komma åt ditt konto kan du läsa [Det går inte att logga in på Adobe Commerce support eller molnkonto](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html) för felsökningshjälp.

1. Klicka **[!UICONTROL API Portal]**.

1. Klicka **[!UICONTROL Delete]** bredvid den befintliga API-nyckeln.

1. [Konfigurera](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) en ny API-nyckel.

>[!IMPORTANT]
>
> Om du genererar nya nycklar i API-portalen ska du omedelbart uppdatera API-nycklarna i [!DNL Admin configuration]. Om du genererar nya nycklar och inte uppdaterar nycklarna i [!DNL Admin]kommer SaaS-tilläggen inte längre att fungera och du kommer att förlora värdefulla data.

Om tillägget inte är installerat installerar du det enligt följande:

1. Lägg till tillägget i `composer.json` och installera det.

   ```bash
   composer require magento/services-id
   ```

1. Aktivera tillägget.

   ```bash
   bin/magento module:enable Magento_ServicesId
   ```

1. Uppdatera databasschemat.

   ```bash
   bin/magento setup:upgrade
   ```

1. Rensa cachen.

   ```bash
   bin/magento cache:clean
   ```

1. [Konfigurera API-nycklar](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) för att ansluta tillägget till systemet.

## Installera agenten

Vi har skapat en [gränssnittsskript](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) för att förenkla installationen. Vi rekommenderar att du använder gränssnittsskriptet, men du kan följa [manuell installation](#manual) metod om det behövs.

>[!INFO]
>
>När agenten har installerats uppdateras den automatiskt när en ny version är tillgänglig.

### Skript

1. Hämta och kör gränssnittsskriptet.

   ```bash
   bash -c "$(wget -qO - https://raw.githubusercontent.com/magento-swat/install-agent-helpers/main/install.sh)"
   ```

   >[!TIP]
   >
   >Vi rekommenderar att du installerar agenten utanför Adobe Commerce rotprojektkatalog.

1. Verifiera installationen.

   ```bash
   ./scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. När du har hämtat och installerat agenten [konfigurera det att köras](#run-the-agent) med någon av följande metoder:

   - [Tjänst](#service) (helst om du har rotåtkomst)

   - [Cron](#cron)

### Manuell {#manual}

Om du inte vill använda våra [gränssnittsskript](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) Om du vill installera agenten måste du installera den manuellt genom att följa dessa steg:

1. Skapa en katalog där du vill hämta agenten.

   >[!TIP]
   >
   >Vi rekommenderar att du installerar agenten utanför Adobe Commerce rotprojektkatalog.

1. Ladda ned den binära filen och packa upp den.

   >[!INFO]
   >
   >Så här använder du [!DNL Site-Wide Analysis Tool]måste du först läsa och godkänna de användarvillkor som visas när du öppnar instrumentpanelen från Adobe Commerce Admin.

   För **AMD64** arkitektur:

   1. Ladda ned startarkivet.

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. Packa upp startarkivet.

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```

   För **ARM64** arkitektur:

   1. Ladda ned startarkivet.

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. Packa upp startarkivet.

      ```bash
      tar -xf launcher.linux-arm64.tar.gz
      ```

1. *(Valfritt)* Kontrollera signaturen för kontrollsummefilen.

   ```bash
   echo -n "LS0tLS1CRUdJTiBQVUJMSUMgS0VZLS0tLS0KTUlJQ0lqQU5CZ2txaGtpRzl3MEJBUUVGQUFPQ0FnOEFNSUlDQ2dLQ0FnRUE0M2FBTk1WRXR3eEZBdTd4TE91dQpacG5FTk9pV3Y2aXpLS29HendGRitMTzZXNEpOR3lRS1Jha0MxTXRsU283VnFPWnhUbHZSSFhQZWt6TG5vSHVHCmdmNEZKa3RPUEE2S3d6cjF4WFZ3RVg4MEFYU1JNYTFadzdyOThhenh0ZHdURVh3bU9GUXdDcjYramFOM3ErbUoKbkRlUWYzMThsclk0NVJxWHV1R294QzBhbWVoakRnTGxJUSs1d1kxR1NtRGRiaDFJOWZqMENVNkNzaFpsOXFtdgorelhjWGh4dlhmTUU4MUZsVUN1elRydHJFb1Bsc3dtVHN3ODNVY1lGNTFUak8zWWVlRno3RFRhRUhMUVVhUlBKClJtVzdxWE9kTGdRdGxIV0t3V2ppMFlrM0d0Ylc3NVBMQ2pGdEQzNytkVDFpTEtzYjFyR0VUYm42V3I0Nno4Z24KY1Q4cVFhS3pYRThoWjJPSDhSWjN1aFVpRHhZQUszdmdsYXJSdUFacmVYMVE2ZHdwYW9ZcERKa29XOXNjNXlkWApBTkJsYnBjVXhiYkpaWThLS0lRSURnTFdOckw3SVNxK2FnYlRXektFZEl0Ni9EZm1YUnJlUmlMbDlQMldvOFRyCnFxaHNHRlZoRHZlMFN6MjYyOU55amgwelloSmRUWXRpdldxbGl6VTdWbXBob1NrVnNqTGtwQXBiUUNtVm9vNkgKakJmdU1sY1JPeWI4TXJCMXZTNDJRU1MrNktkMytwR3JyVnh0akNWaWwyekhSSTRMRGwrVzUwR1B6LzFkeEw2TgprZktZWjVhNUdCZm00aUNlaWVNa3lBT2lKTkxNa1cvcTdwM200ejdUQjJnbWtldm1aU3Z5MnVMNGJLYlRoYXRlCm9sdlpFd253WWRxaktkcVkrOVM1UlNVQ0F3RUFBUT09Ci0tLS0tRU5EIFBVQkxJQyBLRVktLS0tLQ==" | base64 -d > release.pub
   ```

   ```bash
   openssl dgst -sha256 -verify release.pub -signature launcher.sha256 launcher.checksum
   ```

1. *(Valfritt)* Kontrollera kontrollsumman.

   ```bash
   shasum -a 512 -c launcher.checksum
   ```

1. Skapa `config.yaml` med följande innehåll.

   ```yaml
   project:
     appname: "Acme Inc" # Company or site name that you provided when installing the agent
   application:
     phppath: php # Path to your PHP CLI interpreter (usually /usr/bin/php)
     magentopath: /var/www/html/example.com # Root directory where your Adobe Commerce application is installed (usually /var/www/html)
     checkregistrypath: /path/to/swat-agent/tmp # Temporary directory for the agent (usually /usr/local/swat-agent/tmp)
     issandbox: false # Enabling sandbox mode to use the agent on staging environment (true or false)
     database:
       user: your-adobe-commerce-db-username # Database user for your Adobe Commerce installation
       password: your-password # Database password for the specified user for your Adobe Commerce installation
       host: 127.0.0.1 # Database host for your Adobe Commerce installation
       dbname: your-adobe-commerce-db-name # Database name for your Adobe Commerce installation
       port: 3306 # Database port for your Adobe Commerce installation (usually 3306)
       tableprefix: # Table Prefix for your Adobe Commerce installation (default value: empty)
    enableautoupgrade: true # Enables automatic upgrade (restart required after an upgrade; agent does not check for upgrades if the option is disabled; true or false)
    runchecksonstart: true # Collect data on the first run (Usually 1)
    loglevel: error # Determines what events are logged based on severity (usually error)
   ```

1. Kontrollera installationen.

   ```bash
   scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. När du har hämtat och installerat agenten måste du [konfigurera det att köras](#run-the-agent) med någon av följande metoder:

   - [Tjänst](#service) (helst om du har rotåtkomst)

   - [Cron](#cron)

## Kör agenten {#run-the-agent}

Vi rekommenderar att du konfigurerar agenten så att den körs som en tjänst. Om du har begränsad åtkomst till din infrastruktur och inte har rotbehörigheter måste du använda [cron](#cron) i stället.

### Tjänst {#service}

1. Skapa en systemenhetsfil `(/etc/systemd/system/scheduler.service)` med följande konfiguration (ersätt `<filesystemowner>` med den UNIX®-användare som äger katalogen där agenten och Adobe Commerce är installerade). Om du hämtade agenten som rotanvändare ändrar du ägare av katalogen och de kapslade filerna.

   ```config
   [Unit]
   Wants=network.target
   After=network.target
   
   [Service]
   Type=simple
   User=<filesystemowner>
   ExecStart=/path/to/agent/scheduler
   Restart=always
   RestartSec=3
   
   [Install]
   WantedBy=multi-user.target
   ```

1. Starta tjänsten.

   ```bash
   systemctl daemon-reload
   ```

   ```bash
   systemctl start scheduler
   ```

   ```bash
   systemctl enable scheduler
   ```

1. Verifiera att tjänsten körs.

   ```bash
   journalctl -u scheduler | grep "Application is going to update" | tail -1 && echo "Agent is successfully installed"
   ```

### Cron {#cron}

Om du inte har rotbehörighet eller inte har behörighet att konfigurera en tjänst som rot kan du använda cron i stället.

Uppdatera ditt kundschema:

```bash
( crontab -l ; echo "* * * * * flock -n /tmp/swat-agent.lockfile -c '/path/to/agent/scheduler' >> /path/to/agent/errors.log 2>&1" ) | sort - | uniq - | crontab -
```

## Avinstallera

Kör följande kommandon för att avinstallera tjänsten från datorn och ta bort alla genererade filer:

1. Stoppa schemaläggaren.

   ```bash
   systemctl stop scheduler
   ```

1. Inaktivera schemaläggaren.

   ```bash
   systemctl disable scheduler
   ```

1. Ta bort schemaläggningstjänstens `systemd` enhetsfil.

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. Läs in `systemd` hanterarkonfiguration.

   ```bash
   systemctl daemon-reload
   ```

1. Återställ alla `systemd` enheter från ett felaktigt tillstånd.

   ```bash
   systemctl reset-failed
   ```

1. Ta bort tjänstkatalogen för schemaläggaren.

   ```bash
   rm -rf <CHECK_REGISTRY_PATH> #see SWAT_AGENT_APPLICATION_CHECK_REGISTRY_PATH in /etc/systemd/system/scheduler.service
   ```

1. Ta bort den binära filen för schemaläggare.

   ```bash
   rm /usr/local/bin/scheduler
   ```

Om du konfigurerade agenten att köras med cron i stället, ska du göra följande:

1. Ta bort agenten från crontab-listan.

   ```bash
   crontab -e
   ```

1. Stoppa det pågående jobbet.

   ```bash
   ps aux | grep scheduler
   ```

1. Ta bort katalogen där du installerade agenten.

   ```bash
   rm -rf swat-agent
   ```

## Felsökning

### Åtkomstnycklar har inte tolkats korrekt

Följande fel kan uppstå om dina nycklar inte tolkas som de ska:

```terminal
ERRO[2022-10-10 00:01:41] Error while refreshing token: error while getting jwt from magento: invalid character 'M' looking for beginning of value
FATA[2022-12-10 20:38:44] bad http status from https://updater.supportinsights.adobe.com/linux-amd64.json: 403 Forbidden
```

Lös det här felet genom att försöka med följande steg:

1. Gör en [skriptad installation](#scripted), spara utdata och granska utdata för fel.
1. Granska den genererade `config.yaml` och verifiera att sökvägen till din Commerce-instans och PHP är korrekt.
1. Kontrollera att användaren som kör schemaläggaren finns i [ägare av filsystem](../../installation/prerequisites/file-system/overview.md) Unix-gruppen eller är samma användare som filsystemets ägare.
1. Se till att [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce-merchant-services/user-guides/integration-services/saas.html) knapparna är korrekt installerade och försöker uppdatera dem för att ansluta tillägget till systemet.
1. [Avinstallera](#uninstall) agenten när nycklarna har uppdaterats och ominstallerats med [installationsskript](#scripted).
1. Kör schemaläggaren och se om du fortfarande får samma fel.
1. Om du fortfarande får samma fel ökar du loggnivån i dialogrutan `config.yaml` för att felsöka och öppna en supportanmälan.

### *SIGFAULT* Fel

Om du ser en *SIGFAULT* när du kör binära filer, kör du förmodligen inte detta som filägare för Adobe Commerce- och agentfiler.
Kontrollera också om alla filer i agentkatalogen som har samma användare som fileägaren som Adobe Commerce-filer har och binärfiler ska köras under den användaren.
Du kan använda `chown` om du vill ändra filens ägare och växla till rätt användare.
Kontrollera att din daemoniseringsmekanism (Cron eller System.d) kör processen under rätt användare.

>[!INFO]
>
>Se [Åtkomst [!DNL Site-Wide Analysis Tool] och generera rapporter](../site-wide-analysis-tool/access.md).
