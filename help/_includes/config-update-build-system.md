---
source-git-commit: 53448b11a2d000fe8e8a7eecf2ffcef4b7e248fa
workflow-type: tm+mt
source-wordcount: '49'
ht-degree: 0%

---
# Uppdatera byggsystem

**Så här uppdaterar du byggsystemet**:

1. Logga in på byggsystemet som ägare av filsystemet.
1. Byt till programmets rotkatalog.

   ```bash
   cd <Magento root dir>
   ```

1. Dra in ändringarna i `app/etc/config.php` från källkontrollen.

   ```bash
   git pull mconfig m2.2_deploy
   ```

1. Kompilera kod.

   ```bash
   bin/magento setup:di:compile
   ```

1. Generera statiska vyfiler när koden har kompilerats.

   ```bash
   bin/magento setup:static-content:deploy -f
   ```

1. Kontrollera ändringarna i källkontrollen.

   ```bash
   git add -A && git commit -m "Updated files on build system" && git push mconfig m2.2_deploy
   ```
