---
title: Kommandoradsverktyg
description: Använd Commerce kommandoradsverktyg för att köra installations- och konfigureringsuppgifter.
exl-id: 44470ce1-a5a2-4c12-962e-e42d11a6bd15
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 0%

---

# Kommandoradsverktyg

Commerce har ett kommandoradsgränssnitt (CLI) -`<magento_root>/bin/magento` - som kör installations- och konfigureringsuppgifter, inklusive:

- Installera Commerce (och relaterade uppgifter som att uppdatera databasschemat, skapa en distributionskonfiguration)
- Rensar cachen
- Hantera index, inklusive omindexering
- Skapa översättningsordlistor och översättningspaket
- Generera obefintliga klasser som fabriker och spärrar för plugin-program och generera konfigurationen för beroendeinjicering för objekthanteraren
- Distribuera statiska vyfiler
- Skapa CSS från mindre

Ytterligare fördelar:

- Ett enskilt kommando (`<magento_root>/bin/magento list`) visar alla tillgängliga installations- och konfigurationskommandon.
- Enhetligt användargränssnitt baserat på Symfoni.
- CLI är utbyggbart så att tredjepartsutvecklare kan&quot;ansluta&quot; till det. Detta innebär också att man slipper inlärningskurva.
- Kommandon för inaktiverade moduler visas inte.

I det här avsnittet diskuteras hur du konfigurerar Adobe Commerce-programmet med CLI. Information om hur du installerar Commerce finns i [Installationsflöde](../../installation/overview.md) i _Installationsguiden_.

## Förutsättningar

Innan du börjar använda CLI bör du kontrollera att:

1. Ditt system uppfyller de krav som beskrivs i [Systemkrav](../../installation/system-requirements.md) i _Installationsguiden_.
1. Du har slutfört alla nödvändiga uppgifter som diskuterades i [Förutsättningar](../../installation/prerequisites/overview.md) i _installationshandboken_.
1. När du har loggat in på Commerce-servern växlar du till en användare som har behörighet att skriva till Commerce filsystem. Se [växla till filsystemets ägare](../../installation/prerequisites/file-system/overview.md) i _installationshandboken_.

## Kör kommandon

Använd följande syntax för att växla till filsystemets ägare och ange kommandot samtidigt för basskalet:

```bash
su <file system owner> -s /bin/bash -c <command>
```

Om filsystemets ägare inte tillåter inloggningar kan du använda följande:

```bash
sudo -u <file system owner> <command>
```

**Så här kör du CLI-kommandon från valfri katalog**:

Lägg till `<magento_root>/bin` i systemet `PATH`.

Exempel på basgränssnitt för CentOS:

```bash
export PATH=$PATH:/var/www/html/magento2/bin
```

Du kan också köra följande:

- `cd <magento_root>/bin` och kör dem som `./magento <command name>`
- `<magento_root>/bin/magento <command name>`
- `<magento_root>` är en underkatalog till webbserverns docroot
