---
title: Installera Nginx för lokala distributioner
description: Lär dig hur du installerar och konfigurerar Nginx-webbservern för lokala Adobe Commerce-distributioner. Konfigurera PHP-FPM och din virtuella värd.
feature: Install, Configuration
badgePaas: label="Lokalt" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gäller endast Adobe Commerce lokala projekt."
exl-id: 041ddb9d-868e-4021-9388-1c9ea11bfd8f
source-git-commit: 352a71cb88ff38c0920201f49f1d7b889509fd61
workflow-type: tm+mt
source-wordcount: '1430'
ht-degree: 0%

---

# Installera Nginx för lokala distributioner {#nginx}

I den här guiden får du hjälp med att installera Nginx för Adobe Commerce lokala distributioner och konfigurera de Nginx-inställningar som Commerce kräver. Det innehåller operativsystemsspecifika procedurer för Ubuntu och CentOS, tillsammans med vägledning för konfiguration av PHP-FPM. Adobe rekommenderar att du följer konfigurationsinstruktionerna i den här handboken för att bevara både funktionaliteten och säkerheten i Commerce-programmet.

Adobe stöder de Nginx-versioner som anges i [systemkraven](../../system-requirements.md) för din Adobe Commerce-version. Versioner som stöds varierar beroende på version. Nginx kräver också en PHP-FPM-konfiguration som stöds. Relaterade PHP-krav finns i [PHP](../php-settings.md).

## Installera på Ubuntu

Använd det här avsnittet för att installera Adobe Commerce i Ubuntu med Nginx, PHP och MySQL.

### Installera Nginx

```bash
sudo apt -y install nginx
```

Du kan även [skapa Nginx från källa](https://www.armanism.com/blog/install-nginx-on-ubuntu).

När du har slutfört följande avsnitt och installerat programmet använder du exempelkonfigurationsfilen för att [konfigurera Nginx](#configure-nginx). Den här rekommenderade konfigurationen bevarar både funktionaliteten och säkerheten för Commerce-programmet.

### Installera och konfigurera PHP-FPM

Adobe Commerce kräver flera [PHP-tillägg](../php-settings.md) för att fungera korrekt. Utöver dessa tillägg måste du även installera och konfigurera tillägget `php-fpm` om du använder Nginx.

Installera och konfigurera `php-fpm`:

1. Installera paketen `php-fpm` och `php-cli` för den PHP-version som stöds av din Adobe Commerce-version. I Ubuntu följer paketnamnen vanligtvis det här mönstret:

   ```bash
   apt-get -y install php<php-version>-fpm php<php-version>-cli
   ```

   >[!NOTE]
   >
   >Ersätt `<php-version>` med den PHP-delversion som stöds som listas i [systemkraven](../../system-requirements.md) för den Adobe Commerce-version som du installerar. Använd samma värde i filsökvägar, tjänstnamn och socketsökväg i följande steg.

1. Öppna `php.ini`-filerna i en redigerare:

   ```bash
   vim /etc/php/<php-version>/fpm/php.ini
   ```

   ```bash
   vim /etc/php/<php-version>/cli/php.ini
   ```

1. Redigera båda filerna så att de matchar följande rader:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe rekommenderar att du anger minnesgränsen till 2 GB när du testar Adobe Commerce. Mer information finns i [Nödvändiga PHP-inställningar](../php-settings.md).

1. Spara och avsluta redigeraren.

1. Starta om tjänsten `php-fpm`:

   ```bash
   systemctl restart php<php-version>-fpm
   ```

### Installera och konfigurera MySQL

Mer information finns i [MySQL](../database/mysql.md).

### Installera Adobe Commerce

Du kan ladda ned Adobe Commerce på flera sätt:

* [Hämta Composer-metapaketet](../../composer.md)

* [Klona Git-databasen](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

I det här exemplet visas en Composer-baserad installation med kommandoraden.

1. Logga in på programservern som [filsystemsägare](../file-system/overview.md).

1. Byt till webbserverns dokumentkatalog eller en katalog som du har konfigurerat som ett virtuellt värddokument. I det här exemplet använder vi Ubuntu-standardvärdet `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. Installera Composer globalt. Composer krävs för att uppdatera beroenden innan Adobe Commerce installeras:

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Skapa ett Composer-projekt med Adobe Commerce metapaket.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Ange dina [autentiseringsnycklar](../authentication-keys.md) när du uppmanas till detta. Din _offentliga nyckel_ är ditt användarnamn. Din _privata nyckel_ är ditt lösenord.

1. Ange läs- och skrivbehörighet för webbservergruppen innan du installerar programmet. Detta är nödvändigt för att kommandoraden ska kunna skriva filer till filsystemet.

   ```bash
   cd /var/www/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :www-data . # Ubuntu
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. Installera från [kommandoraden](../../advanced.md). I det här exemplet antas att installationskatalogen har namnet `magento2ee` och att databasvärden finns på samma dator (`localhost`):

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=<db-name> \
   --db-user=<db-user> \
   --db-password=<db-password> \
   --backend-frontname=<backend-uri> \
   --admin-firstname=<admin-first-name> \
   --admin-lastname=<admin-last-name> \
   --admin-email=<admin-email> \
   --admin-user=<admin-user> \
   --admin-password=<admin-password> \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1 \
   --search-engine=<search-engine-value> \
   --<search-engine-host-parameter>=search-host.example.com \
   --<search-engine-port-parameter>=9200
   ```

   >[!NOTE]
   >
   >Använd värdet `--search-engine` och matchande alternativ för värd/port som krävs för den Adobe Commerce-version som du installerar. För tidigare versioner än 2.4.6 använder du `elasticsearch7` med `--elasticsearch-*`-alternativen för Elasticsearch 7 eller OpenSearch. För version 2.4.6 och senare använder du sökmotorvärdet och motsvarande CLI-alternativ som stöds i den versionen.

1. Växla till utvecklarläge:

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Konfigurera Nginx

Adobe rekommenderar att du konfigurerar Nginx med hjälp av konfigurationsfilen `nginx.conf.sample` som finns i installationskatalogen och konfigurationen av det virtuella Nginx-värdsystemet för att bevara både funktioner och säkerhet för Commerce-programmet.

>[!IMPORTANT]
>
>Filen `nginx.conf.sample` innehåller nödvändiga programroutningsregler och säkerhetshärjande regler. Det begränsar till exempel körning av skadliga skript som överförts till servern. Om du inte använder den här filen eller ändrar dess regler, ansvarar du för att implementera likvärdiga säkerhetskontroller i din anpassade Nginx-konfiguration.

Dessa instruktioner förutsätter att du använder Ubuntu-standardplatsen för det virtuella Nginx-värdsystemet, till exempel `/etc/nginx/sites-available`, och Ubuntu-standarddokumentroten, till exempel `/var/www/html`. Du kan ändra de här platserna så att de passar din miljö.

1. Skapa ett nytt virtuellt värdsystem för din plats:

   ```bash
   vim /etc/nginx/sites-available/magento
   ```

1. Lägg till följande konfiguration:

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php/php<php-version>-fpm.sock;
   }
   
   server {
   
     listen 80;
     server_name www.magento-dev.com;
     set $MAGE_ROOT /var/www/html/magento2;
     include /var/www/html/magento2/nginx.conf.sample;
   }
   ```

   >[!NOTE]
   >
   >Direktivet `include` måste peka på exempelkonfigurationsfilen nginx i installationskatalogen.

1. Ersätt `www.magento-dev.com` med ditt domännamn. Detta måste matcha den bas-URL som du angav när du installerade Adobe Commerce.

1. Spara och avsluta redigeraren.

1. Aktivera det nya virtuella värdsystemet genom att skapa en länk till det i katalogen `/etc/nginx/sites-enabled`:

   ```bash
   ln -s /etc/nginx/sites-available/magento /etc/nginx/sites-enabled
   ```

1. Kontrollera att syntaxen är korrekt:

   ```bash
   nginx -t
   ```

1. Starta om Nginx:

   ```bash
   systemctl restart nginx
   ```

### Verifiera installationen

Kontrollera installationen genom att öppna en webbläsare och navigera till platsens bas-URL. Mer information finns i [Verifiera installationen](../../next-steps/verify.md).

## Installera i CentOS 7

Använd det här avsnittet för att installera Adobe Commerce i CentOS 7 med Nginx, PHP och MySQL.

### Installera Nginx

```bash
yum -y install epel-release
```

```bash
yum -y install nginx
```

När installationen är klar startar du nginx och konfigurerar det så att det startar vid start:

```bash
systemctl start nginx
```

```bash
systemctl enable nginx
```

När du har slutfört följande avsnitt och installerat programmet använder du en exempelkonfigurationsfil för att konfigurera Nginx.

### Installera och konfigurera PHP-FPM

Adobe Commerce kräver flera [PHP](../php-settings.md)-tillägg för att fungera korrekt. Utöver dessa tillägg måste du även installera och konfigurera tillägget `php-fpm` om du använder Nginx.

1. Installera `php-fpm`:

   ```bash
   yum -y install <php-fpm-package>
   ```

1. Öppna filen `/etc/php.ini` i en redigerare.

   >[!NOTE]
   >
   >Installera det paket som innehåller `php-fpm` för den PHP-version som stöds av den Adobe Commerce-version som du installerar. Paketnamnen varierar beroende på databas och operativsystem. Se [systemkrav](../../system-requirements.md).

1. Avkommentera raden `cgi.fix_pathinfo` och ändra värdet till `0`.

1. Redigera filen så att den matchar följande rader:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Adobe rekommenderar att du anger minnesgränsen till 2 GB när du testar Adobe Commerce. Mer information finns i [Nödvändiga PHP-inställningar](../php-settings.md).

1. Avkommentera sessionssökvägskatalogen och ange sökvägen:

   ```conf
   session.save_path = "/var/lib/php/session"
   ```

1. Spara och avsluta redigeraren.

1. Öppna `/etc/php-fpm.d/www.conf` i en redigerare.

1. Redigera filen så att den matchar följande rader:

   ```conf
   user = nginx
   group = nginx
   listen = /run/php-fpm/php-fpm.sock
   listen.owner = nginx
   listen.group = nginx
   listen.mode = 0660
   ```

1. Avkommentera miljöraderna:

   ```conf
   env[HOSTNAME] = $HOSTNAME
   env[PATH] = /usr/local/bin:/usr/bin:/bin
   env[TMP] = /tmp
   env[TMPDIR] = /tmp
   env[TEMP] = /tmp
   ```

1. Spara och avsluta redigeraren.

1. Skapa en katalog för PHP-sessionssökvägen och ändra ägaren till användaren och gruppen `nginx`:

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R nginx:nginx /var/lib/php/
   ```

1. Skapa en katalog för PHP-FPM-socketen och ändra ägaren till användaren och gruppen `nginx`:

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R nginx:nginx /run/php-fpm/
   ```

1. Starta tjänsten `php-fpm` och konfigurera den så att den startar vid start:

   ```bash
   systemctl start php-fpm
   ```

   ```bash
   systemctl enable php-fpm
   ```

1. Kontrollera att tjänsten `php-fpm` körs:

   ```bash
   netstat -pl | grep php-fpm.sock
   ```

### Installera och konfigurera MySQL

Mer information finns i [MySQL](../database/mysql.md).

### Installera Adobe Commerce

Du kan ladda ned Adobe Commerce på flera sätt:

* [Hämta Composer-metapaketet](../../composer.md)

* [Klona Git-databasen](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository)

I det här exemplet visas en Composer-baserad installation med kommandoraden.

1. Logga in på programservern som [filsystemsägare](../file-system/overview.md).

1. Byt till webbserverns dokumentkatalog eller en katalog som du har konfigurerat som ett virtuellt värddokument. I det här exemplet använder du CentOS-standardvärdet `/usr/share/nginx/html`.

   ```bash
   cd /usr/share/nginx/html
   ```

1. Installera Composer globalt. Composer krävs för att uppdatera beroenden innan Adobe Commerce installeras:

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Skapa ett Composer-projekt med Adobe Commerce metapaket.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Ange dina [autentiseringsnycklar](../authentication-keys.md) när du uppmanas till detta. Din _offentliga nyckel_ är ditt användarnamn. Din _privata nyckel_ är ditt lösenord.

1. Ange läs- och skrivbehörighet för webbservergruppen innan du installerar programmet. Detta är nödvändigt för att kommandoraden ska kunna skriva filer till filsystemet.

   ```bash
   cd /usr/share/nginx/html/<magento install directory>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :nginx . # CentOS
   ```

   ```bash
   chmod u+x bin/magento
   ```

1. Installera från [kommandoraden](../../advanced.md). I det här exemplet antas att installationskatalogen har namnet `magento2ee` och att databasvärden finns på samma dator (`localhost`):

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=<db-name> \
   --db-user=<db-user> \
   --db-password=<db-password> \
   --backend-frontname=<backend-uri> \
   --admin-firstname=<admin-first-name> \
   --admin-lastname=<admin-last-name> \
   --admin-email=<admin-email> \
   --admin-user=<admin-user> \
   --admin-password=<admin-password> \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1
   ```

1. Växla till utvecklarläge:

   ```bash
   cd /usr/share/nginx/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Konfigurera Nginx

Vi rekommenderar att du konfigurerar Nginx med hjälp av filen `nginx.conf.sample` i installationskatalogen och med konfigurationen för det virtuella Nginx-värdsystemet.

>[!IMPORTANT]
>
>Filen `nginx.conf.sample` innehåller nödvändiga programroutningsregler och säkerhetshärjande regler. Det begränsar till exempel körning av skadliga skript som överförts till servern. Om du inte använder den här filen eller ändrar dess regler, ansvarar du för att implementera likvärdiga säkerhetskontroller i din anpassade Nginx-konfiguration.

Dessa instruktioner förutsätter att du använder CentOS-standardplatsen för det virtuella Nginx-värdsystemet, till exempel `/etc/nginx/conf.d`, och standarddokumentroten, till exempel `/usr/share/nginx/html`. Du kan ändra de här platserna så att de passar din miljö.

1. Skapa ett nytt virtuellt värdsystem för din plats:

   ```bash
   vim /etc/nginx/conf.d/magento.conf
   ```

1. Lägg till följande konfiguration:

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php-fpm/php-fpm.sock;
   }
   
   server {
   
     listen 80;
     server_name www.magento-dev.com;
     set $MAGE_ROOT /usr/share/nginx/html/magento2;
     include /usr/share/nginx/html/magento2/nginx.conf.sample;
   }
   ```

   >[!NOTE]
   >
   >Direktivet `include` måste peka på exempelkonfigurationsfilen nginx i installationskatalogen.

1. Ersätt `www.magento-dev.com` med ditt domännamn.

1. Spara och avsluta redigeraren.

1. Kontrollera att syntaxen är korrekt:

   ```bash
   nginx -t
   ```

1. Starta om Nginx:

   ```bash
   systemctl restart nginx
   ```

### Konfigurera SELinux och firewalld

SELinux är aktiverat som standard i CentOS 7. Använd följande kommando för att bekräfta att det körs:

```bash
sestatus
```

Så här konfigurerar du SELinux och firewall:

1. Installera hanteringsverktygen för SELinux:

   ```bash
   yum -y install policycoreutils-python
   ```

1. Kör följande kommandon för att ändra säkerhetskontexten för installationskatalogen:

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/app/etc(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/var(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/media(/.*)?'
   ```

   ```bash
   semanage fcontext -a -t httpd_sys_rw_content_t '/usr/share/nginx/html/magento2/pub/static(/.*)?'
   ```

   ```bash
   restorecon -Rv '/usr/share/nginx/html/magento2/'
   ```

1. Installera brandväggspaketet:

   ```bash
   yum -y install firewalld
   ```

1. Starta brandväggen och konfigurera den så att den startar vid start:

   ```bash
   systemctl start firewalld
   ```

   ```bash
   systemctl enable firewalld
   ```

1. Kör följande kommandon för att öppna portar för HTTP och HTTPS så att du kan komma åt bas-URL:en från en webbläsare:

   ```bash
   firewall-cmd --permanent --add-service=http
   ```

   ```bash
   firewall-cmd --permanent --add-service=https
   ```

   ```bash
   firewall-cmd --reload
   ```

### Verifiera installationen

Kontrollera installationen genom att öppna en webbläsare och navigera till platsens bas-URL. Mer information finns i [Verifiera installationen](../../next-steps/verify.md).
