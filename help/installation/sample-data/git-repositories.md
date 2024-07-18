---
title: Klona exempeldata i Git-databaser
description: Följ de här stegen för att installera exempeldata för Adobe Commerce genom att klona Git-databaser.
exl-id: 748eee30-2821-457d-9c1c-62ede8bc0510
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 0%

---

# Klona exempeldata i Git-databaser

I det här avsnittet beskrivs hur du klonar och lägger till exempeldata om du klonade GitHub-databasen i Magento Open Source. Den här metoden är endast avsedd för utvecklare som bidrar till utvecklingen (det vill säga utvecklare som tänker bidra till kodbasen Magento Open Source).

Om du inte är en bidragsgivare väljer du ett av de andra alternativen som visas i innehållsförteckningen till vänster på sidan.

Utvecklare som deltar kan använda den här metoden för att installera exempeldata *endast* om följande är sant:

* Du använder Magento Open Source
* Du [klonade GitHub-databasen](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/)

>[!WARNING]
>
>Du kan använda exempeldata med antingen grenen `develop` (mer aktuell) eller en släppt gren (till exempel `2.4` (mer stabil)). Vi rekommenderar att du använder en frisläppt gren eftersom den är stabilare. Om du bidrar med kod till databasen och du behöver den senaste koden använder du grenen `develop`. Oavsett vilken gren du väljer måste du [klona](https://developer.adobe.com/commerce/contributor/guides/install/clone-repository/) motsvarande gren i Magento Open Source GitHub-databasen. Exempeldata för grenen `develop` kan till exempel användas *endast* med grenen Magento Open Source `develop`.

## Klona exempeldatabasen

I det här avsnittet beskrivs hur du installerar exempeldata genom att klona databasen med exempeldata. Du kan klona exempeldatabasen på något av följande sätt:

* Klona med [SSH-protokollet](#clone-with-ssh)
* Klona med [HTTPS-protokollet](#clone-with-https)

### Klona med SSH

Så här klonar du GitHub-databasen med exempeldata med SSH-protokollet:

1. Gå till [exempeldatalagret](https://github.com/magento/magento2-sample-data) i en webbläsare.
1. Klicka på **SSH** i listan bredvid namnet på grenen.
1. Klicka på **Kopiera till Urklipp**

   I bilden nedan visas ett exempel.

   ![Klona GitHub-databasen med SSH](../../assets/installation/install_mage2_clone-ssh.png)

1. Byt till webbserverns dokumentrotkatalog.

   Vanligtvis är det `/var/www` för Ubuntu och `/var/www/html` för CentOS.

1. Ange `git clone` och klistra in värdet som du fick tidigare.

   Ett exempel följer:

   ```bash
   git clone git@github.com:magento/magento2-sample-data.git
   ```

1. Vänta tills databasen har klonats på servern.

   >[!NOTE]
   >
   >Om följande fel visas kontrollerar du att du [delade din SSH-nyckel](https://docs.github.com/articles/generating-ssh-keys/) med GitHub:<br>

   ```
   Cloning into 'magento2'...
   Permission denied (publickey).
   fatal: The remote end hung up unexpectedly
   ```

1. Kontrollera att du checkar ut den gren i exempeldatalagret som motsvarar den gren du använde från huvuddatabasen `magento2`.

   Exempel:

   Om du använde `2.4-develop`-grenen i Magento Open Source GitHub-databasen bör Sample Data-grenen vara `2.4-develop`.

   Om du vill checka ut rätt gren kör du följande kommando från exempeldatalagrets rotkatalog (förutsatt att du behöver `2.4-develop`-grenen):

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

1. Gå till [exempeldatalagret](https://github.com/magento/magento2-sample-data) i en webbläsare.
1. Klicka på **HTTPS** under fältet **klon-URL** till höger på sidan.
1. Klicka på **Kopiera till Urklipp**.

   I bilden nedan visas ett exempel.

   ![Klona GitHub-databasen med HTTPS](../../assets/installation/install_mage2_clone-https.png)

1. Byt till webbserverns dokumentrotkatalog.

   Vanligtvis är det `/var/www` för Ubuntu och `/var/www/html` för CentOS.

1. Ange `git clone` och klistra in värdet som du fick tidigare.

   Ett exempel följer:

   ```bash
   git clone https://github.com/magento/magento2-sample-data.git
   ```

1. Vänta tills databasen har klonats på servern.
1. Kontrollera att du checkar ut den gren i exempeldatalagret som motsvarar den gren du använde från huvuddatabasen `magento2`.

   Exempel:

   Om du använde `2.4-develop`-grenen i Magento Open Source GitHub-databasen bör Sample Data-grenen vara `2.4-develop`.

   Om du vill checka ut rätt gren kör du följande kommando från exempeldatalagrets rotkatalog (förutsatt att du behöver `2.4-develop`-grenen):

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
>Om du installerar exempeldata *efter*-installationen av Adobe Commerce måste du också köra följande kommando för att uppdatera databasen och schemat:
>
>```bash
><magento_root>/bin/magento setup:upgrade
>```

## Ange ägarskap och behörigheter för filsystemet

Eftersom skriptet `php build-sample-data.php` skapar länkar mellan exempeldatalagret och din Magento Open Source-databas måste du ange filsystembehörigheter och ägarskap i exempeldatalagret. Om du inte gör det blir det fel att öppna butiken.

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
