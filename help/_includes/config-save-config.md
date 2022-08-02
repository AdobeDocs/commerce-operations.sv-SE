---
source-git-commit: a75b6e0360e7896b8349e7b1877c28d31d5bc0a8
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---
# Uppdatera den delade konfigurationen

**Uppdatera konfigurationen**:

1. Logga in på utvecklingssystemet som ägare av filsystemet eller växla till det.

1. Byt till programroten och kör kommandot dump.

   ```bash
   cd <Magento root dir>
   php bin/magento app:config:dump
   ```

   Om Commerce till exempel är installerat i `/var/www/html/magento2`, ange:

   ```bash
   cd /var/www/html/magento2
   php bin/magento app:config:dump
   ```

1. Bekräfta att `app/etc/config.php` uppdaterades.

   ```bash
   git status
   ```

   Exempelsvar:

   ```terminal
   On branch m2.2_deploy
   Changed but not updated:
     (use "git add <file>..." to update what will be committed)
     (use "git checkout -- <file>..." to discard changes in working directory)
          modified:   app/etc/config.php
   ```

   >[!WARNING]
   >
   >Gör _not_ skicka ändringar av `generated`, `pub/media`, eller `pub/static` kataloger till källkontroll. Du genererar dessa filer i ditt byggsystem. Utvecklingssystemet har förmodligen kod, teman och så vidare som inte är klara att användas i produktionssystemet.

1. Checka in dina ändringar i `app/etc/config.php` endast till källkontroll.

   ```bash
   git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
   ```
