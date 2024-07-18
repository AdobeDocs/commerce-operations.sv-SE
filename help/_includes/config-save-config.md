---
source-git-commit: ca8dc855e0598d2c3d43afae2e055aa27035a09b
workflow-type: tm+mt
source-wordcount: '94'
ht-degree: 0%

---
# Uppdatera den delade konfigurationen

**Så här uppdaterar du konfigurationen**:

1. Logga in på utvecklingssystemet som ägare av filsystemet eller växla till det.

1. Byt till programroten och kör kommandot dump.

   ```bash
   cd <Magento root dir>
   php bin/magento app:config:dump
   ```

   Om Commerce till exempel är installerat i `/var/www/html/magento2` anger du:

   ```bash
   cd /var/www/html/magento2
   php bin/magento app:config:dump
   ```

1. Bekräfta att `app/etc/config.php` har uppdaterats.

   ```bash
   git status
   ```

   Exempelsvar:

   ```
   On branch m2.2_deploy
   Changed but not updated:
     (use "git add <file>..." to update what will be committed)
     (use "git checkout -- <file>..." to discard changes in working directory)
          modified:   app/etc/config.php
   ```

   >[!WARNING]
   >
   >Skicka _inte_ ändringar i katalogerna `generated`, `pub/media` eller `pub/static` till källkontrollen. Du genererar dessa filer i ditt byggsystem. Utvecklingssystemet har förmodligen kod, teman och så vidare som inte är klara att användas i produktionssystemet.

1. Checka endast in dina ändringar i `app/etc/config.php` för källkontroll.

   ```bash
   git add app/etc/config.php && git commit -m "Updated shared configuration" && git push mconfig m2.2_deploy
   ```
