---
title: Apache
description: Följ de här stegen för att installera och konfigurera Apache-webbservern för lokala installationer av Adobe Commerce.
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---

# Apache

Adobe Commerce stöder Apache 2.4.x.

## Apache-obligatoriska direktiv

1. Ange `AllowEncodedSlashes` i serverkonfigurationen (globalt) eller i den virtuella värdkonfigurationen för att undvika avkodning av kodade snedstreck som kan orsaka problem för URL:er. Om du till exempel hämtar produkter med ett snedstreck i SKU via API:t, vill du inte att det ska konverteras. Exempelblocket är inte fullständigt och andra direktiv krävs.

   ```conf
   <VirtualHost *:443>
     # Allow encoded slashes
     AllowEncodedSlashes NoDecode
   </VirtualHost>
   ```

## Apache-skrivningar och åtkomst

I det här avsnittet beskrivs hur du aktiverar Apache 2.4-omskrivningar och anger en inställning för [distribuerad konfigurationsfil, `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html).

Adobe Commerce använder serveråterskrivningar och `.htaccess` för att ge katalognivåinstruktioner för Apache. Följande instruktioner finns även i alla andra avsnitt i det här avsnittet.

Använd det här avsnittet för att aktivera Apache 2.4-omskrivningar och ange en inställning för [distribuerad konfigurationsfil, `.htaccess`](https://httpd.apache.org/docs/current/howto/htaccess.html)

Adobe Commerce använder serveråterskrivningar och `.htaccess` för att ge katalognivåinstruktioner för Apache.

>[!NOTE]
>
>Om du inte aktiverar de här inställningarna visas vanligtvis inga format i din butik eller administratör.

1. Aktivera modulen för omskrivning av Apache:

   ```bash
   a2enmod rewrite
   ```

1. Så här aktiverar du programmet att använda den distribuerade `.htaccess` konfigurationsfilen, se riktlinjerna i [Dokumentation för Apache 2.4](https://httpd.apache.org/docs/current/mod/mod_rewrite.html).

   >[!TIP]
   >
   >I Apache 2.4 är serverns standardkonfigurationsfil `/etc/apache2/sites-available/000-default.conf`.

   Du kan till exempel lägga till följande i slutet av `000-default.conf`:

   ```terminal
   <Directory "/var/www/html">
       AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >Ibland kan ytterligare parametrar behövas. Mer information finns i [Dokumentation för Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

1. Om du har ändrat Apache-inställningarna startar du om Apache:

   ```bash
   service apache2 restart
   ```

   >[!NOTE]
   >
   >- Om du har uppgraderat från en tidigare Apache-version ska du först leta efter `<Directory "/var/www/html">` eller `<Directory "/var/www">` in `000-default.conf`.
   >- Du måste ändra värdet för `AllowOverride` i direktivet för den katalog som du vill installera Adobe Commerce eller Magento Open Source. Om du till exempel vill installera i webbserverdokumentet redigerar du direktivet i `<Directory /var/www>`.

>[!NOTE]
>
>Om du inte aktiverar de här inställningarna visas vanligtvis format som inte finns i storefront eller Admin.

## Nödvändiga moduler för Apache

Adobe Commerce kräver att följande Apache-moduler är installerade:

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expirres.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## Verifiera Apache-versionen

Kontrollera vilken Apache-version du kör genom att ange:

```bash
apache2 -v
```

Resultatet ser ut ungefär så här:

```terminal
Server version: Apache/2.4.04 (Ubuntu)
Server built: Jul 22 2020 14:35:32
```

- Om Apache *not* finns i:
   - [Installera eller uppgradera Apache på Ubuntu](#installing-apache-on-ubuntu)
   - [Installerar Apache på CentOS](#installing-apache-on-centos)

## Installera eller uppgradera Apache på Ubuntu

I följande avsnitt beskrivs hur du installerar eller uppgraderar Apache:

- Installera Apache
- Uppgradera till Apache 2.4 i Ubuntu för att använda PHP 7.4.

### Installerar Apache på Ubuntu

Installera standardversionen av Apache:

1. Installera Apache

   ```bash
   apt-get -y install apache2
   ```

1. Verifiera installationen.

   ```bash
   apache2 -v
   ```

   Resultatet ser ut ungefär så här:

   ```terminal
   Server version: Apache/2.4.18 (Ubuntu)
   Server built: 2020-04-15T18:00:57
   ```

1. Aktivera [skriver om och `.htaccess`](#apache-rewrites-and-htaccess).

### Uppgraderar Apache på Ubuntu

Uppgradera till Apache 2.4:

1. Lägg till `ppa:ondrej` databas med Apache 2.4:

   ```bash
   apt-get -y update
   ```

   ```bash
   apt-add-repository ppa:ondrej/apache2
   ```

   ```bash
   apt-get -y update
   ```

1. Installera Apache 2.4:

   ```bash
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >Om kommandot &quot;apt-get install&quot; misslyckas på grund av ofullständiga beroenden bör du kontakta en resurs som [https://askubuntu.com/](https://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa).

1. Verifiera installationen.

   ```bash
   apache2 -v
   ```

   Meddelanden som liknar följande bör visas:

   ```terminal
   Server version: Apache/2.4.10 (Ubuntu)
   Server built: Jul 22 2020 22:46:25
   ```

1. Aktivera [skriver om och `.htaccess`](#apache-rewrites-and-htaccess).

## Installerar Apache på CentOS

Adobe Commerce kräver omskrivning av Apache-servern. Du måste också ange vilken typ av direktiv som kan användas i `.htaccess`som programmet använder för att ange regler för omskrivning.

Installation och konfigurering av Apache är i stort sett en trestegsprocess: installera programmet, aktivera omskrivning och ange `.htaccess` direktiv.

### Installerar Apache

1. Installera Apache 2.4 om du inte redan har gjort det.

   ```bash
   yum -y install httpd
   ```

1. Verifiera installationen:

   ```bash
   httpd -v
   ```

   Meddelanden som liknar följande för att bekräfta att installationen lyckades:

   ```terminal
   Server version: Apache/2.4.40 (Unix)
   Server built: Oct 16 2020 14:48:21
   ```

1. Fortsätt med nästa avsnitt.

   >[!NOTE]
   >
   >Även om Apache 2.4 finns som standard med CentOS, se följande avsnitt för att konfigurera det.

### Aktivera omskrivning och .htaccess för CentOS

1. Öppna `/etc/httpd/conf/httpd.conf` fil för redigering:

   ```bash
   vim /etc/httpd/conf/httpd.conf`
   ```

1. Leta reda på det block som börjar med:

   ```conf
   <Directory "/var/www/html">
   ```

1. Ändra värdet för `AllowOverride` till `All`.

   Exempel:

   ```conf
   <Directory "/var/www/">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

   >[!NOTE]
   >
   >Föregående värden för `Order` kanske inte fungerar i alla fall. Mer information finns i dokumentationen för Apache ([2.4](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order)).

1. Spara filen och avsluta textredigeraren.

1. Starta om Apache om du vill använda Apache-inställningarna.

   ```bash
   service apache2 restart
   ```

>[!NOTE]
>
>Om du inte aktiverar de här inställningarna visas vanligtvis inga format i din butik eller administratör.

### Aktivera omskrivning och .htaccess för Ubuntu

1. Öppna `/etc/apache2/sites-available/default` fil för redigering:

   ```bash
   vim /etc/apache2/sites-available/default
   ```

1. Leta reda på det block som börjar med:

   `<Directory "/var/www/html">`

1. Ändra värdet för `AllowOverride` till `All`.

   Exempel:

   ```conf
   <Directory "/var/www/html">
     Options Indexes FollowSymLinks MultiViews
     AllowOverride All
     Order allow,deny
     Allow from all
   </Directory>
   ```

1. Spara filen och avsluta textredigeraren.

1. Konfigurera Apache att använda `mod_rewrite` modul:

   ```bash
   cd /etc/apache2/mods-enabled
   ```

   ```bash
   ln -s ../mods-available/rewrite.load
   ```

1. Starta om Apache för att tillämpa ändringarna:

   ```bash
   service apache2 restart
   ```

## Lösa 403-fel (ej tillåtet)

Om du stöter på 403 Otillåtna fel när du försöker få åtkomst till webbplatsen kan du uppdatera din Apache-konfiguration eller din virtuella värdkonfiguration så att besökarna kan komma åt webbplatsen:

### Lösning av 403 Otillåtna fel för Apache 2.4

Om du vill att webbplatsbesökare ska kunna komma åt din webbplats använder du något av [Kräv direktiv](https://httpd.apache.org/docs/2.4/howto/access.html).

Exempel:

```conf
<Directory "/var/www/">
  Options Indexes FollowSymLinks MultiViews
  AllowOverride All
  Order allow,deny
  Require all granted
</Directory>
```

>[!NOTE]
>
>Föregående värden för `Order` kanske inte fungerar i alla fall. Mer information finns i [Apache-dokumentation](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).
