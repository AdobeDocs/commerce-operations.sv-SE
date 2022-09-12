---
title: Konfigurera butiken
description: Följ de här stegen för att konfigurera din Adobe Commerce- eller Magento Open Source-butik.
source-git-commit: 46302eb8e8fd9bb7c9e7fbf990abb149bedd0ff4
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---


# Konfigurera butiken

Innan du kör det här kommandot måste du göra följande *eller* du måste [installera programmet](../advanced.md):

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
| `--base-url` | Bas-URL som används för att komma åt din administratör och butiker i något av följande format:<br><br>- `http[s]://<host or ip>/<your install dir>/`.<br><br>**Obs!** Ordningen (`http://` eller `https://`) och ett avslutande snedstreck krävs. `<your install dir>` är den dokumentberoende sökvägen som programmet ska installeras i. Beroende på hur du konfigurerar webbservern och de virtuella värdarna kan sökvägen vara magento2 eller tom.<br><br>Om du vill komma åt programmet på localhost kan du använda `http://127.0.0.1/<your install dir>/`.<br><br>- `{{base_url}}` som representerar en bas-URL som definieras av en virtuell värdinställning eller av en virtualiseringsmiljö som Docker. Om du till exempel konfigurerar en virtuell värd med värdnamnet commerce.example.com kan du installera programmet med `--base-url={{base_url}}` och få åtkomst till administratören via en URL som `http://commerce.example.com/admin`. | Nej |
| `--language` | Språkkod som ska användas i Admin och storefront.<br><br>(Om du inte redan har gjort det kan du visa listan med språkkoder genom att ange `magento info:language:list` från `bin` katalog.) | Nej |
| `--currency` | Standardvaluta som ska användas i butiken. <br><br>(Om du inte redan har gjort det kan du visa listan över valutor genom att ange `magento info:currency:list` från `bin` katalog.) | Nej |
| `--timezone` | Standardtidszon att använda i Admin och storefront. (Om du inte redan har gjort det kan du visa listan över tidszoner genom att ange `magento info:timezone:list` från `bin` katalog.) | Nej |
| `--use-rewrites` | `1` innebär att du använder webbserveromskrivningar för genererade länkar i butiken och Admin.<br><br>`0` inaktiverar användning av webbserveromskrivningar. Detta är standardinställningen. | Nej |
| `--use-secure` | `1` används för att använda SSL (Secure Sockets Layer) i butiks-URL:er. Kontrollera att webbservern har stöd för SSL innan du väljer det här alternativet.<br><br>`0` inaktiverar användningen av SSL. I det här fallet antas alla andra säkra URL-alternativ också vara 0. Detta är standardinställningen. | Nej |
| `--base-url-secure` | Säker bas-URL som används för att få åtkomst till din administratör och butiker i följande format: `http[s]://<host or ip>/<your install dir>/` | Nej |
| `--use-secure-admin` | `1` innebär att du använder SSL för att komma åt administratören. Kontrollera att webbservern har stöd för SSL innan du väljer det här alternativet.<br><br>`0` betyder att du inte använder SSL med administratören. Detta är standardinställningen. | Nej |
| `--admin-use-security-key` | `1` gör att programmet använder ett slumpmässigt genererat nyckelvärde för att få åtkomst till sidor i Admin och i formulär. Dessa nyckelvärden hjälper till att förhindra attacker med förfalskade korsskriptattacker mellan webbplatser. Detta är standardinställningen.<br/><br/>`0` inaktiverar användningen av nyckeln. | Nej |
| `--magento-init-params` | Lägg till i valfritt kommando för att anpassa parametrar för programinitiering<br/><br/>Till exempel: `MAGE_MODE=developer&MAGE_DIRS[base][path]=/var/www/example.com&MAGE_DIRS[cache][path]=/var/tmp/cache` | Nej |
