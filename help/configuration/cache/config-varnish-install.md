---
title: Installera lack
description: Se råd om hur du installerar Varnish.
source-git-commit: c65c065c5f9ac2847caa8898535afdacf089006a
workflow-type: tm+mt
source-wordcount: '165'
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

Ett exempel följer:

```terminal
varnishd (varnish-6.3.2 revision 199de9b)
Copyright (c) 2006 Verdens Gang AS
Copyright (c) 2006-2019 Varnish Software AS
```

Kontrollera att versionen är 6.x innan du fortsätter. Om du kör en version som är lägre än 6.x måste du uppgradera till en version som stöds. Mer information finns i installationsdokumentationen för Varnish.
