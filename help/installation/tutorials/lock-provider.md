---
title: Konfigurera låsprovidern
description: Följ de här stegen för att förhindra att duplicerade cron-jobb och cron-grupper körs på din Adobe Commerce- eller Magento Open Source-distribution.
exl-id: c54e05b7-38fd-4731-bc77-a873b44d0ae8
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---

# Konfigurera låsprovidern

Innan du kör kommandot måste du göra följande *eller* du måste [installera programmet](../advanced.md):

* [Skapa eller uppdatera distributionskonfigurationen](deployment.md)
* [Skapa databasschemat](database.md)

## Säker installation

{{$include /help/_includes/secure-install.md}}

## Konfigurera låset

Konfigurera en låsleverantör för att förhindra att dubblettcron-jobb och cron-grupper startas. (Kräver Adobe Commerce eller Magento Open Source 2.2.x, 2.2.5 och senare samt 2.3.3 och senare.)

Adobe Commerce och Magento Open Source använder databasen för att spara lås som standard. Om du har flera noder på dina servrar rekommenderar vi att du använder Zookeeper som låsleverantör.

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
| `--lock-zookeeper-host` | Värd och port att ansluta till Zookeeper-klustret när du använder `zookeeper` låsleverantör.<br><br>Exempel: `127.0.0.1:2181` | Ja, om du anger `--lock-provider=zookeeper` |
| `--lock-zookeeper-path` | Sökvägen där Zookeeper sparar lås.<br><br>Standardsökvägen är: `/magento/locks` | Nej |
| `--lock-file-path` | Sökvägen där fillås sparas. | Ja, om du anger `--lock-provider=file` |
