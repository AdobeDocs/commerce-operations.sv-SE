---
title: Kör enhetstester
description: Kör enhetstester som definieras i Adobe Commerce kodbas.
exl-id: 23200420-d15c-4910-8ce6-abd0cc070777
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '141'
ht-degree: 0%

---

# Kör enhetstester

{{file-system-owner}}

Det här kommandot kör en uppsättning tester som definierats i kodbasen i Commerce 2. Du kan antingen köra alla tester eller tester som du väljer. När en typ som inte stöds anges avslutas programmet och alla tillgängliga typer visas. Efter körning visas en detaljerad rapport som visar testkörningen och resultaten.

## Förutsättningar

Innan du kör det här kommandot gör du följande _måste_ vara true:

- The `Magento_Developer` -modulen måste vara aktiverad. Du kan aktivera den på följande sätt:

  ```bash
  bin/magento module:enable [--force] Magento_Developer
  ```

  Använd `--force` endast om det är nödvändigt.

- Systemet måste vara konfigurerat för att köra de önskade testerna.

Om du till exempel vill köra integrationstester bör du kopiera `dev/tests/integration/etc/install-config-mysql.php.dist` till `dev/tests/integration/etc/install-config-mysql.php` och anpassa den efter din egen miljö.

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

```terminal
all, unit, integration, integration-all, static, static-all, integrity, legacy, default
```

Så här kör du integreringstester:

```bash
bin/magento dev:tests:run integration
```
