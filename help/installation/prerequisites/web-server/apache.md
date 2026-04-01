---
title: Installera Apache för lokala distributioner
description: Lär dig hur du installerar och konfigurerar Apache för lokala Adobe Commerce-distributioner. Aktivera nödvändiga inställningar för moduler, omskrivningar och &grave;.htaccess&grave;.
feature: Install, Configuration
badgePaas: label="Lokalt" type="Informative" url="https://experienceleague.adobe.com/en/docs/commerce/user-guides/product-solutions" tooltip="Gäller endast Adobe Commerce lokala projekt."
exl-id: a9a394c9-389f-42ef-9029-dd22c979cfb8
source-git-commit: 352a71cb88ff38c0920201f49f1d7b889509fd61
workflow-type: tm+mt
source-wordcount: '1015'
ht-degree: 0%

---

# Installera Apache för lokala distributioner {#apache}

I den här guiden får du hjälp med att installera Apache för Adobe Commerce lokala distributioner och konfigurera Apache-inställningarna som Commerce kräver. Den innehåller delade Apache-krav och operativsystemsspecifika procedurer för Ubuntu och CentOS. Adobe rekommenderar att du följer konfigurationsinstruktionerna i den här handboken för att bevara både funktionaliteten och säkerheten i Commerce-programmet.

Adobe stöder Apache-versionerna som listas i [systemkraven](../../system-requirements.md) för din Adobe Commerce-version. Versioner som stöds varierar beroende på version. Apache kräver också en PHP-konfiguration som stöds. Relaterade PHP-krav finns i [PHP-inställningar](../php-settings.md).

Börja med det avsnitt som passar din miljö:

- Om Apache redan är installerat börjar du med [Granska Apache-krav](#review-apache-requirements).
- Om du behöver installera eller uppgradera Apache på Ubuntu går du till [Installera eller uppgradera Apache på Ubuntu](#installing-or-upgrading-apache-on-ubuntu).
- Om du behöver installera Apache på CentOS går du till [Installera Apache på CentOS](#installing-apache-on-centos).

## Granska Apache-krav

Uppfyll dessa krav på alla Apache-servrar som har Adobe Commerce som värd.

### Konfigurera obligatoriska direktiv

Ange `AllowEncodedSlashes` i serverkonfigurationen (globalt) eller i den virtuella värdkonfigurationen för att undvika avkodning av kodade snedstreck som kan orsaka problem för URL:er. Om du till exempel hämtar produkter med ett snedstreck i SKU via API:t, vill du inte att snedstrecket ska konverteras. Följande exempelblock är inte fullständigt och andra direktiv krävs.

```conf
<VirtualHost *:443>
  # Allow encoded slashes
  AllowEncodedSlashes NoDecode
</VirtualHost>
```

### Konfigurera återskrivningar och .htaccess {#apache-rewrites-and-htaccess}

Använd det här avsnittet om du vill aktivera Apache-omskrivning och konfigurera den [distribuerade `.htaccess` filen &#x200B;](https://httpd.apache.org/docs/current/howto/htaccess.html). Adobe Commerce använder serverskrivningar och `.htaccess` för att tillhandahålla katalognivåinstruktioner för Apache.

>[!IMPORTANT]
>
>Om du inte aktiverar de här inställningarna visas vanligtvis inga format i din butik eller administratör. Det kan också hindra Apache från att tillämpa Adobe Commerce-säkerhetsskydd som definieras i `.htaccess`.

1. Aktivera modulen för omskrivning av Apache:

   ```bash
   a2enmod rewrite
   ```

1. Aktivera programmet att använda den distribuerade konfigurationsfilen `.htaccess`.

   1. Redigera `/etc/apache2/sites-available/000-default.conf` på Ubuntu. Information om andra Apache-layouter eller om ytterligare parametrar krävs finns i [dokumentationen för Apache](https://httpd.apache.org/docs/current/mod/mod_rewrite.html) och i [dokumentationen för Apache-åtkomstkontroll](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).

   1. Lägg till eller uppdatera direktivet `AllowOverride` för den katalog där du tänker installera Adobe Commerce.

   Om du till exempel installerar Adobe Commerce i standardinställningen `docroot` lägger du till följande block i `000-default.conf`:

   ```conf
   <Directory "/var/www/html">
     AllowOverride All
   </Directory>
   ```

   >[!NOTE]
   >
   >Om du uppgraderade från en tidigare Apache-version söker du först efter ett befintligt `<Directory "/var/www/html">`- eller `<Directory "/var/www">`-block i `000-default.conf`. Om du installerar Adobe Commerce i en annan `docroot` ska du uppdatera det matchande `<Directory>`-blocket för den sökvägen.

1. Starta om Apache för att tillämpa ändringarna:

   ```bash
   service apache2 restart
   ```

### Installera nödvändiga moduler

Adobe Commerce kräver att följande Apache-moduler är installerade:

- [mod_deflate.c](https://httpd.apache.org/docs/2.4/mod/mod_deflate.html)
- [mod_expirres.c](https://httpd.apache.org/docs/2.4/mod/mod_expires.html)
- [mod_headers.c](https://httpd.apache.org/docs/2.4/mod/mod_headers.html)
- [mod_rewrite.c](https://httpd.apache.org/docs/2.4/mod/mod_rewrite.html)
- [mod_security.c](https://modsecurity.org)
- [mod_ssl.c](https://httpd.apache.org/docs/2.4/mod/mod_ssl.html)

## Kontrollera att Apache är installerat

Kontrollera att Apache är installerat och visa den aktuella versionen genom att ange:

```bash
apache2 -v
```

Resultatet visar information som liknar följande:

```text
Server version: Apache/<installed-version>
Server built: <build-date>
```

- Om Apache *inte* är installerat, se:
   - [Installera eller uppgradera Apache på Ubuntu](#installing-or-upgrading-apache-on-ubuntu)
   - [Installera Apache på CentOS](#installing-apache-on-centos)

## Installera eller uppgradera Apache på Ubuntu {#installing-or-upgrading-apache-on-ubuntu}

Installation och konfigurering av Apache i Ubuntu är en process i tre steg:

1. Installera programvaran.
1. Aktivera omskrivningar.
1. Ange `.htaccess` direktiv.

När du konfigurerar omskrivningar av Apache-servern måste du ange vilken typ av direktiv som kan användas i `.htaccess`, som programmet använder för att ange omskrivningsregler och säkerhetsskydd.

### Installera Apache på Ubuntu

1. Installera Apache om du inte redan har gjort det:

   ```bash
   apt-get -y install apache2
   ```

1. Verifiera installationen:

   ```bash
   apache2 -v
   ```

   Meddelanden som liknar följande för att bekräfta att installationen lyckades:

   ```text
   Server version: Apache/<installed-version>
   Server built: <build-date>
   ```

1. Fortsätt med nästa avsnitt.

   >[!NOTE]
   >
   >Även om Apache tillhandahålls som standard med Ubuntu, se följande avsnitt för att konfigurera det.

### Uppgradera Apache på Ubuntu

Om Apache redan är installerat och du använder en version som är tidigare än `2.4` uppgraderar du till Apache `2.4` eller till den senaste versionen som stöds av den Adobe Commerce-version som du har distribuerat. Se [systemkrav](../../system-requirements.md).

1. Uppdatera paketinformation:

   ```bash
   apt-get -y update
   ```

1. Lägg till en databas som innehåller en Apache-version som stöds för din miljö, om det behövs.

1. Installera eller uppgradera Apache:

   ```bash
   apt-get install -y apache2
   ```

   >[!NOTE]
   >
   >Om kommandot `apt-get install` inte fungerar på grund av att beroenden inte uppfylls, bör du läsa dokumentationen till operativsystemspaketet eller distributionssupportresurserna.

1. Verifiera installationen:

   ```bash
   apache2 -v
   ```

1. Kontrollera att den installerade versionen matchar den version som stöds för din Adobe Commerce-version i [systemkraven](../../system-requirements.md).

1. Aktivera [omskrivningar och `.htaccess` för Ubuntu](#enable-rewrites-and-htaccess-for-ubuntu).

### Aktivera omskrivning och .htaccess för Ubuntu

1. Öppna filen `/etc/apache2/sites-available/000-default.conf` för redigering:

   ```bash
   vim /etc/apache2/sites-available/000-default.conf
   ```

1. Leta reda på det block som börjar med:

   ```conf
   <Directory "/var/www/html">
   ```

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

1. Konfigurera Apache att använda modulen `mod_rewrite`:

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

>[!IMPORTANT]
>
>Om du inte aktiverar de här inställningarna visas vanligtvis inga format i din butik eller administratör. Det kan också hindra Apache från att tillämpa Adobe Commerce-säkerhetsskydd som definieras i `.htaccess`.

## Installera Apache på CentOS {#installing-apache-on-centos}

Installation och konfigurering av Apache i CentOS är en process i tre steg:

1. Installera programvaran
2. Aktivera omskrivning
3. Ange `.htaccess` direktiv.

När du konfigurerar omskrivningar av Apache-servern måste du ange vilken typ av direktiv som kan användas i `.htaccess`, som programmet använder för att ange omskrivningsregler och säkerhetsskydd.

### Installerar Apache

1. Installera Apache om du inte redan har gjort det.

   ```bash
   yum -y install httpd
   ```

1. Verifiera installationen:

   ```bash
   httpd -v
   ```

   Meddelanden som liknar följande för att bekräfta att installationen lyckades:

   ```text
   Server version: Apache/<installed-version>
   Server built: <build-date>
   ```

1. Fortsätt med nästa avsnitt.

   >[!NOTE]
   >
   >Även om Apache tillhandahålls som standard med CentOS läser du följande avsnitt för att konfigurera det.

### Aktivera omskrivning och .htaccess för CentOS

1. Öppna filen `/etc/httpd/conf/httpd.conf` för redigering:

   ```bash
   vim /etc/httpd/conf/httpd.conf
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
   >Föregående värden för `Order` kanske inte fungerar i alla fall. Mer information finns i [Apache-dokumentationen](https://httpd.apache.org/docs/2.4/mod/mod_authz_host.html#order).

1. Spara filen och avsluta textredigeraren.

1. Starta om Apache om du vill använda Apache-inställningarna.

   ```bash
   systemctl restart httpd
   ```

>[!IMPORTANT]
>
>Om du inte aktiverar de här inställningarna visas vanligtvis inga format i din butik eller administratör. Det kan också hindra Apache från att tillämpa Adobe Commerce-säkerhetsskydd som definieras i `.htaccess`.

## Lösa 403-fel (ej tillåtet)

Om du stöter på 403 Otillåtna fel när du försöker få åtkomst till webbplatsen kan du uppdatera din Apache-konfiguration eller din virtuella värdkonfiguration så att besökarna kan komma åt webbplatsen:

### Lös 403 Otillåtna fel för Apache

Använd något av [direktiven &#x200B;](https://httpd.apache.org/docs/2.4/howto/access.html) som krävs om du vill att webbplatsbesökare ska kunna komma åt din webbplats.

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
>Föregående värden för `Order` kanske inte fungerar i alla fall. Mer information finns i [Apache-dokumentationen](https://httpd.apache.org/docs/2.4/mod/mod_access_compat.html#order).
