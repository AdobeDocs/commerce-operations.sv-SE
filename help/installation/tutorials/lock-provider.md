---
title: Konfigurera låsprovidern
description: Följ de här stegen för att förhindra att duplicerade cron-jobb och cron-grupper körs på din Adobe Commerce-distribution.
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '224'
ht-degree: 0%

---

# Konfigurera låsprovidern

Innan du kör kommandot måste du göra följande *eller* du måste [installera programmet](../advanced.md):

* [Skapa eller uppdatera distributionskonfigurationen](deployment.md)
* [Skapa databasschemat](database.md)

## Säker installation

{{$include /help/_includes/secure-install.md}}

## Konfigurera låset

Konfigurera en låsleverantör för att förhindra att dubblettcron-jobb och cron-grupper startas. (Kräver Adobe Commerce 2.2.x, 2.2.5 och senare samt 2.3.3 och senare.)

Adobe Commerce använder databasen för att spara lås som standard. Om du har flera noder på dina servrar rekommenderar vi att du använder Zookeeper som låsleverantör.

Om du kör Adobe Commerce i molninfrastruktur behöver du inte konfigurera inställningar för låsleverantör. Programmet konfigurerar fillås-providern för Pro-projekt under provisioneringsprocessen. Se [Molnvariabler](https://devdocs.magento.com/cloud/env/variables-cloud.html).

### Kommandoanvändning

```bash
bin/magento setup:config:set [--<parameter_name>=<value>, ...]
```

### Parameterbeskrivningar

| Namn | Värde | Obligatoriskt? |
|--- |--- |--- |
| `--lock-provider` | Lås leverantörens namn: `db`, `zookeeper`, eller `file`.<br><br>Standardlåsleverantör: `db` | Nej |
| `--lock-db-prefix` | Det specifika db-prefixet för att undvika låskonflikter när du använder `db` låsleverantör.<br><br>Standardvärdet: `NULL` | Nej |
| `--lock-zookeeper-host` | Värd och port att ansluta till Zookeeper-klustret när du använder `zookeeper` låsleverantör.<br><br>Till exempel: `127.0.0.1:2181` | Ja, om du anger `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Sökvägen där Zookeeper sparar lås.<br><br>Standardsökvägen är: `/magento/locks` | Nej |
| `--lock-file-path` | Sökvägen där fillås sparas. | Ja, om du anger `--lock-provider=file` |
