---
title: Förbättra säkerheten genom att ändra dokumentroten
description: Förhindra obehörig webbläsarbaserad åtkomst till Adobe Commerce lokala filsystem.
feature: Install, Security
exl-id: aabe148d-00c8-4011-a629-aa5abfa6c682
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '578'
ht-degree: 0%

---

# Förbättra säkerheten genom att ändra dokumentroten

I en standardinstallation med en Apache-webbserver installeras Adobe Commerce i standardwebbroten: `/var/www/html/magento2`.

Katalogen `magento2/` innehåller följande:

- `pub/`
- `setup/`
- `var/`

Programmet hanteras från `/var/www/html/magento2/pub`. Resten av filsystemet är känsligt eftersom det är tillgängligt via en webbläsare.
Om du ställer in webbroten på katalogen `pub/` hindras webbplatsbesökare från att komma åt känsliga områden i filsystemet från en webbläsare.

I det här avsnittet beskrivs hur du ändrar Apache-dokumentroten för en befintlig instans så att filer från katalogen `pub/` kan hanteras, vilket är säkrare.

## En anteckning om nginx

Om du använder [nginx](../prerequisites/web-server/nginx.md) och filen [`nginx.conf.sample`](https://github.com/magento/magento2/blob/2.4/nginx.conf.sample) som ingår i installationskatalogen, hanterar du förmodligen redan filer från katalogen `pub/`.

När konfigurationen `nginx.conf.sample` används i ett serverblock som definierar platsen åsidosätter den serverns docroot-inställningar för att hantera filer från katalogen `pub/`. Se till exempel den sista raden i följande konfiguration:

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
- Adobe Commerce (2.4+)

>[!NOTE]
>
>Mer information finns i [Förutsättningar](../prerequisites/overview.md) och [Installationshandboken](../overview.md).

## 1. Redigera serverkonfigurationen

Namnet på och platsen för den virtuella värdfilen beror på vilken version av Apache du kör. I det här exemplet visas namnet och platsen för den virtuella värdfilen på Apache v2.4.

1. Logga in på programservern.
1. Redigera din virtuella värdfil:

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. Lägg till sökvägen till din `pub/`-katalog i direktivet `DocumentRoot`:

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

Lägg till följande nod i filen `env.php`.

```conf
'directories' => [
    'document_root_is_pub' => true
]
```

Mer information finns i referensen [env.php](../../configuration/reference/config-reference-envphp.md).

## 4. Växlingslägen

[Programlägen](../../configuration/bootstrap/application-modes.md), som innehåller `production` och `developer`, är utformade för att förbättra säkerheten och underlätta utvecklingen. Som namnen tyder på bör du växla till läget `developer` när du utökar eller anpassar programmet och växla till läget `production` när du kör i en live-miljö.

Att växla mellan lägen är ett viktigt steg när du vill verifiera att serverkonfigurationen fungerar som den ska. Du kan växla mellan lägena med CLI-verktyget:

1. Gå till installationskatalogen.
1. Växla till läget `production`.

   ```bash
   bin/magento deploy:mode:set production
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Uppdatera webbläsaren och kontrollera att butiken visas korrekt.
1. Växla till läget `developer`.

   ```bash
   bin/magento deploy:mode:set developer
   ```

   ```bash
   bin/magento cache:flush
   ```

1. Uppdatera webbläsaren och kontrollera att butiken visas korrekt.

## 5. Verifiera butiken

Gå till butiken i en webbläsare och kontrollera att allt fungerar.

1. Öppna en webbläsare och ange serverns värdnamn eller IP-adress i adressfältet. Exempel: `http://192.168.33.10`.

   I bilden nedan visas ett exempel på en butikssida. Om den visas på följande sätt har installationen lyckats!

   ![Storefront som verifierar en lyckad installation](../../assets/installation/install-success_store.png)

   Se [felsökningsavsnittet](https://support.magento.com/hc/en-us/articles/360032994352) om sidan visar 404 (Hittades inte) eller inte kan läsa in andra resurser som bilder, CSS och JS.

1. Försök att komma åt en programkatalog från en webbläsare. Lägg till katalognamnet i serverns värdnamn eller IP-adress i adressfältet:

   Om du ser ett 404-meddelande eller meddelandet&quot;Åtkomst nekad&quot; har du begränsat åtkomsten till filsystemet.

   ![Åtkomst nekad](../../assets/installation/access-denied.png)
