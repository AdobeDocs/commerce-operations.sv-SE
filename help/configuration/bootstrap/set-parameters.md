---
title: Ange värdet för bootstrap-parametrar
description: Lär dig hur du ställer in bootstrap-parametrar för Commerce.
exl-id: 4e1e4e5e-e1bc-49a5-8a2a-2e6b91ca9175
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '559'
ht-degree: 1%

---

# Bootstrap-parametrar

I det här avsnittet visas hur du ställer in värden för startparametrar för Commerce-program. Se [Översikt över programinitiering och -start](initialization.md).

I följande tabell beskrivs bootstrap-parametrarna som du kan ange:

| Bootstrap-parameter | Beskrivning |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | Anger anpassade katalog- och URL-sökvägar |
| MAGE_PROFILER | Aktiverar beroendediagram och HTML-profilering |

>[!INFO]
>
>- Alla bootstrap-parametrar finns inte dokumenterade.
>- Du anger nu programläge (utvecklare, standard, produktion) med kommandot [`magento deploy:mode:set {mode}`](../cli/set-mode.md).

## Ange parametrar med en miljövariabel

I det här avsnittet beskrivs hur du anger värden för bootstrap-parametrar med hjälp av systemvariabler.

### Ange programläge

Du kan ange bootstrap-variabler som systemomfattande systemvariabler, vilket gör att alla processer kan använda dem.

Du kan till exempel använda systemmiljövariabeln `MAGE_PROFILER` för att ange ett läge enligt följande:

```
MAGE_PROFILER={firebug|csv|<custom value>}
```

Ange variabeln med ett gränssnittsspecifikt kommando. Eftersom skal har olika syntax bör du läsa en referens som [unix.stackexchange.com](https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables).

Exempel på Bash-skal för CentOS:

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>Om `PHP Fatal error` visas i webbläsaren när du har angett ett profileringsvärde startar du om webbservern. Orsaken kan vara PHP-bytekodscachning, som cachelagrar bytekoder och PHP-klassökvägar.

## Ange parametrar för Apache eller Nginx

I det här avsnittet beskrivs hur du anger läge för antingen Apache eller Nginx.

### Nginx-inställning

Se [Nginx-exempelkonfigurationen](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16) på _GitHub_.

### Apache.htaccess-inställning

Ett sätt att ange programläge är att redigera `.htaccess`. På så sätt behöver du inte ändra inställningarna för Apache.

Du kan ändra `.htaccess` på följande platser, beroende på startpunkten till Commerce-programmet:

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**Så här anger du en variabel**:

1. Öppna någon av de föregående filerna i en textredigerare och lägg till eller ta bort kommentaren till den önskade inställningen.

   Om du till exempel vill ange ett [läge](application-modes.md) avkommenterar du följande:

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. Ange värdet för `MAGE_PROFILER` till något av följande:

   ```
   firebug
   csvfile
   <custom value>
   ```

1. Spara ändringarna i `.htaccess`. Du behöver inte starta om Apache för att ändringen ska börja gälla.

### Apache-inställning

Apache-webbservern stöder inställning av programläge med `mod_env` direktiv.

Apache `mod_env`-direktivet skiljer sig något åt i [Apache version 2.2](https://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv) och [Apache version 2.4](https://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv).

De procedurer som följer visar hur du ställer in programläget i en virtuell Apache-värd. Det här är inte det enda sättet att använda `mod_env`-direktiv. Mer information finns i Apache-dokumentationen.

>[!TIP]
>
>I följande avsnitt förutsätts att du redan har konfigurerat din virtuella värd. Om du inte har det kan du titta på en resurs som [den här självstudiekursen för DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts).

**Så här anger du en bootstrap-variabel för Apache på Ubuntu**:

1. Som användare med `root`-behörighet öppnar du konfigurationsfilen för det virtuella värdsystemet i en textredigerare.

   Om din virtuella värd till exempel har namnet `my.magento`,

   - Apache 2.4: `vim /etc/apache2/sites-available/my.magento.conf`
   - Apache 2.2: `vim /etc/apache2/sites-available/my.magento`

1. Lägg till följande rad var som helst i konfigurationen av det virtuella värdsystemet:

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   Exempel:

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. Spara ändringarna och avsluta textredigeraren.
1. Aktivera ditt virtuella värdsystem om du inte redan har gjort det:

   ```bash
   a2ensite <virtual host config file name>
   ```

   Exempel:

   ```bash
   a2ensite my.magento.conf
   ```

1. Starta om webbservern när du har angett läget:

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

>[!TIP]
>
>I det här avsnittet förutsätts att du redan har konfigurerat din virtuella värd. Om du inte har det kan du titta på en resurs som [den här självstudiekursen för DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6).

**Så här anger du en bootstrap-variabel för Apache i CentOS**:

1. Som användare med `root`-behörighet öppnar du `/etc/httpd/conf/httpd.conf` i en textredigerare.

1. Lägg till följande rad var som helst i konfigurationen av det virtuella värdsystemet:

   ```conf
   SetEnv "<variable name>" "<variable value>"
   ```

   Exempel:

   ```conf
   SetEnv "MAGE_PROFILER" "firebug"
   ```

1. Spara ändringarna och avsluta textredigeraren.

1. Starta om webbservern när du har angett läget:

   - Ubuntu: `service apache2 restart`
   - CentOS: `service httpd restart`

