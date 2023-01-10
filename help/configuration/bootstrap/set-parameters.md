---
title: Ange värdet för bootstrap-parametrar
description: Lär dig hur du ställer in bootstrap-parametrar för Commerce-programmet.
source-git-commit: 0d106b36f479ecf2eda3fecf6740b28d4b6793eb
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Bootstrap-parametrar

I det här avsnittet visas hur du anger värden för startparametrar för Commerce-program. Se [Översikt över programinitiering och -start](initialization.md).

I följande tabell beskrivs bootstrap-parametrarna som du kan ange:

| Bootstrap-parameter | Beskrivning |
| ------------------- | -------------------------------------------- |
| MAGE_DIRS | Anger anpassade katalog- och URL-sökvägar |
| MAGE_PROFILER | Aktiverar beroendediagram och HTML-profilering |

>[!INFO]
>
>- Alla bootstrap-parametrar finns inte dokumenterade.
>- Nu anger du programläge (utvecklare, standard, produktion) med [`magento deploy:mode:set {mode}`](../cli/set-mode.md) -kommando.


## Ange parametrar med en miljövariabel

I det här avsnittet beskrivs hur du anger värden för bootstrap-parametrar med hjälp av systemvariabler.

### Ange programläge

Du kan ange bootstrap-variabler som systemomfattande systemvariabler, vilket gör att alla processer kan använda dem.

Du kan till exempel använda `MAGE_PROFILER` systemmiljövariabel för att ange ett läge enligt följande:

```terminal
MAGE_PROFILER={firebug|csv|<custom value>}
```

Ange variabeln med ett gränssnittsspecifikt kommando. Eftersom skal har olika syntax bör du använda en referens som [unix.stackexchange.com][unix-stackx].

Exempel på Bash-skal för CentOS:

```bash
export MAGE_PROFILER=firebug
```

>[!INFO]
>
>Om en `PHP Fatal error` visas i webbläsaren när du har angett ett profileringsvärde startar du om webbservern. Orsaken kan vara PHP-bytekodscachning, som cachelagrar bytekoder och PHP-klassökvägar.

## Ange parametrar för Apache eller Nginx

I det här avsnittet beskrivs hur du anger läge för antingen Apache eller Nginx.

### Nginx-inställning

Se [Nginx-exempelkonfiguration] på _GitHub_.

### Apache.htaccess-inställning

Ett sätt att ange programläge är genom att redigera `.htaccess`. På så sätt behöver du inte ändra inställningarna för Apache.

Du kan ändra `.htaccess` på någon av följande platser, beroende på din startpunkt för Commerce-programmet:

- `<magento_root>/.htaccess`
- `<magento_root>/pub/.htaccess`

**Så här anger du en variabel**:

1. Öppna någon av de föregående filerna i en textredigerare och lägg till eller ta bort kommentaren till den önskade inställningen.

   Du kan till exempel ange en [läge](application-modes.md)avkommentera följande:

   ```conf
   #   SetEnv MAGE_PROFILER firebug
   ```

1. Ange värdet för `MAGE_PROFILER` till något av följande:

   ```terminal
   firebug
   csvfile
   <custom value>
   ```

1. Spara ändringarna i `.htaccess`; du behöver inte starta om Apache för att ändringen ska börja gälla.

### Apache-inställning

Webbservern Apache har stöd för att ställa in programläge med `mod_env` direktiv.

Apache `mod_env` -direktivet skiljer sig något åt i [Apache version 2.2] och [Apache version 2.4].

De procedurer som följer visar hur du ställer in programläget i en virtuell Apache-värd. Detta är inte det enda sättet att använda `mod_env` direktiv, Mer information finns i dokumentationen för Apache.

>[!TIP]
>
>I följande avsnitt förutsätts att du redan har konfigurerat din virtuella värd. Om du inte har det, bör du kontakta en resurs som [den här självstudiekursen om DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-ubuntu-14-04-lts).

**Ange en bootstrap-variabel för Apache i Ubuntu**:

1. Som användare med `root` behörighet, öppna konfigurationsfilen för det virtuella värdsystemet i en textredigerare.

   Om din virtuella värd till exempel har ett namn `my.magento`,

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
>I det här avsnittet förutsätts att du redan har konfigurerat din virtuella värd. Om du inte har det, bör du kontakta en resurs som [den här självstudiekursen om DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-set-up-apache-virtual-hosts-on-centos-6).

**Ange en bootstrap-variabel för Apache i CentOS**:

1. Som användare med `root` behörighet, öppna `/etc/httpd/conf/httpd.conf` i en textredigerare.

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

<!-- link definitions -->

[Apache version 2.2]: https://httpd.apache.org/docs/2.2/mod/mod_env.html#setenv
[Apache version 2.4]: https://httpd.apache.org/docs/2.4/mod/mod_env.html#setenv
[Nginx-exempelkonfiguration]: https://github.com/magento/magento2/blob/2.4/nginx.conf.sample#L16
[unix-stackx]: https://unix.stackexchange.com/questions/117467/how-to-permanently-set-environmental-variables
