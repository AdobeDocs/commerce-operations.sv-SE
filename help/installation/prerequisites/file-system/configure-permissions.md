---
title: Konfigurera filägarskap och behörigheter
description: Följ de här stegen för att konfigurera filsystembehörigheter för lokala installationer av Adobe Commerce.
exl-id: 2410ee4f-978c-4b71-b3f6-0c042f9f4dc4
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 0%

---

# Konfigurera filägarskap och behörigheter

I det här avsnittet beskrivs hur du anger läs- och skrivbehörigheter för webbservergruppen innan du installerar Adobe Commerce. Detta är nödvändigt för att kommandoraden ska kunna skriva filer till filsystemet.

Proceduren du använder skiljer sig åt beroende på om du använder [delad värdtjänst](#set-permissions-for-one-user-on-shared-hosting) och har en användare eller om du använder en [privat server](#set-ownership-and-permissions-for-two-users) och har två användare.

## Ange behörigheter för en användare vid delad värdtjänst

I det här avsnittet beskrivs hur du anger förinstallationsbehörigheter om du loggar in på programservern som samma användare som kör webbservern. Den här typen av konfiguration är vanlig i delade värdmiljöer.

Så här anger du behörigheter innan du installerar programmet:

1. Logga in på programservern.
1. Använd ett filhanteringsprogram som tillhandahålls av din delade värdleverantör för att verifiera att skrivbehörigheter har angetts i följande kataloger:

   * `vendor` (Kompositör eller komprimerad arkivinstallation)
   * `app/etc`
   * `pub/static`
   * `var`
   * `generated`
   * Andra statiska resurser

1. Om du har kommandoradsåtkomst anger du följande kommandon i den ordning som visas:

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} +
   ```

   ```bash
   chmod u+x bin/magento
   ```

   Om du vill ange alla kommandon på en rad anger du följande under förutsättning att programmet är installerat i `/var/www/html/magento2`:

   ```bash
   cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod u+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod u+w {} + && chmod u+x bin/magento
   ```

1. Om du inte redan har gjort det ska du skaffa programmet på något av följande sätt:

   * [Metapaket för disposition](../../composer.md)
   * [Klona databasen (endast bidragsutvecklare)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

1. [Installera programmet](../../advanced.md) när du har angett ägarskap och behörigheter för filsystemet

>[!NOTE]
>
>Om du vill begränsa behörigheter ytterligare efter att du har installerat programmet kan du [konfigurera en mask](../../next-steps/set-umask.md).

## Ange ägarskap och behörigheter för två användare

I det här avsnittet beskrivs hur du ställer in ägarskap och behörigheter för din egen server eller en privat värdkonfiguration. I den här typen av konfiguration kan du *inte* logga in som, eller växla till, webbserveranvändaren. Du loggar vanligtvis in som en användare och kör webbservern som en annan användare.

Så här anger du ägarskap och behörigheter för ett tvåanvändarsystem:

Utför följande uppgifter i den ordning som visas:

* [Om den delade gruppen](#about-the-shared-group)
* [Skapa filsystemets ägare och ge användaren ett starkt lösenord](#create-the-file-system-owner-and-give-the-user-a-strong-password)
* [Hitta webbserverns användargrupp](#find-the-web-server-user-group)
* [Placera filsystemets ägare i webbservergruppen](#put-the-file-system-owner-in-the-web-server-group)
* [Skaffa programvaran](#get-the-software)
* [Ange ägarskap och behörigheter för den delade gruppen](#set-ownership-and-permissions-for-the-shared-group)

### Om den delade gruppen

Om du vill att webbservern ska kunna skriva filer och kataloger i filsystemet, men att filsystemets ägare ska behålla *ägarskap*, måste båda användarna finnas i samma grupp. Detta är nödvändigt för att båda användarna ska kunna dela åtkomst till filer (inklusive filer som skapats med Admin eller andra webbaserade verktyg).

I det här avsnittet beskrivs hur du skapar en ägare av ett filsystem och placerar användaren i webbservergruppen. Du kan använda ett befintligt användarkonto om du vill. Vi rekommenderar att användaren har ett starkt lösenord av säkerhetsskäl.

>[!NOTE]
>
>Gå till [Hitta webbserverns användargrupp](#find-the-web-server-user-group) om du tänker använda ett befintligt användarkonto.

### Skapa filsystemets ägare och ge användaren ett starkt lösenord

I det här avsnittet beskrivs hur du skapar filsystemets ägare. (filsystemets ägare är en annan term för kommandoradsanvändaren **.)

Om du vill skapa en användare på CentOS eller Ubuntu anger du följande kommando som en användare med `root`-behörighet:

```bash
adduser <username>
```

Om du vill ge användaren ett lösenord anger du följande kommando som en användare med `root`-behörighet:

```bash
passwd <username>
```

Följ instruktionerna på skärmen för att skapa ett lösenord för användaren.

>[!WARNING]
>
>Om du inte har `root`-behörighet på programservern kan du använda ett annat lokalt användarkonto. Kontrollera att användaren har ett starkt lösenord och fortsätt med [Placera filsystemägaren i webbservergruppen](#step-3-put-the-file-system-owner-in-the-web-servers-group).

Om du till exempel vill skapa en användare med namnet `magento_user` och ge användaren ett lösenord anger du:

```bash
sudo adduser magento_user
```

```bash
sudo passwd magento_user
```

>[!WARNING]
>
>Eftersom syftet med att skapa den här användaren är att tillhandahålla extra säkerhet, måste du skapa ett [starkt lösenord](https://en.wikipedia.org/wiki/Password_strength).

### Hitta webbserverns användargrupp

Så här hittar du webbserverns användargrupp:

* CentOS:

  ```bash
  grep -E -i '^user|^group' /etc/httpd/conf/httpd.conf
  ```

  eller

  ```bash
  grep -Ei '^user|^group' /etc/httpd/conf/httpd.conf
  ```

Vanligtvis är både användar- och gruppnamnet `apache`.

* Ubuntu: `ps aux | grep apache` för att hitta Apache-användaren och sedan `groups <apache user>` för att hitta gruppen.

Vanligtvis är både användarnamnet och gruppnamnet `www-data`.

### Placera filsystemets ägare i webbservergruppen

Om du vill placera filsystemägaren i webbserverns primära grupp (med det typiska Apache-gruppnamnet för CentOS och Ubuntu) anger du följande kommando som en användare med `root`-behörighet:

* CentOS: `usermod -a -G apache <username>`
* Ubuntu: `usermod -a -G www-data <username>`

>[!NOTE]
>
>Alternativen för `-a -G` är viktiga eftersom de lägger till `apache` eller `www-data` som en *sekundär* grupp i användarkontot, vilket bevarar användarens *primära* grupp. Om du lägger till en sekundär grupp till ett användarkonto kan [begränsa filägarskap och behörigheter](#set-ownership-and-permissions-for-two-users) för att säkerställa att medlemmar i en delad grupp bara har åtkomst till vissa filer.

Så här lägger du till användaren `magento_user` i den primära gruppen `apache` i CentOS:

```bash
sudo usermod -a -G apache magento_user
```

Bekräfta att användaren är medlem i webbservergruppen genom att ange följande kommando:

```bash
groups magento_user
```

I följande exempelresultat visas användarens primära (`magento`) och sekundära (`apache`) grupper.

```bash
magento_user : magento_user apache
```

>[!NOTE]
>
>Vanligtvis är användarnamnet och det primära gruppnamnet samma.

Starta om webbservern för att slutföra åtgärden:

* Ubuntu: `service apache2 restart`
* CentOS: `service httpd restart`

### Skaffa programvaran

Om du inte redan har gjort det ska du skaffa programmet på något av följande sätt:

* [Metapaket för disposition](../../composer.md)
* [Klona databasen (endast bidragsutvecklare)](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

### Ange ägarskap och behörigheter för den delade gruppen

Så här anger du ägarskap och behörigheter innan du installerar programmet:

1. Logga in på programservern som, eller växla till, ägare av filsystemet.
1. Ange följande kommandon i den ordning som visas:

   ```bash
   cd <app_root>
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} +
   ```

   ```bash
   find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} +
   ```

   ```bash
   chown -R :<web server group> .
   ```

   ```bash
   chmod u+x bin/magento
   ```

Om du vill ange alla kommandon på en rad anger du följande under förutsättning att programmet är installerat i `/var/www/html/magento2` och webbservergruppens namn är `apache`:

```bash
cd /var/www/html/magento2 && find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && chown -R :apache . && chmod u+x bin/magento
```

Om filsystembehörigheterna inte har angetts korrekt och inte kan ändras av filsystemets ägare, kan du ange kommandot som en användare med `root`-behörighet:

```bash
cd /var/www/html/magento2 && sudo find var generated vendor pub/static pub/media app/etc -type f -exec chmod g+w {} + && sudo find var generated vendor pub/static pub/media app/etc -type d -exec chmod g+ws {} + && sudo chown -R :apache . && sudo chmod u+x bin/magento
```

## Växla till filsystemets ägare

När du har utfört de andra uppgifterna i det här avsnittet, anger du något av följande kommandon för att växla till den användaren:

* Ubuntu: `su <username>`
* CentOS: `su - <username>`

Exempel:

```bash
su magento_user
```
