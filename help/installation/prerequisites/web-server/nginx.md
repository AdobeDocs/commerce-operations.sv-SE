---
title: Nginx
description: Följ de här stegen för att installera och konfigurera Nginx-webbservern för lokala installationer av Adobe Commerce och Magento Open Source.
source-git-commit: 8f05fb6fc212c2b3fda80457bbf27ecf16fb1194
workflow-type: tm+mt
source-wordcount: '1180'
ht-degree: 0%

---


# Nginx

Adobe Commerce har stöd för nginx 1.18 (eller [senaste huvudversionen](https://nginx.org/en/linux_packages.html#mainline)). Du måste också installera den senaste versionen av `php-fpm`.

Installationsanvisningarna varierar beroende på vilket operativsystem du använder. Se [PHP](../php-settings.md) för information.

## Ubuntu

I följande avsnitt beskrivs hur du installerar Adobe Commerce och Magento Open Source 2.x på Ubuntu med nginx, PHP och MySQL.

### Installera nginx

```bash
sudo apt -y install nginx
```

Du kan också [skapa nginx från källa](https://www.armanism.com/blog/install-nginx-on-ubuntu)

När vi har slutfört följande avsnitt och installerat programmet använder vi en exempelkonfigurationsfil för att [konfigurera nginx](#configure-nginx).

### Installera och konfigurera php-fpm

Adobe Commerce och Magento Open Source kräver flera [PHP-tillägg](../php-settings.md) att fungera som det ska. Förutom dessa tillägg måste du även installera och konfigurera `php-fpm` om du använder nginx.

Installera och konfigurera `php-fpm`:

1. Installera `php-fpm` och `php-cli`:

   ```bash
   apt-get -y install php7.2-fpm php7.2-cli
   ```

   >[!NOTE]
   >
   >Det här kommandot installerar den senaste tillgängliga versionen av PHP 7.2.X. Se [systemkrav](../../system-requirements.md) för PHP-versioner som stöds.

1. Öppna `php.ini` filer i en redigerare:

   ```bash
   vim /etc/php/7.2/fpm/php.ini
   ```

   ```bash
   vim /etc/php/7.2/cli/php.ini
   ```

1. Redigera båda filerna så att de matchar följande rader:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Vi rekommenderar att du anger minnesgränsen till 2 G när du testar Adobe Commerce och Magento Open Source. Se [Nödvändiga PHP-inställningar](../php-settings.md) för mer information.

1. Spara och avsluta redigeraren.

1. Starta om `php-fpm` tjänst:

   ```bash
   systemctl restart php7.2-fpm
   ```

### Installera och konfigurera MySQL

Se [MySQL](../database/mysql.md) för mer information.

### Installera och konfigurera

Det finns flera sätt att ladda ned Adobe Commerce och Magento Open Source, bland annat:

* [Hämta Composer-metapaketet](../../composer.md)

* [Klona Git-databasen](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

I det här exemplet visas en Composer-baserad installation med kommandoraden.

1. Som [ägare av filsystem](../file-system/overview.md)loggar du in på programservern.

1. Byt till webbserverns dokumentkatalog eller en katalog som du har konfigurerat som ett virtuellt värddokument. I det här exemplet använder vi Ubuntu-standarden `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. Installera Composer globalt. Composer krävs för att uppdatera beroenden innan Adobe Commerce eller Magento Open Source installeras:

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Skapa ett Composer-projekt med metapaketet Magento Open Source eller Adobe Commerce.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Ange [autentiseringsnycklar](../authentication-keys.md). Dina _publik nyckel_ är ditt användarnamn, din _privat nyckel_ är ditt lösenord.

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

1. Installera från [kommandorad](../../advanced.md). I det här exemplet antas att installationskatalogen har ett namn `magento2ee`, `db-host` finns på samma dator (`localhost`) och `db-name`, `db-user`och `db-password` är alla `magento`:

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=magento \
   --db-user=magento \
   --db-password=magento \
   --backend-frontname=admin \
   --admin-firstname=admin \
   --admin-lastname=admin \
   --admin-email=admin@admin.com \
   --admin-user=admin \
   --admin-password=admin123 \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1 \
   --search-engine=elasticsearch7 \
   --elasticsearch-host=es-host.example.com \
   --elasticsearch-port=9200
   ```

1. Växla till utvecklarläge:

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Konfigurera nginx

Vi rekommenderar att du konfigurerar nginx med `nginx.conf.sample` konfigurationsfilen som finns i installationskatalogen och det nya virtuella värdsystemet.

Dessa instruktioner förutsätter att du använder Ubuntu-standardplatsen för det virtuella värdsystemet nginx (till exempel `/etc/nginx/sites-available`) och Ubuntu standarddocroot (till exempel `/var/www/html`) kan du dock ändra de här platserna så att de passar din miljö.

1. Skapa en ny virtuell värd för din plats:

   ```bash
   vim /etc/nginx/sites-available/magento
   ```

1. Lägg till följande konfiguration:

   ```conf
   upstream fastcgi_backend {
     server  unix:/run/php/php7.2-fpm.sock;
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
   >The `include` -direktivet måste peka på exempelkonfigurationsfilen nginx i installationskatalogen.

1. Ersätt `www.magento-dev.com` med ditt domännamn. Detta måste matcha den bas-URL som du angav när du installerade Adobe Commerce eller Magento Open Source.

1. Spara och avsluta redigeraren.

1. Aktivera det nya virtuella värdsystemet genom att skapa en länk till det i `/etc/nginx/sites-enabled` katalog:

   ```bash
   ln -s /etc/nginx/sites-available/magento /etc/nginx/sites-enabled
   ```

1. Kontrollera att syntaxen är korrekt:

   ```bash
   nginx -t
   ```

1. Starta om nginx:

   ```bash
   systemctl restart nginx
   ```

### Verifiera installationen

Öppna en webbläsare och navigera till platsens bas-URL till [verifiera installationen](../../next-steps/verify.md).

## CentOS 7

I följande avsnitt beskrivs hur du installerar Adobe Commerce och Magento Open Source 2.x i CentOS 7 med nginx, PHP och MySQL.

### Installera nginx

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

När du har slutfört följande avsnitt och installerat programmet använder vi en exempelkonfigurationsfil för att konfigurera nginx.

### Installera och konfigurera php-fpm

Adobe Commerce och Magento Open Source kräver flera [PHP](../php-settings.md) tillägg för att fungera korrekt. Förutom dessa tillägg måste du även installera och konfigurera `php-fpm` om du använder nginx.

1. Installera `php-fpm`:

   ```bash
   yum -y install php70w-fpm
   ```

1. Öppna `/etc/php.ini` i en redigerare.

1. Avkommentera `cgi.fix_pathinfo` rad och ändra värdet till `0`.

1. Redigera filen så att den matchar följande rader:

   ```conf
   memory_limit = 2G
   max_execution_time = 1800
   zlib.output_compression = On
   ```

   >[!NOTE]
   >
   >Vi rekommenderar att du anger minnesgränsen till 2 G när du testar Adobe Commerce eller Magento Open Source. Se [Nödvändiga PHP-inställningar](../php-settings.md) för mer information.

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

1. Skapa en katalog för PHP-sessionssökvägen och ändra ägaren till `apache` användare och grupp:

   ```bash
   mkdir -p /var/lib/php/session/
   ```

   ```bash
   chown -R apache:apache /var/lib/php/
   ```

1. Skapa en katalog för PHP-sessionssökvägen och ändra ägaren till `apache` användare och grupp:

   ```bash
   mkdir -p /run/php-fpm/
   ```

   ```bash
   chown -R apache:apache /run/php-fpm/
   ```

1. Starta `php-fpm` och konfigurera den så att den startar vid start:

   ```bash
   systemctl start php-fpm
   ```

   ```bash
   systemctl enable php-fpm
   ```

1. Verifiera att `php-fpm` tjänsten körs:

   ```bash
   netstat -pl | grep php-fpm.sock
   ```

### Installera och konfigurera MySQL

Se [MySQL](..//database/mysql.md) för mer information.

### Installera och konfigurera

Det finns flera sätt att ladda ned Adobe Commerce och Magento Open Source, bland annat:

* [Hämta Composer-metapaketet](../../composer.md)

* [Klona Git-databasen](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

I det här exemplet visas en Composer-baserad installation med kommandoraden.

1. Som [ägare av filsystem](../file-system/overview.md)loggar du in på programservern.

1. Byt till webbserverns dokumentkatalog eller en katalog som du har konfigurerat som ett virtuellt värddokument. I det här exemplet använder vi Ubuntu-standarden `/var/www/html`.

   ```bash
   cd /var/www/html
   ```

1. Installera Composer globalt. Composer krävs för att uppdatera beroenden innan Adobe Commerce eller Magento Open Source installeras:

   ```bash
   curl -sS https://getcomposer.org/installer | sudo php -- --install-dir=/usr/bin --filename=composer
   ```

1. Skapa ett Composer-projekt med metapaketet Magento Open Source eller Adobe Commerce.

   **Magento Open Source**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-community-edition <install-directory-name>
   ```

   **Adobe Commerce**

   ```bash
   composer create-project --repository=https://repo.magento.com/ magento/project-enterprise-edition <install-directory-name>
   ```

   Ange [autentiseringsnycklar](../authentication-keys.md). Dina _publik nyckel_ är ditt användarnamn, din _privat nyckel_ är ditt lösenord.

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

1. Installera från [kommandorad](../../advanced.md). I det här exemplet antas att installationskatalogen har ett namn `magento2ee`, `db-host` finns på samma dator (`localhost`) och `db-name`, `db-user`och `db-password` är alla `magento`:

   ```bash
   bin/magento setup:install \
   --base-url=http://localhost/magento2ee \
   --db-host=localhost \
   --db-name=magento \
   --db-user=magento \
   --db-password=magento \
   --backend-frontname=admin \
   --admin-firstname=admin \
   --admin-lastname=admin \
   --admin-email=admin@admin.com \
   --admin-user=admin \
   --admin-password=admin123 \
   --language=en_US \
   --currency=USD \
   --timezone=America/Chicago \
   --use-rewrites=1
   ```

1. Växla till utvecklarläge:

   ```bash
   cd /var/www/html/magento2/bin
   ```

   ```bash
   ./magento deploy:mode:set developer
   ```

### Konfigurera nginx

Vi rekommenderar att du konfigurerar nginx med `nginx.conf.sample` konfigurationsfilen som finns i installationskatalogen och det nya virtuella värdsystemet.

Dessa instruktioner förutsätter att du använder CentOS-standardplatsen för det virtuella värdsystemet (till exempel `/etc/nginx/conf.d`) och standarddokumentrot (till exempel `/usr/share/nginx/html`) kan du dock ändra de här platserna så att de passar din miljö.

1. Skapa en ny virtuell värd för din plats:

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
   >The `include` -direktivet måste peka på exempelkonfigurationsfilen nginx i installationskatalogen.

1. Ersätt `www.magento-dev.com` med ditt domännamn.

1. Spara och avsluta redigeraren.

1. Kontrollera att syntaxen är korrekt:

   ```bash
   nginx -t
   ```

1. Starta om nginx:

   ```bash
   systemctl restart nginx
   ```

### Konfigurera SELinux och Fireworks

SELinux är aktiverat som standard i CentOS 7. Använd följande kommando för att se om det körs:

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

Öppna en webbläsare och navigera till platsens bas-URL till [verifiera installationen](../../next-steps/verify.md).
