---
title: Installera lack
description: Läs mer om installationskraven för Adobe Commerce cachning. Upptäck installationsresurser och riktlinjer för konfiguration.
feature: Configuration, Cache
exl-id: e1881a85-3965-42d9-a46f-c2f5f20fbacc
source-git-commit: 10f324478e9a5e80fc4d28ce680929687291e990
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---

# Installera lack

Installation av programvara för lack ligger utanför den här handbokens räckvidd. Mer information om hur du installerar Varnish finns i:

- [installationshandbok](https://www.varnish-software.com/developers/tutorials/installing-varnish-ubuntu/)
- [Installationsguider för lack](https://www.varnish-cache.org/docs)
- [Så här installerar du engelska (Tecmint)](https://www.tecmint.com/install-varnish-cache-web-accelerator/)

>[!INFO]
>
>Det här avsnittet är skrivet för lack i CentOS och Apache 2.4. Om du konfigurerar lack i en annan miljö är vissa kommandon troligtvis olika. Mer information finns i föregående dokumentation.
>
>Om du tänker installera variantmoduler (vmods), till exempel helskärmsläge, bör du installera varnish genom att kompilera koden i stället för att installera från ett paket. Mer information finns i [Saint-läge](config-varnish-advanced.md#saint-mode).

## Bekräfta din engelska version

Öppna en terminal och ange följande kommando för att visa versionen av lack:

```bash
varnishd -V
```

Kontrollera att [Adobe Commerce stöder](../../installation/system-requirements.md) den installerade versionen av Varnish innan du fortsätter. Om du kör en version som inte stöds måste du uppgradera till en version som stöds. Mer information finns i installationsdokumentationen för Varnish.
