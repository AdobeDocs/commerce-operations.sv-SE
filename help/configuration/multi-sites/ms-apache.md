---
title: Konfigurera flera webbplatser med Apache
description: Följ den här självstudiekursen för att konfigurera flera webbplatser med Apache.
source-git-commit: 5e072a87480c326d6ae9235cf425e63ec9199684
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 0%

---


# Konfigurera flera webbplatser med Apache

Vi antar att:

Om det behövs kopierar du den befintliga `index.php` startpunktsskript för webbplatsen eller butiksvyn och lägg till följande i det:

- Du arbetar på en utvecklingsmaskin (bärbar dator, virtuell dator osv.)

   Ytterligare uppgifter kan behövas för att driftsätta flera webbplatser i en hostingmiljö. kontakta din värdleverantör för mer information.

   Ytterligare uppgifter krävs för att konfigurera Adobe Commerce i molninfrastrukturen. När du har slutfört de uppgifter som beskrivs i det här avsnittet, se [Konfigurera flera webbplatser eller butiker](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) i _Guide för Commerce on Cloud Infrastructure_.

- Du använder en virtuell värd per webbplats; konfigurationsfilen för det virtuella värdsystemet är `/etc/httpd/httpd.conf`

   Olika versioner av Apache på olika operativsystem ställer in virtuella värdar på olika sätt. Läs [Apache-dokumentation](https://httpd.apache.org/docs/2.4/vhosts) eller en nätverksadministratör om du inte är säker på hur du konfigurerar en virtuell värd.

- Commerce-programvaran är installerad i `/var/www/html/magento2`
- Du har två andra webbplatser än standardwebbplatsen:

   - `french.mysite.mg` med webbplatskod `french` och butiksvykod `fr`
   - `german.mysite.mg` med webbplatskod `german` och butiksvykod `de`

## Vägkarta för att skapa flera webbplatser med Apache

Du kan konfigurera flera arkiv på följande sätt:

1. [Konfigurera webbplatser, butiker och butiksvyer](ms-admin.md) i Admin.
1. Skapa en [Virtuell värd för Apache](#step-2-create-apache-virtual-hosts) per Commerce-webbplats.

## Steg 1: Skapa webbplatser, butiker och butiksvyer i administratören

Se [Konfigurera flera webbplatser, butiker och butiksvyer i administratören](ms-admin.md).

## Steg 2: Skapa virtuella Apache-värdar

I det här avsnittet beskrivs hur du anger värden för `MAGE_RUN_TYPE` och `MAGE_RUN_CODE` med hjälp av servervariabeln Apache `SetEnvIf` i en virtuell värd.

Mer information om `SetEnvIf`, se:

- [Apache 2.2](https://httpd.apache.org/docs/2.2/mod/mod_setenvif.html)
- [Apache 2.4](https://httpd.apache.org/docs/2.4/mod/mod_setenvif.html)

**Skapa virtuella Apache-värdar**:

1. Som användare med `root` behörighet, öppna konfigurationsfilen för det virtuella värdsystemet i en textredigerare.

   Öppna till exempel `/etc/httpd/conf/httpd.conf`

1. Leta reda på avsnittet som börjar med `<VirtualHost *:80>`.
1. Skapa följande virtuella värdar efter befintliga virtuella värdar:

   ```conf
   <VirtualHost *:80>
      ServerName          mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          french.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "french"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   
   <VirtualHost *:80>
      ServerName          german.mysite.mg
      DocumentRoot        /var/www/html/magento2/pub/
      SetEnv MAGE_RUN_CODE "german"
      SetEnv MAGE_RUN_TYPE "website"
   </VirtualHost>
   ```

1. Spara ändringarna i `httpd.conf` och avsluta textredigeraren.
1. Starta om Apache:

   - CentOS: `service httpd restart`
   - Ubuntu: `service apache2 restart`

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
>- Ytterligare uppgifter kan behövas för att driftsätta flera webbplatser i en hostingmiljö. kontakta din värdleverantör för mer information.
>- Det krävs ytterligare uppgifter för att konfigurera Adobe Commerce för molninfrastruktur. se [Konfigurera flera olika Creative Cloud-webbplatser eller -butiker](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/configure-store/multiple-sites.html) i _Guide för Commerce on Cloud Infrastructure_.


### Felsökning

- Om de franska och tyska webbplatserna returnerar 404s men administratören läser in, måste du kontrollera att du har fyllt i [Steg 6: Lägg till butikskoden i bas-URL:en](ms-admin.md#step-6-add-the-store-code-to-the-base-url).
- Om alla URL-adresser returnerar 404s måste du starta om webbservern.
- Om administratören inte fungerar som den ska ska du kontrollera att du har konfigurerat dina virtuella värdar korrekt.
