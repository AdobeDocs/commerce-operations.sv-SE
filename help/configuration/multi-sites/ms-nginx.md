---
title: Konfigurera flera webbplatser med Nginx
description: Följ den här självstudiekursen för att konfigurera flera webbplatser med Nginx.
exl-id: f13926a2-182c-4ce2-b091-19c5f978f267
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '959'
ht-degree: 0%

---

# Konfigurera flera webbplatser med Nginx

Vi antar att:

- Du arbetar på en utvecklingsmaskin (bärbar dator, virtuell dator eller liknande).

  Ytterligare uppgifter kan behövas för att distribuera flera webbplatser i en värdmiljö. Kontakta din värdleverantör för mer information.

  Ytterligare uppgifter krävs för att konfigurera Adobe Commerce i molninfrastrukturen. När du har slutfört de uppgifter som beskrivs i det här avsnittet, se [Konfigurera flera webbplatser eller butiker](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) i _Guide för Commerce on Cloud Infrastructure_.

- Du godkänner flera domäner i en virtuell värdfil eller använder en virtuell värd per webbplats. Konfigurationsfilerna för den virtuella värden finns i `/etc/nginx/sites-available`.
- Du använder `nginx.conf.sample` tillhandahålls av Commerce med endast de ändringar som diskuteras i den här självstudiekursen.
- Commerce-programvaran är installerad i `/var/www/html/magento2`.
- Du har två andra webbplatser än standardwebbplatsen:

   - `french.mysite.mg` med webbplatskod `french` och butiksvykod `fr`
   - `german.mysite.mg` med webbplatskod `german` och butiksvykod `de`
   - `mysite.mg` är standardwebbplats och standardbutiksvy

>[!TIP]
>
>Se [Skapa webbplatser](ms-admin.md#step-2-create-websites) och [Skapa butiksvyer](ms-admin.md#step-4-create-store-views) om du vill ha hjälp med att hitta dessa värden.

Här följer en färdplan för hur du konfigurerar flera webbplatser med Nginx:

1. [Konfigurera webbplatser, butiker och butiksvyer](ms-admin.md) i Admin.
1. Skapa en [Nginx virtuell värd](#step-2-create-nginx-virtual-hosts)) för att mappa många webbplatser eller en Nginx virtuell värd per Commerce-webbplats (steg som beskrivs nedan).
1. Skicka värdena för [MAGE-variabler](ms-overview.md) `$MAGE_RUN_TYPE` och `$MAGE_RUN_CODE` till nginx med hjälp av Magento `nginx.conf.sample` (steg som beskrivs nedan).

   - `$MAGE_RUN_TYPE` kan vara antingen `store` eller `website`:

      - Använd `website` för att läsa in webbplatsen i butiken.
      - Använd `store` för att läsa in alla butiksvyer i butiken.

   - `$MAGE_RUN_CODE` är den unika kod för webbplats- eller butiksvyn som motsvarar `$MAGE_RUN_TYPE`.

1. Uppdatera bas-URL-konfigurationen för Commerce-administratören.

## Steg 1: Skapa webbplatser, butiker och butiksvyer i administratören

Se [Konfigurera flera webbplatser, butiker och butiksvyer i administratören](ms-admin.md).

## Steg 2: Skapa nya virtuella värdar

I det här steget beskrivs hur du läser in webbplatser i butiken. Du kan använda antingen webbplatser eller butiksvyer. Om du använder butiksvyer måste du justera parametervärdena därefter. Du måste slutföra uppgifterna i det här avsnittet som en användare med `sudo` behörighet.

Genom att bara använda en [nginx virtuell värdfil](#step-2-create-nginx-virtual-hosts)kan du göra din ursprungliga konfiguration enkel och ren. Genom att använda flera virtuella värdfiler kan du anpassa varje butik (och använda en anpassad plats för `french.mysite.mg` till exempel).

**Skapa en virtuell värd** (förenklad):

Den här konfigurationen utökas [nginx-konfiguration](../../installation/prerequisites/web-server/nginx.md).

1. Öppna en textredigerare och lägg till följande innehåll i en ny fil med namnet `/etc/nginx/sites-available/magento`:

   ```conf
   map $http_host $MAGE_RUN_CODE {
       default '';
       french.mysite.mg french;
       german.mysite.mg german;
   }
   
   server {
       listen 80;
       server_name mysite.mg french.mysite.mg german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Spara ändringarna i filerna och avsluta textredigeraren.
1. Verifiera serverkonfigurationen:

   ```bash
   nginx -t
   ```

1. Om det lyckas visas följande meddelande:

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Om fel visas kontrollerar du syntaxen för konfigurationsfilerna för det virtuella värdsystemet.

1. Skapa en symbolisk länk i dialogrutan `/etc/nginx/sites-enabled` katalog:

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/magento magento
   ```

Mer information om mappningsdirektivet finns i [nginx-dokumentation om kardirektivet](http://nginx.org/en/docs/http/ngx_http_map_module.html#map).


**Skapa flera virtuella värdar**:

1. Öppna en textredigerare och lägg till följande innehåll i en ny fil med namnet `/etc/nginx/sites-available/french.mysite.mg`:

   ```conf
   server {
       listen 80;
       server_name french.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE french;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Skapa en annan fil med namnet `german.mysite.mg` i samma katalog med följande innehåll:

   ```conf
   server {
       listen 80;
       server_name german.mysite.mg;
       set $MAGE_ROOT /var/www/html/magento2;
       set $MAGE_MODE developer;
       set $MAGE_RUN_TYPE website; #or set $MAGE_RUN_TYPE store;
       set $MAGE_RUN_CODE german;
       include /var/www/html/magento2/nginx.conf;
   }
   ```

1. Spara ändringarna i filerna och avsluta textredigeraren.
1. Verifiera serverkonfigurationen:

   ```bash
   nginx -t
   ```

1. Om det lyckas visas följande meddelande:

   ```terminal
   nginx: configuration file /etc/nginx/nginx.conf test is successful
   ```

   Om fel visas kontrollerar du syntaxen för konfigurationsfilerna för det virtuella värdsystemet.

1. Skapa symboliska länkar i `/etc/nginx/sites-enabled` katalog:

   ```bash
   cd /etc/nginx/sites-enabled
   ```

   ```bash
   ln -s /etc/nginx/sites-available/french.mysite.mg french.mysite.mg
   ```

   ```bash
   ln -s /etc/nginx/sites-available/german.mysite.mg german.mysite.mg
   ```

## Steg 3: Ändra nginx.conf.sample

>[!TIP]
>
>Redigera inte `nginx.conf.sample` fil; det är en viktig Commerce-fil som kan uppdateras med varje ny release. I stället kopierar du `nginx.conf.sample` , ändra namn på filen och redigera sedan den kopierade filen.

**Redigera PHP-startpunkten för huvudprogrammet**:

Ändra `nginx.conf.sample` fil**:

1. Öppna en textredigerare och granska `nginx.conf.sample` fil,`<magento2_installation_directory>/nginx.conf.sample`. Leta efter följande avsnitt:

   ```conf
   # PHP entry point for main application
   location ~ (index|get|static|report|404|503|health_check)\.php$ {
       try_files $uri =404;
       fastcgi_pass   fastcgi_backend;
       fastcgi_buffers 1024 4k;
   
       fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
       fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
       fastcgi_read_timeout 600s;
       fastcgi_connect_timeout 600s;
   
       fastcgi_index  index.php;
       fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
       include        fastcgi_params;
   }
   ```

1. Uppdatera `nginx.conf.sample` fil med följande två rader före programsatsen include:

   ```conf
   fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
   fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
   ```

Ett exempel på en uppdaterad PHP-startpunkt för huvudprogrammet ser ut så här:

```conf
# PHP entry point for main application

location ~ (index|get|static|report|404|503|health_check)\.php$ {
    try_files $uri =404;
    fastcgi_pass   fastcgi_backend;
    fastcgi_buffers 1024 4k;

    fastcgi_param  PHP_FLAG  "session.auto_start=off \n suhosin.session.cryptua=off";
    fastcgi_param  PHP_VALUE "memory_limit=1G \n max_execution_time=18000";
    fastcgi_read_timeout 600s;
    fastcgi_connect_timeout 600s;

    fastcgi_index  index.php;
    fastcgi_param  SCRIPT_FILENAME  $document_root$fastcgi_script_name;
    # START - Multisite customization
    fastcgi_param MAGE_RUN_TYPE $MAGE_RUN_TYPE;
    fastcgi_param MAGE_RUN_CODE $MAGE_RUN_CODE;
    # END - Multisite customization
    include        fastcgi_params;
}
```

## Steg 4: Uppdatera konfigurationen för bas-URL

Du måste uppdatera bas-URL:en för `french` och `german` webbplatser i Commerce Admin.

### Uppdatera bas-URL för fransk webbplats

1. Logga in på Commerce Admin och navigera till **Lager** > **Inställningar** > **Konfiguration** > **Allmänt** > **Webb**.
1. Ändra _konfigurationsomfång_ till `french` webbplats.
1. Expandera **Bas-URL** och uppdatera **Bas-URL** och **Bas länk-URL** värde till `http://french.magento24.com/`.
1. Expandera **Bas-URL:er (säkra)** och uppdatera **URL för säker bas** och **URL för säker baslänk** värde till `https://french.magento24.com/`.
1. Klicka **Spara konfiguration** och spara konfigurationsändringarna.

### Uppdatera bas-URL för tysk webbplats

1. Logga in på Commerce Admin och navigera till **Lager** > **Inställningar** > **Konfiguration** > **Allmänt** > **Webb**.
1. Ändra _konfigurationsomfång_ till `german` webbplats.
1. Expandera **Bas-URL** och uppdatera **Bas-URL** och **Bas länk-URL** värde till `http://german.magento24.com/`.
1. Expandera **Bas-URL:er (säkra)** och uppdatera **URL för säker bas** och **URL för säker baslänk** värde till `https://german.magento24.com/`.
1. Klicka **Spara konfiguration** och spara konfigurationsändringarna.

### Rensa cachen

Kör följande kommando för att rensa `config` och `full_page` cacher.

```bash
bin/magento cache:clean config full_page
```

## Verifiera platsen

Om du inte har ställt in DNS för butikernas URL:er måste du lägga till en statisk väg till värden i din `hosts` fil:

1. Hitta ditt operativsystem `hosts` -fil.
1. Lägg till den statiska vägen i formatet:

   ```conf
   <ip-address> french.mysite.mg
   <ip-address> german.mysite.mg
   ```

1. Gå till en av följande URL:er i webbläsaren:

   ```http
   http://mysite.mg/admin
   http://french.mysite.mg/frenchstoreview
   http://german.mysite.mg/germanstoreview
   ```

>[!INFO]
>
>- Ytterligare uppgifter kan behövas för att distribuera flera webbplatser i en värdmiljö. Kontakta din värdleverantör för mer information.
>- Ytterligare uppgifter krävs för att konfigurera Adobe Commerce för molninfrastruktur. Mer information finns [Konfigurera flera olika Creative Cloud-webbplatser eller -butiker](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) i _Guide för Commerce on Cloud Infrastructure_.

### Felsökning

- Om de franska och tyska webbplatserna returnerar 404s men administratören läser in, måste du kontrollera att du har fyllt i [Steg 6: Lägg till butikskoden i bas-URL:en](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- Om alla URL-adresser returnerar 404s måste du starta om webbservern.
- Om administratören inte fungerar som den ska ska du kontrollera att du har konfigurerat dina virtuella värdar korrekt.
