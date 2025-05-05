---
title: Installationshandbok
description: Använd den här guiden för att installera [!DNL Site-Wide Analysis Tool] för din webbplats
exl-id: ba36dc74-806d-49c5-b4d1-ba53ed4076fb
feature: Configuration, Install
source-git-commit: 16feb8ec7ecc88a6ef03a769d45b1a3a2fe88d97
workflow-type: tm+mt
source-wordcount: '1136'
ht-degree: 0%

---

# Installationshandbok

>[!IMPORTANT]
>
>Från och med den 23 april 2024 kommer den [!DNL Site-Wide Analysis Tool] att inaktiveras för alla Adobe Commerce lokala kunder.

Det [!DNL Site-Wide Analysis Tool] ger 24/7 prestandaövervakning, rapporter och rekommendationer i realtid för att säkerställa säkerheten och användbarheten för Adobe Commerce på molninfrastrukturinstallationer. Den innehåller också detaljerad information om tillgängliga och installerade korrigeringsfiler, tillägg från tredje part och din Adobe Commerce-installation.

>[!INFO]
>
>Lär dig [hur du [!DNL Site-Wide Analysis Tool] aktiverar](../site-wide-analysis-tool/access.md) och genererar rapporter.

Om du har en lokal installation av Adobe Commerce installerar du en agent på din infrastruktur för att använda verktyget. Du behöver inte installera agenten på Adobe Commerce i molninfrastrukturprojekt.

## Agent

Med agenten [!DNL Site-Wide Analysis Tool] kan du använda [!DNL Site-Wide Analysis Tool] för lokala installationer av Adobe Commerce.

Agenten [!DNL Site-Wide Analysis Tool] samlar in program- och affärsdata, analyserar dem och ger ytterligare insikter om installationstillståndet så att du kan förbättra kundupplevelsen. Den övervakar ditt program och hjälper dig att identifiera problem med prestanda, säkerhet, tillgänglighet och program.

Följande steg krävs för att installera agenten:

1. Kontrollera systemkraven.

1. Konfigurera API-nycklar i tillägget [!UICONTROL Commerce Services Connector].

1. Installera agenten.

1. Kör agenten.

>[!INFO]
>
>Agenten har stöd för Adobe Commerce-installationer med flera noder. Installera och konfigurera agenten på varje nod.

## Systemkrav

Din lokala infrastruktur måste uppfylla följande krav innan du installerar agenten:

- Operativsystem

   - [!DNL Linux x86-64]-fördelningar, som [!DNL Red Hat® Enterprise Linux (RHEL)], [!DNL CentOS], [!DNL Ubuntu], [!DNL Debian] och liknande

  >[!IMPORTANT]
  >
  >Adobe Commerce stöds inte på [!DNL Microsoft Windows] eller [!DNL macOS].

- Adobe Commerce 2.4.5-p1 eller senare (på grund av beroendet av Service Connector)

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

Agenten kräver att tillägget [[!DNL Commerce Services Connector]](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html?lang=sv-SE) är installerat på datorn och [konfigurerat](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html?lang=sv-SE) med API-nycklar. Kontrollera att tillägget är installerat genom att köra följande kommando:

```bash
bin/magento module:status Magento_ServicesId
```

Om du har installerat tillägget och konfigurerat det med en befintlig API-nyckel för en annan tjänst, **MÅSTE du generera om API-nyckeln** och uppdatera den i Adobe Commerce Admin för agenten.

1. Placera webbplatsen i [underhållsläge](../../installation/tutorials/maintenance-mode.md).

1. Logga in på [account.magento.com](https://account.magento.com/customer/account/login?_ga=2.164207871.117144580.1649172612-1623400270.1640858671).

   >[!NOTE]
   >
   > Om du har problem med att få åtkomst till ditt konto kan du läsa [Det går inte att logga in på Adobe Commerce support eller molnkontot](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/troubleshooting/miscellaneous/unable-to-log-in-to-support-or-cloud-project.html?lang=sv-SE) för att få hjälp med felsökning.

1. Klicka på **[!UICONTROL API Portal]**.

1. Klicka på **[!UICONTROL Delete]** bredvid den befintliga API-nyckeln.

1. [Konfigurera](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html?lang=sv-SE) en ny API-nyckel.

>[!IMPORTANT]
>
> Om du genererar nya nycklar i API-portalen ska du omedelbart uppdatera API-nycklarna i [!DNL Admin configuration]. Om du genererar nya nycklar och inte uppdaterar nycklarna i [!DNL Admin] kommer dina SaaS-tillägg inte längre att fungera och du kommer att förlora värdefulla data.

Om tillägget inte är installerat följer du instruktionerna nedan för att installera det:

1. Lägg till tillägget i din `composer.json`-fil och installera det.

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

1. [Konfigurera API-nycklar](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html?lang=sv-SE) för att ansluta tillägget till systemet.

## Installera agenten

Vi har skapat ett [gränssnittsskript](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) som förenklar installationen. Vi rekommenderar att du använder gränssnittsskriptet, men du kan följa metoden [manuell installation](#manual) om det behövs.

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
   >Vi rekommenderar att agenten installeras utanför Adobe Commerce rotprojektkatalog.

1. Verifiera installationen.

   ```bash
   ./scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. När du har hämtat och installerat agenten [konfigurerar du den så att den körs](#run-the-agent) på något av följande sätt:

   - [Tjänst](#service) (helst om du har rotåtkomst)

   - [Cron](#cron)

### Manuell {#manual}

Om du inte vill använda vårt [gränssnittsskript](https://github.com/magento-swat/install-agent-helpers/blob/main/install.sh) för att installera agenten måste du installera den manuellt genom att följa de här stegen:

1. Skapa en katalog där du vill hämta agenten.

   >[!TIP]
   >
   >Vi rekommenderar att agenten installeras utanför Adobe Commerce rotprojektkatalog.

1. Hämta den binära filen och packa upp den.

   >[!INFO]
   >
   >Om du vill använda [!DNL Site-Wide Analysis Tool] måste du först läsa och godkänna användningsvillkoren som presenteras när du öppnar instrumentpanelen från Adobe Commerce Admin.

   För **AMD64**-arkitekturen:

   1. Ladda ned startarkivet.

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-amd64.tar.gz
      ```

   1. Packa upp startarkivet.

      ```bash
      tar -xf launcher.linux-amd64.tar.gz
      ```

   För **ARM64**-arkitekturen:

   1. Ladda ner startarkivet.

      ```bash
      curl -O https://updater.supportinsights.adobe.com/launcher/launcher.linux-arm64.tar.gz
      ```

   1. Packa upp startarkivet.

      ```bash
      tar -xf launcher.linux-arm64.tar.gz
      ```

1. *(Valfritt)* Verifiera signaturen för checksummefilen.

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

1. `config.yaml` Skapa filen med följande innehåll.

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

1. Verifiera installationen.

   ```bash
   scheduler -v
   ```

   ```bash
   Version: 1.0.1
   Success exit.
   ```

1. När du har hämtat och installerat agenten måste du [konfigurera den så att den körs](#run-the-agent) på något av följande sätt:

   - [Tjänst](#service) (helst om du har rotåtkomst)

   - [Cron](#cron)

## Kör agenten {#run-the-agent}

Vi rekommenderar att du konfigurerar agenten så att den körs som en tjänst. Om du har begränsad åtkomst till din infrastruktur och inte har rotbehörigheter måste du använda [cron](#cron) i stället.

### Tjänst {#service}

1. Skapa en systemd-enhetsfil `(/etc/systemd/system/scheduler.service)` med följande konfiguration (ersätt `<filesystemowner>` med den UNIX-användare® som äger katalogen där agenten och Adobe Commerce-programvaran är installerade). Om du har laddat ned agenten som rotanvändare ändrar du ägaren till katalogen och de kapslade filerna.

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

1. Kontrollera att tjänsten är igång.

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

1. Ta bort enhetsfilen `systemd` för schemaläggningstjänsten.

   ```bash
   rm /etc/systemd/system/scheduler.service
   ```

1. Läs in hanterarkonfigurationen för `systemd` igen.

   ```bash
   systemctl daemon-reload
   ```

1. Återställ eventuella `systemd` enheter från ett felaktigt tillstånd.

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

```
ERRO[2022-10-10 00:01:41] Error while refreshing token: error while getting jwt from magento: invalid character 'M' looking for beginning of value
FATA[2022-12-10 20:38:44] bad http status from https://updater.supportinsights.adobe.com/linux-amd64.json: 403 Forbidden
```

Lös det här felet genom att försöka med följande steg:

1. Gör en [skriptad installation](#scripted), spara utdata och granska utdata för fel.
1. Granska den genererade `config.yaml`-filen och kontrollera att sökvägen till din Commerce-instans och PHP är korrekt.
1. Kontrollera att användaren som kör schemaläggaren finns i Unix-gruppen [för filsystemet](../../installation/prerequisites/file-system/overview.md) eller är samma användare som filsystemets ägare.
1. Kontrollera att nycklarna för [Commerce Services Connector](https://experienceleague.adobe.com/docs/commerce/user-guides/integration-services/saas.html?lang=sv-SE) är korrekt installerade och försök uppdatera dem för att ansluta tillägget till systemet.
1. [Avinstallera](#uninstall) agenten efter att nycklarna har uppdaterats och installera om med [installationsskriptet](#scripted).
1. Kör schemaläggaren och se om du fortfarande får samma fel.
1. Om du fortfarande får samma fel kan du öka loggnivån i `config.yaml` för att felsöka och öppna en supportanmälan.

### *SIGFAULT* Fel

Om du får ett *SIGFAULT*-fel när du kör binära filer, kommer du förmodligen inte att köra detta som filägare för Adobe Commerce- och agentfiler.
Kontrollera också om alla filer i agentkatalogen som har samma användare som fileägaren som Adobe Commerce-filer har och binärfiler ska köras under den användaren.
Du kan använda kommandot `chown` för att ändra filägaren och växla till lämplig användare.
Kontrollera att din daemoniseringsmekanism (Cron eller System.d) kör processen under rätt användare.

>[!INFO]
>
>Se [Åtkomst [!DNL Site-Wide Analysis Tool] och generera rapporter](../site-wide-analysis-tool/access.md).
