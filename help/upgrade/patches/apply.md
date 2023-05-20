---
title: Använd korrigeringar
description: Lär dig mer om metoderna för att använda korrigeringsfiler i ett Adobe Commerce- eller Magento Open Source-projekt.
exl-id: 1d5d81ad-0115-4575-adfd-dde7c2826d85
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---

# Tillämpa patchar

Du kan använda patchar på följande sätt:

- [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}
- [Kommandorad](../patches/apply.md#command-line)
- [Disposition](../patches/apply.md#composer)

## Disposition

>[!IMPORTANT]
>
>Om du vill använda officiella kvalitetspatchar använder du [[!DNL Quality Patches Tool]](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html){target="_blank"}. Utför alltid omfattande testning innan du distribuerar någon anpassad patch.

Så här använder du en anpassad korrigering med Composer:

1. Öppna kommandoradsprogrammet och gå till projektkatalogen.
1. Lägg till `cweagans/composer-patches` plugin till `composer.json` -fil.

   ```bash
   composer require cweagans/composer-patches
   ```

1. Redigera `composer.json` och lägg till följande avsnitt för att ange:
   - **Modul:** *\&quot;magento/module-payment\&quot;*
   - **Titel:** *\&quot;MAGETWO-56934: Checkout page freezes when order with Authorize.net with invalid credit card\&quot;*
   - **Sökväg till korrigering:** *\&quot;patches/composer/github-issue-6474.diff\&quot;*

   Till exempel:

   ```json
   "extra": {
       "composer-exit-on-patch-failure": true,
       "patches": {
           "magento/module-payment": {
               "MAGETWO-56934: Checkout page freezes when ordering with Authorize.net with invalid credit card": "patches/composer/github-issue-6474.diff"
           }
       }
   }
   ```

   Om en korrigering påverkar flera moduler måste du skapa flera korrigeringsfiler för flera moduler.

1. Lägg på plåstret. Använd `-v` bara om du vill se felsökningsinformation.

   ```bash
   composer -v install
   ```

1. Uppdatera `composer.lock` -fil. Låsfilen spårar vilka korrigeringar som har tillämpats på varje Composer-paket i ett objekt.

   ```bash
   composer update --lock
   ```

## Kommandorad

Så här använder du patchar från kommandoraden:

1. Överför den lokala filen till `<Magento_root>` på servern med hjälp av FTP, SFTP, SSH eller din normala transportmetod.
1. Logga in på servern som [admin-användare](../../configuration/cli/config-cli.md#prerequisites) och kontrollera att filen finns i rätt katalog.
1. Kör följande kommandon i kommandoradsgränssnittet enligt patch-tillägget:

   ```bash
   patch < patch_file_name.patch
   ```

   Kommandot förutsätter att filen som ska korrigeras finns i förhållande till korrigeringsfilen.

   >[!NOTE]
   >
   >Om kommandoraden visar: `File to patch:`betyder det att den inte kan hitta den avsedda filen, även om sökvägen verkar vara korrekt. I den ruta som visas i kommandoradsterminalen visar den första raden filen som ska korrigeras. Kopiera filsökvägen och klistra in den i `File to patch:` fråga och tryck `Enter` och plåstret ska vara färdigt.

1. Uppdatera cacheminnet i administratören under **System** > Verktyg > **Cachehantering**.

   Du kan också använda korrigeringen lokalt med samma kommando och sedan implementera den och skicka den normalt.
