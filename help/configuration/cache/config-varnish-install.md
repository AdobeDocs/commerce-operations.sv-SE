---
title: Installera lack
description: Se råd om hur du installerar Varnish.
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
source-git-commit: ec3ab7e3c6c3835e73653b0d4f74aadc861016d3
workflow-type: tm+mt
source-wordcount: '162'
ht-degree: 0%

---

# Installera lack

Installation av programvara för lack ligger utanför den här handbokens räckvidd. Mer information om hur du installerar Varnish finns i:

- [installationsguide](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [Installationsguider för lack](https://www.varnish-cache.org/docs)
- [Så här installerar du Varnish (Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>Det här avsnittet är skrivet för lack i CentOS och Apache 2.4. Om du konfigurerar lack i en annan miljö är vissa kommandon troligtvis olika. Mer information finns i föregående dokumentation.
>
>Om du tänker installera variantmoduler (vmods), till exempel helskärmsläge, bör du installera varnish genom att kompilera koden i stället för att installera från ett paket. Se [Saint-läge](config-varnish-advanced.md#saint-mode) för mer information.

## Bekräfta din engelska version

Öppna en terminal och ange följande kommando för att visa versionen av lack:

```bash
varnishd -V
```

Se till att [Adobe Commerce och Magento Open Source stöder](../../installation/system-requirements.md) den installerade versionen av Varnish innan du fortsätter. Om du kör en version som inte stöds måste du uppgradera till en version som stöds. Mer information finns i installationsdokumentationen för Varnish.
