---
title: Underhållslägesalternativ för uppgradering
description: 'Skapa en anpassad sida för underhållsläge som kunderna ser på Adobe Commerce eller Magento Open Source i butiken medan du utför en uppgradering. '
source-git-commit: bbc412f1ceafaa557d223aabfd4b2a381d6ab04a
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---


# Alternativ för underhållsläge vid uppgradering

I det här avsnittet beskrivs hur du kan skapa en anpassad underhållssida som visas för användare medan ditt Magento-program uppgraderas. Det är valfritt att skapa en anpassad sida, men vi rekommenderar att du gör det eftersom webbplatsen är tillgänglig under en del av uppgraderingen.

Om du skapar en anpassad sida som användare kan omdirigeras till, förhindras åtkomst till webbplatsen och dessutom informeras användarna om att webbplatsen genomgår underhåll.

>[!NOTE]
>
>Du måste utföra uppgifterna i det här avsnittet som en användare med `root` behörighet. Det går inte att ange anpassade underhållssidor i utvecklarläge.

## Skapa den anpassade underhållssidan

Om du vill skapa en underhållssida och dirigera om den skapar du först en underhållssida med namnet:

- Apache: `<web server docroot>/maintenance.html`
- nginx: `<magento_root>/maintenance.html`

Lägg till följande innehåll:

```html
<!DOCTYPE html>
<html>
<head>
<title>Temporarily Offline</title>
<meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
<style>
h1
{ font-size: 50px; }

body
{ text-align:center; font: 20px Helvetica, sans-serif; color: #333; }

</style>
</head>
<body>

# Temporarily offline

<p>We're down for a short time to perform maintenance on our site to give you the best possible experience. Check back soon!</p>
</body>
</html>
```

## Anpassad underhållssida för Apache

I det här avsnittet beskrivs hur du skapar en anpassad underhållssida och hur du omdirigerar trafik till den.

Exemplet i det här avsnittet visar hur du ändrar följande filer, som är ett sätt att konfigurera underhållssidan:

- Apache 2.4: `/etc/apache2/sites-available/000-default.conf`
- Apache 2.2: `/etc/apache2/sites-available/default` (Ubuntu) `/etc/httpd/conf/httpd.conf` (CentOS)

Så här omdirigerar du trafik till en anpassad underhållssida:

1. Uppdatera Apache-konfigurationen så här:

   - Omdirigera all trafik till underhållssidan
   - Tillåtslista vissa IP-adresser så att en administratör kan uppgradera Magento.

   Följande exempel tillåtslista 192.0.2.110.

   Lägg till följande i slutet av konfigurationsfilen för Apache:

   ```terminal
   RewriteEngine On
   RewriteCond %{REMOTE_ADDR} !^192\.0\.2\.110
   RewriteCond %{DOCUMENT_ROOT}/maintenance.html -f
   RewriteCond %{DOCUMENT_ROOT}/maintenance.enable -f
   RewriteCond %{SCRIPT_FILENAME} !maintenance.html
   RewriteRule ^.*$ /maintenance.html [R=503,L]
   ErrorDocument 503 /maintenance.html
   Header Set Cache-Control "max-age=0, no-store"
   ```

1. Starta om Apache:

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

1. Ange följande kommando:

   ```bash
   touch <web server docroot>/maintenance.enable
   ```

1. [Uppgradera systemet](../implementation/perform-upgrade.md).
1. Testa webbplatsen för att kontrollera att den fungerar som den ska.
1. När uppgraderingen är klar tar du bort `maintenance.enable`.

## Anpassad underhållssida för nginx

I det här avsnittet beskrivs hur du skapar en anpassad underhållssida och hur du omdirigerar trafik till den.

Så här omdirigerar du trafik till en anpassad underhållssida:

1. Använd en textredigerare för att öppna [nginx](https://glossary.magento.com/nginx) konfigurationsfil som innehåller serverblocket.
1. Lägg till följande i serverblocket (`server` endast visas för tydlighet, lägg inte till ett andra serverblock).

   Följande tillåtslista IP-adressen 192.0.2.110 och 192.0.2.115 för på ett system där Magento är installerat i `/var/www/html/magento2`:

   ```conf
   server {
        listen 80;
        set $MAGE_ROOT /var/www/html/magento2;
   
        set $maintenance off;
   
        if (-f $MAGE_ROOT/maintenance.enable) {
            set $maintenance on;
        }
   
        if ($remote_addr ~ (192.0.2.110|192.0.2.115)) {
            set $maintenance off;
        }
   
        if ($maintenance = on) {
            return 503;
        }
   
        location /maintenance {
        }
   
        error_page 503 @maintenance;
   
        location @maintenance {
        root $MAGE_ROOT;
        rewrite ^(.*)$ /maintenance.html break;
    }
   
        include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Ange följande kommando:

   ```bash
   touch <magento_root>/maintenance.enable
   ```

1. Läs in nästa konfiguration igen:

   ```bash
   service nginx reload
   ```

1. [Uppgradera systemet](../implementation/perform-upgrade.md).
1. Testa webbplatsen för att kontrollera att den fungerar som den ska.
1. När uppgraderingen är klar tar du bort eller byter namn `maintenance.enable`
1. Läs in nästa konfiguration igen:

   ```bash
   service nginx reload
   ```
