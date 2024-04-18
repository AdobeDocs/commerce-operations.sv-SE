---
title: Klona exempeldata i Git-databaser
description: Följ de här stegen för att installera exempeldata för Adobe Commerce genom att klona Git-databaser.
exl-id: 748eee30-2821-457d-9c1c-62ede8bc0510
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 0%

---

# Klona exempeldata i Git-databaser

I det här avsnittet beskrivs hur du klonar och lägger till exempeldata om du klonade GitHub-databasen i Magento Open Source. Den här metoden är endast avsedd för utvecklare som bidrar till utvecklingen (det vill säga utvecklare som tänker bidra till kodbasen Magento Open Source).

Om du inte är en bidragsgivare väljer du ett av de andra alternativen som visas i innehållsförteckningen till vänster på sidan.

Utvecklare kan använda den här metoden för att installera exempeldata *endast* om följande är sant:

* Du använder Magento Open Source
* Du [klonade GitHub-databasen](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

>[!WARNING]
>
>Du kan använda exempeldata med `develop` gren (mer aktuell) eller en frisläppt gren (till exempel `2.4` (stabilare). Vi rekommenderar att du använder en frisläppt gren eftersom den är stabilare. Om du bidrar med kod till databasen och behöver den senaste koden använder du `develop` gren. Oavsett vilken gren du väljer måste du [klona](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) den motsvarande grenen i GitHub-databasen i Magento Open Source. Exempeldata för `develop` grenen kan användas *endast* med Magento Open Source `develop` gren.

## Klona exempeldatabasen

I det här avsnittet beskrivs hur du installerar exempeldata genom att klona databasen med exempeldata. Du kan klona exempeldatabasen på något av följande sätt:

* Klona med [SSH-protokoll](#clone-with-ssh)
* Klona med [HTTPS-protokoll](#clone-with-https)

### Klona med SSH

Så här klonar du GitHub-databasen med exempeldata med SSH-protokollet:

1. I en webbläsare går du till [exempeldatalager](https://github.com/magento/magento2-sample-data).
1. Klicka på bredvid namnet på grenen **SSH** från listan.
1. Klicka **Kopiera till Urklipp**

   I bilden nedan visas ett exempel.

   ![Klona GitHub-databasen med SSH](../../assets/installation/install_mage2_clone-ssh.png)

1. Byt till webbserverns dokumentrotkatalog.

   Vanligtvis är det för Ubuntu `/var/www` och för CentOS `/var/www/html`.

1. Retur `git clone` och klistra in värdet som du fick tidigare.

   Ett exempel följer:

   ```bash
   git clone git@github.com:magento/magento2-sample-data.git
   ```

1. Vänta tills databasen har klonats på servern.

   >[!NOTE]
   >
   >Om följande fel visas kontrollerar du att [delade SSH-nyckeln](https://docs.github.com/articles/generating-ssh-keys/) med GitHub:<br>

   ```terminal
   Cloning into 'magento2'...
   Permission denied (publickey).
   fatal: The remote end hung up unexpectedly
   ```

1. Se till att du checkar ut den gren i exempeldatalagret som motsvarar den gren du använde från huvuddelen `magento2` databas.

   Exempel:

   Om du använde `2.4-develop` grenen Sample Data i Magento Open Source GitHub-databasen ska `2.4-develop`.

   Om du vill checka ut rätt gren kör du följande kommando från exempeldatalagrets rotkatalog (förutsatt att du behöver `2.4-develop` gren):

   ```bash
   git checkout 2.4-develop
   ```

1. Ändra till `<app_root>`.
1. Ange följande kommando för att skapa symboliska länkar mellan filerna som du klonade så att exempeldata fungerar som de ska:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

1. Vänta tills kommandot har slutförts.

1. Se [Ange behörigheter och ägarskap för filsystemet](#set-file-system-ownership-and-permissions).

1. Kör följande kommando:

   ```bash
   bin/magento setup:upgrade
   ```

### Klona med HTTPS

Så här klonar du GitHub-databasen med exempeldata med HTTPS-protokollet:

1. I en webbläsare går du till [exempeldatalager](https://github.com/magento/magento2-sample-data).
1. Till höger på sidan, under **klona URL** fält, klicka **HTTPS**.
1. Klicka **Kopiera till Urklipp**.

   I bilden nedan visas ett exempel.

   ![Klona GitHub-databasen med HTTPS](../../assets/installation/install_mage2_clone-https.png)

1. Byt till webbserverns dokumentrotkatalog.

   Vanligtvis är det för Ubuntu `/var/www` och för CentOS `/var/www/html`.

1. Retur `git clone` och klistra in värdet som du fick tidigare.

   Ett exempel följer:

   ```bash
   git clone https://github.com/magento/magento2-sample-data.git
   ```

1. Vänta tills databasen har klonats på servern.
1. Se till att du checkar ut den gren i exempeldatalagret som motsvarar den gren du använde från huvuddelen `magento2` databas.

   Exempel:

   Om du använde `2.4-develop` grenen Sample Data i Magento Open Source GitHub-databasen ska `2.4-develop`.

   Om du vill checka ut rätt gren kör du följande kommando från exempeldatalagrets rotkatalog (förutsatt att du behöver `2.4-develop` gren):

   ```bash
   git checkout 2.4-develop
   ```

1. Ändra till `<magento_root>`.
1. Ange följande kommando för att skapa symboliska länkar mellan filerna som du klonade så att exempeldata fungerar som de ska:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="<path_to_your_magento_instance>"
   ```

   Exempel:

   ```bash
   php -f <sample-data_clone_dir>/dev/tools/build-sample-data.php -- --ce-source="/var/www/magento2"
   ```

1. Vänta tills kommandot har slutförts.
1. Se nästa avsnitt.

>[!WARNING]
>
>Om du installerar exempeldata *efter* När du installerar Adobe Commerce måste du också köra följande kommando för att uppdatera databasen och schemat:
>
>```bash
><magento_root>/bin/magento setup:upgrade
>```

## Ange ägarskap och behörigheter för filsystemet

På grund av `php build-sample-data.php` skriptet skapar länkar mellan exempeldatalagret och din Magento Open Source-databas. Du måste ange filsystembehörigheter och ägarskap i exempeldatalagret. Om du inte gör det blir det fel att öppna butiken.

Så här anger du behörigheter och ägarskap för filsystemet i exempeldatabasen:

1. Byt till din exempeldataklonkatalog.
1. Ange ägarskap:

   ```bash
   chown -R :<your web server group name> .
   ```

   Typiska exempel:

   * CentOS: `chown -R :apache .`

   * Ubuntu: `chown -R :www-data .`

1. Ange behörigheter:

   ```bash
   find . -type d -exec chmod g+ws {} +
   ```

1. Rensa statiska filer:

   ```bash
   cd <your Magento Open Source install dir>
   ```

   ```bash
   rm -rf var/cache/* var/page_cache/* generated/*
   ```

## Slutför installationen av exempeldata

{{$include /help/_includes/sample-data-complete.md}}
