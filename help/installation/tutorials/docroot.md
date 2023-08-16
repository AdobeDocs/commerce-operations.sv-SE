---
title: Förbättra säkerheten genom att ändra dokumentroten
description: Förhindra obehörig webbläsarbaserad åtkomst till Adobe Commerce eller Magento Open Source lokala filsystem.
feature: Install, Security
exl-id: aabe148d-00c8-4011-a629-aa5abfa6c682
source-git-commit: 32dd5005422b98923ce1bdf6c3fb3f55c2ec15bd
workflow-type: tm+mt
source-wordcount: '586'
ht-degree: 0%

---

# Förbättra säkerheten genom att ändra dokumentroten

I en standardinstallation med en Apache-webbserver installeras Adobe Commerce och Magento Open Source i standardwebbroten: `/var/www/html/magento2`.

The `magento2/` katalogen innehåller följande:

- `pub/`
- `setup/`
- `var/`

Ansökan kommer från `/var/www/html/magento2/pub`. Resten av filsystemet är känsligt eftersom det är tillgängligt via en webbläsare.
Ange webbroten på `pub/` -katalogen förhindrar besökare från att komma åt känsliga delar av filsystemet via en webbläsare.

I det här avsnittet beskrivs hur du ändrar Apache-dokumentroten för en befintlig instans för att hantera filer från `pub/` katalog, vilket är säkrare.

## En anteckning om nginx

Om du använder [nginx](../prerequisites/web-server/nginx.md) och [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) filen som finns i installationskatalogen. Du hanterar förmodligen redan filer från `pub/` katalog.

När den används i ett serverblock som definierar din plats, `nginx.conf.sample` konfigurationen åsidosätter serverns dokumentrotinställningar för att hantera filer från `pub/` katalog. Se till exempel den sista raden i följande konfiguration:

```conf
# /etc/nginx/sites-available/magento

upstream fastcgi_backend {
   server  unix:/run/php/php7.4-fpm.sock;
}

server {

         listen 80;
         server_name 192.168.33.10;
         set $MAGE_ROOT /var/www/html/magento2ce;
         include /var/www/html/magento2ce/nginx.conf.sample;
}
```

## Innan du börjar

För att slutföra den här självstudiekursen behöver du tillgång till en fungerande installation som körs på en LAMP-stack:

- Linux
- Apache (2.4+)
- MySQL (5.7+)
- PHP (7.4)
- Elasticsearch (7.x) eller OpenSearch (1.2)
- Adobe Commerce eller Magento Open Source (2.4+)

>[!NOTE]
>
>Se [Förutsättningar](../prerequisites/overview.md) och [Installationshandbok](../overview.md) för mer information.

## 1. Redigera serverkonfigurationen

Namnet på och platsen för den virtuella värdfilen beror på vilken version av Apache du kör. I det här exemplet visas namnet och platsen för den virtuella värdfilen på Apache v2.4.

1. Logga in på programservern.
1. Redigera din virtuella värdfil:

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. Lägg till sökvägen till `pub/` till `DocumentRoot` direktiv:

   ```conf
   <VirtualHost *:80>
   
            ServerAdmin webmaster@localhost
            DocumentRoot /var/www/html/magento2ce/pub
   
            ErrorLog ${APACHE_LOG_DIR}/error.log
            CustomLog ${APACHE_LOG_DIR}/access.log combined
   
            <Directory "/var/www/html">
                        AllowOverride all
            </Directory>
    </VirtualHost>
   ```

1. Starta om Apache:

   ```bash
   systemctl restart apache2
   ```

## 2. Uppdatera din bas-URL

Om du lade till ett katalognamn till serverns värdnamn eller IP-adress för att skapa bas-URL:en när du installerade programmet (till exempel `http://192.168.33.10/magento2`) måste du ta bort den.

>[!NOTE]
>
>Ersätt `192.168.33.10` med serverns värdnamn.

1. Logga in i databasen:

   ```bash
   mysql -u <user> -p
   ```

1. Ange den databas du skapade när du installerade programmet:

   ```shell
   use <database-name>
   ```

1. Uppdatera bas-URL:

   ```shell
   UPDATE core_config_data SET value='http://192.168.33.10' WHERE path='web/unsecure/base_url';
   ```

## 3. Uppdatera filen env.php.

Lägg till följande nod i `env.php` -fil.

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

Se [env.php reference](../../configuration/reference/config-reference-envphp.md) för mer information.

## 4. Växlingslägen

[Programlägen](../../configuration/bootstrap/application-modes.md), som innehåller `production` och `developer`, har utformats för att förbättra säkerheten och underlätta utvecklingen. Du bör växla till `developer` läge när du utökar eller anpassar programmet och växlar till `production` när du kör i en aktiv miljö.

Att växla mellan lägen är ett viktigt steg när du vill verifiera att serverkonfigurationen fungerar som den ska. Du kan växla mellan lägena med CLI-verktyget:

1. Gå till installationskatalogen.
1. Växla till `production` läge.

   ```bash
   bin/magento deploy:mode:set production
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Uppdatera webbläsaren och kontrollera att butiken visas korrekt.
1. Växla till `developer` läge.

   ```bash
   bin/magento deploy:mode:set developer
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Uppdatera webbläsaren och kontrollera att butiken visas korrekt.

## 5. Verifiera butiken

Gå till butiken i en webbläsare och kontrollera att allt fungerar.

1. Öppna en webbläsare och ange serverns värdnamn eller IP-adress i adressfältet. Exempel, `http://192.168.33.10`.

   I bilden nedan visas ett exempel på en butikssida. Om den visas på följande sätt har installationen lyckats!

   ![Storefront som verifierar en lyckad installation](../../assets/installation/install-success_store.png)

   Se [felsökningsavsnitt](https://support.magento.com/hc/en-us/articles/360032994352) om sidan visar 404 (Hittades inte) eller inte kan läsa in andra resurser som bilder, CSS och JS.

1. Försök att komma åt en programkatalog från en webbläsare. Lägg till katalognamnet i serverns värdnamn eller IP-adress i adressfältet:

   Om du ser ett 404-meddelande eller meddelandet&quot;Åtkomst nekad&quot; har du begränsat åtkomsten till filsystemet.

   ![Åtkomst nekad](../../assets/installation/access-denied.png)
