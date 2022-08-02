---
title: Kommandoradsverktyg
description: Använd kommandoradsverktyget i Commerce för att köra installations- och konfigureringsuppgifter.
source-git-commit: 6a3995dd24f8e3e8686a8893be9693581d31712b
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---


# Kommandoradsverktyg

Commerce har ett kommandoradsgränssnitt -`<magento_root>/bin/magento`—som kör installations- och konfigureringsuppgifter, inklusive:

- Installera Commerce (och relaterade uppgifter som att uppdatera databasschemat, skapa en distributionskonfiguration)
- Rensar cachen
- Hantera index, inklusive omindexering
- Skapa översättningsordlistor och översättningspaket
- Generera obefintliga klasser som fabriker och spärrar för plugin-program och generera konfigurationen för beroendeinjicering för objekthanteraren
- Distribuera statiska vyfiler
- Skapa CSS från mindre

Ytterligare fördelar:

- Ett enda kommando (`<magento_root>/bin/magento list`) listar alla tillgängliga installations- och konfigurationskommandon.
- Enhetligt användargränssnitt baserat på Symfoni.
- CLI är utbyggbart så att tredjepartsutvecklare kan&quot;ansluta&quot; till det. Detta innebär också att man slipper inlärningskurva.
- Kommandon för inaktiverade moduler visas inte.

I det här avsnittet diskuteras hur du konfigurerar Adobe Commerce och Magento Open Source med hjälp av CLI. Mer information om hur du installerar Commerce finns i [Installationsöversikt](https://devdocs.magento.com/guides/2.4/install-gde/bk-install-guide.html) i _Installationsguide_.

## Förutsättningar

Innan du börjar använda CLI bör du kontrollera att:

1. Ditt system uppfyller kraven i [Systemkrav](https://devdocs.magento.com/guides/v2.4/install-gde/system-requirements.html) i _Installationsguide_.
1. Du har slutfört alla nödvändiga uppgifter som diskuterades i [Förutsättningar](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/prereq-overview.html) i _Installationsguide_.
1. När du har loggat in på Commerce-servern växlar du till en användare som har behörighet att skriva till Commerce-filsystemet. Se [växla till filsystemets ägare](https://devdocs.magento.com/guides/v2.4/install-gde/prereq/file-sys-perms-over.html) i _Installationsguide_.

## Kör kommandon

Använd följande syntax för att växla till filsystemets ägare och ange kommandot samtidigt för basskalet:

```bash
su <file system owner> -s /bin/bash -c <command>
```

Om filsystemets ägare inte tillåter inloggningar kan du använda följande:

```bash
sudo -u <file system owner> <command>
```

**Köra CLI-kommandon från vilken katalog som helst**:

Lägg till `<magento_root>/bin` till ditt system `PATH`.

Exempel på basgränssnitt för CentOS:

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

Du kan också köra följande:

- `cd <magento_root>/bin` och kör dem som `./magento <command name>`
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` är en underkatalog till webbserverns dokument
