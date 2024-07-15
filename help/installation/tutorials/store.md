---
title: Konfigurera butiken
description: Följ de här stegen för att konfigurera din Adobe Commerce Store.
exl-id: ab5e9c43-d914-4de9-98a9-b60d3984b23c
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Konfigurera butiken

Innan du kör det här kommandot måste du göra följande *eller* måste du [installera programmet](../advanced.md):

* [Skapa eller uppdatera distributionskonfigurationen](deployment.md)
* [Skapa databasschemat](database.md)

## Säker installation

{{$include /help/_includes/secure-install.md}}

## Konfigurera butiken

Kommandoanvändning:

```bash
bin/magento setup:store-config:set [--<parameter_name>=<value>, ...]
```

Där följande tabell definierar parametrar och värden:

| Namn | Värde | Obligatoriskt? |
|--- |--- |--- |
| `--base-url` | Bas-URL som används för att komma åt din administratör och butiker i något av följande format: <br><br>- `http[s]://<host or ip>/<your install dir>/`.<br><br>**Obs!** Schemat (`http://` eller `https://`) och ett avslutande snedstreck krävs båda. `<your install dir>` är den dokumentberoende sökvägen där programmet ska installeras. Beroende på hur du konfigurerar webbservern och de virtuella värdarna kan sökvägen vara magento2 eller tom.<br><br>Du kan använda `http://127.0.0.1/<your install dir>/` för att komma åt programmet på den lokala värden.<br><br>- `{{base_url}}` som representerar en bas-URL som definieras av en virtuell värdinställning eller av en virtualiseringsmiljö som Docker. Om du till exempel konfigurerar en virtuell värd med värdnamnet commerce.example.com kan du installera programmet med `--base-url={{base_url}}` och få åtkomst till administratören med en URL som `http://commerce.example.com/admin`. | Nej |
| `--language` | Språkkod som ska användas i Admin och storefront.<br><br>(Om du inte redan har gjort det kan du visa listan med språkkoder genom att ange `magento info:language:list` i katalogen `bin`.) | Nej |
| `--currency` | Standardvaluta som ska användas i butiken. <br><br>(Om du inte redan har gjort det kan du visa listan över valutor genom att ange `magento info:currency:list` i katalogen `bin`.) | Nej |
| `--timezone` | Standardtidszon att använda i Admin och storefront. (Om du inte redan har gjort det kan du visa listan över tidszoner genom att ange `magento info:timezone:list` i katalogen `bin`.) | Nej |
| `--use-rewrites` | `1` betyder att du använder webbserveromskrivningar för genererade länkar i storefront och Admin.<br><br>`0` inaktiverar användning av omskrivningar av webbservrar. Det här är standardinställningen. | Nej |
| `--use-secure` | `1` aktiverar användning av Secure Sockets Layer (SSL) i butiks-URL:er. Kontrollera att webbservern stöder SSL innan du väljer det här alternativet.<br><br>`0` inaktiverar användningen av SSL. I det här fallet antas alla andra säkra URL-alternativ också vara 0. Det här är standardinställningen. | Nej |
| `--base-url-secure` | Säker bas-URL som ska användas för att komma åt din administratör och butiker i följande format: `http[s]://<host or ip>/<your install dir>/` | Nej |
| `--use-secure-admin` | `1` betyder att du använder SSL för att komma åt administratören. Kontrollera att webbservern stöder SSL innan du väljer det här alternativet.<br><br>`0` betyder att du inte använder SSL med administratören. Det här är standardinställningen. | Nej |
| `--admin-use-security-key` | `1` gör att programmet använder ett slumpmässigt genererat nyckelvärde för att få åtkomst till sidor i Admin och i formulär. Dessa nyckelvärden hjälper till att förhindra attacker med förfalskade korsskriptattacker mellan webbplatser. Det här är standardinställningen.<br/><br/>`0` inaktiverar användningen av nyckeln. | Nej |
| `--magento-init-params` | Lägg till i valfritt kommando för att anpassa parametrar för programinitiering<br/><br/>Till exempel: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | Nej |
