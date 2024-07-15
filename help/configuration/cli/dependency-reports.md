---
title: Beroenderapporter
description: Skapa rapporter som visar summorna för modul-, cirkulär- och ramverksberoenden.
exl-id: b7a32fe1-71c5-495f-8276-242503fb50ae
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 0%

---

# Beroenderapporter

{{file-system-owner}}

Du kan köra följande typer av rapporter:

- **Modulberoenden**: Visar det totala antalet beroenden mellan moduler och om beroendena är hårda eller mjuka.
- **Cirkulära beroenden**: Visar det totala antalet beroendekedjor samt antalet och listan med cirkulära beroenden för varje modul.
- **Ramverksberoenden**: Visar det totala antalet beroenden av Commerce Framework per modul (inklusive det totala antalet ramverksposter för varje bibliotek).

Ett beroende i en kommentar är också ett beroende.

## Kör beroenderapporter

Kommandoalternativ:

```bash
bin/magento info:dependencies:{show-modules|show-modules-circular|show-framework} [-d|--directory="<path>"] [-o|--output="<path and filename"]
```

I följande tabell förklaras kommandots alternativ, parametrar och värden.

| Parameter | Värde | Obligatoriskt? |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------- | --------- |
| `show-modules` | Rapport om modulberoenden. | Ja |
| `show-modules-circular` | Cirkulär beroenderapport. | Ja |
| `show-framework` | Rapport om ramverksberoenden. | Ja |
| `-d --directory` | Sökväg till baskatalogen för att börja söka efter rapportdata. | Nej |
| `-o --output` | Anger den absoluta filsystemsökvägen och filnamnet för rapportens CSV-utdatafil (kommaavgränsat värde). | Nej |

Om ingen katalog eller filnamn skickas som argument används följande programrot som standardkatalog och följande standardfilnamn används:

| Kommando | Filnamn |
| ----------------------------------------------------- | ----------------------------------- |
| `bin/magento info:dependencies:show-modules` | `modules-dependencies.csv` |
| `bin/magento info:dependencies:show-modules-circular` | `modules-circular-dependencies.csv` |
| `bin/magento info:dependencies:show-framework` | `framework-dependencies.csv` |

### Exempelmodulens beroenderapport

Följande är en del av utdata för en exempelmodulberoenderapport:

```terminal
"","All","Hard","Soft"
"Total number of dependencies","602","587","15"

"Dependencies for each module:","All","Hard","Soft"
"magento/module-cron","2","2","0"
" -- magento/module-config","","1","0"
" -- magento/module-store","","1","0"

"magento/module-catalog-rule","8","8","0"
" -- magento/module-store","","1","0"
" -- magento/module-rule","","1","0"
" -- magento/module-catalog","","1","0"
" -- magento/module-customer","","1","0"
" -- magento/module-backend","","1","0"
" -- magento/module-eav","","1","0"
" -- magento/module-indexer","","1","0"
" -- magento/module-import-export","","1","0"
```

### Exempel på cirkelberoenderapport

Följande är en del av utdata för en cirkelberoenderapport:

```terminal
"Circular dependencies:","Total number of chains"
"","848"

"Circular dependencies for each module:",""
"magento/module-config","70"
"magento/module-config->magento/module-store->magento/module-directory->magento/module-config"
"magento/module-config->magento/module-store->magento/module-config"
"magento/module-config->magento/module-cron->magento/module-config"
"magento/module-config->magento/module-email->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-theme->magento/module-customer->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-reports->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-catalog->magento/module-theme->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-catalog->magento/module-log->magento/module-eav->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-checkout->magento/module-catalog-inventory->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-checkout->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-customer->magento/module-theme->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-payment->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-checkout->magento/module-customer->magento/module-review->magento/module-catalog->magento/module-themeax->magento/module-config"
"magento/module-config->magento/module-backend->magento/module-sales->magento/module-checkout->magento/module-customer->magento/module-review->magento/module-catalog->magento/module-catalog-rule->magento/module-rule->magento/module-eav->magento/module-config"
```

### Exempelrapport om ramverksberoenden

Följande är en del av utdata för en exempelrapport om ramverksberoenden:

```terminal
"Dependencies of framework:","Total number"
"","111"

"Dependencies for each module:",""
"Magento\Cron","1"
" -- Magento\Framework","143"

"Magento\CatalogRule","1"
" -- Magento\Framework","234"

"Magento\Webapi","2"
" -- Magento\Framework","347"
" -- Magento\Server","1"

"Magento\Checkout","1"
" -- Magento\Framework","759"

"Magento\Reports","1"
" -- Magento\Framework","553"
```
