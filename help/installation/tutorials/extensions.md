---
title: Installera ett tillägg
description: Så här installerar du ett Adobe Commerce- eller Magento Open Source-tillägg.
exl-id: b564662a-2e5f-4fa9-bae1-ca7498478fa9
source-git-commit: 8d0d8f9822b88f2dd8cbae8f6d7e3cdb14cc4848
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 0%

---

# Installera ett tillägg

Kod som utökar eller anpassar Adobe Commerce-beteendet kallas ett tillägg. Du kan även paketera och distribuera tillägg på [Commerce Marketplace](https://marketplace.magento.com) eller ett annat tilläggsdistributionssystem.

Tilläggen omfattar:

- Moduler (utöka Adobe Commerce funktioner)
- Teman (ändra utseende och känsla för din butik och administratör)
- Språkpaket (lokalisera butiken och administratören)

>[!TIP]
>
>I det här avsnittet beskrivs hur du använder kommandoraden för att installera tillägg som du köper från Commerce Marketplace. Du kan använda samma procedur för att installera _alla_ -tillägg. Allt du behöver är tilläggets disposition och version. Öppna tilläggets `composer.json` och notera värdena för `"name"` och `"version"`.

Före installationen kanske du vill:

1. Säkerhetskopiera databasen.
1. Aktivera underhållsläge:

   ```bash
   bin/magento maintenance:enable
   ```

Om du vill installera ett tillägg måste du:

1. Få ett tillägg från Commerce Marketplace eller en annan tilläggsutvecklare.
1. Om du installerar ett tillägg från Commerce Marketplace ska du kontrollera att `repo.magento.com` databasen finns i din `composer.json` fil:

   ```bash
   "repositories": [
       {
           "type": "composer",
           "url": "https://repo.magento.com/"
       }
   ]
   ```

1. Hämta tilläggets dispositionsnamn och version.
1. Uppdatera `composer.json` i projektet med tilläggets namn och version.
1. Kontrollera att tillägget har installerats korrekt.
1. Aktivera och konfigurera tillägget.

## Hämta namnet och versionen för tilläggsdispositionen

Om du redan känner till namnet och versionen på tilläggets disposition hoppar du över det här steget och fortsätter med [Uppdatera dina `composer.json` fil](#update-your-composer-file).

Så här hämtar du tilläggets dispositionsnamn och version från Commerce Marketplace:

1. Logga in på [Commerce Marketplace](https://marketplace.magento.com) med det användarnamn och lösenord som du använde för att köpa tillägget.

1. Klicka på i det övre högra hörnet **Ditt namn** > **Min profil**.

   ![Gå till ditt Marketplace-konto](../../assets/installation/marketplace-my-profile.png)

1. Klicka **Mina inköp**.

   ![Marketplace-inköpshistorik](../../assets/installation//marketplace-my-purchases.png)

1. Hitta det tillägg som du vill installera och klicka på **Teknisk information**.

   ![Teknisk information visar tilläggets dispositionsnamn](../../assets/installation/marketplace-extension-technical-details.png)

>[!TIP]
>
>Du kan också hitta Composer-namnet och versionen av _alla_ tillägg (vare sig du har köpt det på Commerce Marketplace eller någon annanstans) i tilläggets `composer.json` -fil.

## Uppdatera din Composer-fil

Lägg till tilläggets namn och version i din `composer.json` fil:

1. Navigera till projektkatalogen och uppdatera `composer.json` -fil.

   ```bash
   composer require <component-name>:<version>
   ```

   Exempel:

   ```bash
   composer require j2t/module-payplug:2.0.2
   ```

1. Ange [autentiseringsnycklar](../prerequisites/authentication-keys.md). Din offentliga nyckel är ditt användarnamn. Din privata nyckel är ditt lösenord.

1. Vänta tills Composer har uppdaterat dina projektberoenden och kontrollera att inga fel uppstår:

   ```terminal
   Updating dependencies (including require-dev)
   Package operations: 1 install, 0 updates, 0 removals
     - Installing j2t/module-payplug (2.0.2): Downloading (100%)
   Writing lock file
   Generating autoload files
   ```

## Verifiera tillägget

Kör följande kommando för att kontrollera att tillägget är korrekt installerat:

```bash
bin/magento module:status J2t_Payplug
```

Tillägget är antagligen inaktiverat som standard:

```terminal
Module is disabled
```

Tilläggsnamnet har formatet `<VendorName>_<ComponentName>`; det här är ett annat format än Composer-namnet. Använd det här formatet om du vill aktivera tillägget. Om du är osäker på tilläggets namn kör du:

```bash
bin/magento module:status
```

Och sök efter tillägget under&quot;Lista över inaktiverade moduler&quot;.

## Aktivera tillägget

Vissa tillägg fungerar inte korrekt om du inte först rensar genererade statiska vyfiler. Använd `--clear-static-content` om du vill rensa statiska visningsfiler när du aktiverar ett tillägg.

1. Aktivera tillägget och rensa statiska visningsfiler:

   ```bash
   bin/magento module:enable J2t_Payplug --clear-static-content
   ```

   Följande utdata bör visas:

   ```terminal
   The following modules have been enabled:
   - J2t_Payplug
   
   To make sure that the enabled modules are properly registered, run 'setup:upgrade'.
   Cache cleared successfully.
   Generated classes cleared successfully. Please run the 'setup:di:compile' command to generate classes.
   Generated static view files cleared successfully.
   ```

1. Registrera tillägget:

   ```bash
   bin/magento setup:upgrade
   ```

1. Kompilera om ditt projekt: I produktionsläget kan du få ett meddelande om att köra kompileringskommandot för Magento igen. Du uppmanas inte att köra kompileringskommandot i utvecklarläget.

   ```bash
   bin/magento setup:di:compile
   ```

1. Kontrollera att tillägget är aktiverat:

   ```bash
   bin/magento module:status J2t_Payplug
   ```

   Du bör se utdata som verifierar att tillägget inte längre är inaktiverat:

   ```terminal
   Module is enabled
   ```

1. Rensa cachen:

   ```bash
   bin/magento cache:clean
   ```

1. Konfigurera tillägget i Admin efter behov.

>[!TIP]
>
>Om fel uppstår när du läser in butiken i en webbläsare använder du följande kommando för att rensa cachen: `bin/magento cache:flush`.

## Uppgradera ett tillägg

Så här uppdaterar eller uppgraderar du en modul eller ett tillägg:

1. Hämta den uppdaterade filen från Marketplace eller någon annan tilläggsutvecklare. Notera modulens namn och version.

1. Exportera innehållet till programmets rotkatalog.

1. Om det finns ett Composer-paket för modulen kör du något av följande.

   Uppdatering per modulnamn:

   ```bash
   composer update vendor/module-name
   ```

   Uppdatering per version:

   ```bash
   composer require vendor/module-name ^x.x.x
   ```

1. Kör följande kommandon för att uppgradera, distribuera och rensa cachen.

   ```bash
   bin/magento setup:upgrade --keep-generated
   ```

   ```bash
   bin/magento setup:static-content:deploy
   ```

   ```bash
   bin/magento cache:clean
   ```
