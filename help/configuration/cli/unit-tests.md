---
title: Kör enhetstester
description: Kör enhetstester som definieras i Adobe Commerce kodbas.
exl-id: 23200420-d15c-4910-8ce6-abd0cc070777
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '142'
ht-degree: 0%

---

# Kör enhetstester

{{file-system-owner}}

Det här kommandot kör en uppsättning tester som definieras i Commerce 2-kodbasen. Du kan antingen köra alla tester eller tester som du väljer. När en typ som inte stöds anges avslutas programmet och alla tillgängliga typer visas. Efter körning visas en detaljerad rapport som visar testkörningen och resultaten.

## Förutsättningar

Innan du kör det här kommandot måste följande _vara_:

- Modulen `Magento_Developer` måste aktiveras. Du kan aktivera den på följande sätt:

  ```bash
  bin/magento module:enable [--force] Magento_Developer
  ```

  Använd bara alternativet `--force` om det är nödvändigt.

- Systemet måste vara konfigurerat för att köra de önskade testerna.

Om du till exempel vill köra integrationstester bör du kopiera `dev/tests/integration/etc/install-config-mysql.php.dist` till `dev/tests/integration/etc/install-config-mysql.php` och ändra den så att den passar din miljö.

## Köra tester

Kommandoanvändning:

```bash
bin/magento dev:tests:run <test>
```

Så här listar du tillgängliga testtyper:

```bash
bin/magento dev:tests:run --help
```

Exempelretur:

```
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

Så här kör du integreringstester:

```bash
bin/magento dev:tests:run integration
```
