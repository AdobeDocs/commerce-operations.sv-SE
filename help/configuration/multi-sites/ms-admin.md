---
title: Konfigurera flera webbplatser, butiker och butiksvyer i administratören
description: Konfigurera ytterligare webbplatser, butiker och butiksvyer i Commerce Admin.
exl-id: e6b4d14d-7504-48f9-a2e1-7e9a1bc76ab9
source-git-commit: f7c82844fd6d006e4ebbcf56f6e10338f67d0bdd
workflow-type: tm+mt
source-wordcount: '1066'
ht-degree: 0%

---

# Konfigurera flera vyer i administratören

Den här aktiviteten kräver att du skapar en rotkategori (och ytterligare kategorier om så önskas) för varje butik. De uppgifter som behandlas i det här avsnittet är ett sätt att konfigurera flera butiker. Mer information finns i följande resurser i Commerce User Guide:

- [Kategorier](https://docs.magento.com/user-guide/catalog/categories.html)
- [Lägga till webbplatser](https://docs.magento.com/user-guide/stores/stores-all-create-website.html)
- [Lagra URL:er](https://docs.magento.com/user-guide/stores/store-urls.html)
- [Innehåll](https://docs.magento.com/user-guide/cms/content-menu.html)

>[!INFO]
>
>Vi använder till exempel bara en fransk webbplats med webbplatskod `french` i det här avsnittet. Självstudiekurser steg för steg finns i [Självstudiekurs: Konfigurera flera webbplatser med Apache](ms-apache.md) och [Självstudiekurs: Konfigurera flera webbplatser med ginx](ms-nginx.md)

## Steg 1: Skapa rotkategorier

Det är valfritt att skapa en rotkategori, men vi visar hur du gör det i den här självstudiekursen om du vill att varje webbplats ska ha en unik rotkategori. Om du vill kan du skapa ytterligare kategorier.

Så här skapar du en rotkategori:

1. Logga in på administratören som en användare som har behörighet att skapa kategorier.
1. Klicka **Katalog** > **Kategorier**.
1. Klicka **Lägg till rotkategori**.
1. I **Kategorinamn** anger du ett unikt namn som identifierar den här kategorin.
1. Kontrollera att Aktivera kategori är inställt på **Ja**.

   Information om de andra alternativen på den här sidan finns i [Rotkategorier](https://docs.magento.com/user-guide/catalog/category-root.html).

   I bilden nedan visas ett exempel.

   ![Skapa och aktivera en rotkategori](../../assets/configuration/add-root-category.png)

1. Klicka **Spara**.
1. Upprepa dessa uppgifter så många gånger som behövs för att skapa rotkategorier för butikerna.

## Steg 2: Skapa webbplatser

Så här skapar du en webbplats:

1. Logga in på administratören som en användare som har behörighet att skapa webbplatser, butiker och butiksvyer.
1. Klicka **Lager** > **Inställningar** > **Alla butiker**.
1. På _Lager_ sida, klicka **Skapa webbplats**.

   - **Namn**—Ange ett namn som identifierar webbplatsen.
   - **Code**—Ange en unik kod. Om du till exempel har en fransk butik kan du ange `french`
   - **Sorteringsordning**—Ange en numerisk sorteringsordning (valfritt).

   I bilden nedan visas ett exempel.

   ![Lägga till en webbplats](../../assets/configuration/multi-site-website.png)

1. Klicka **Spara webbplats**.
1. Upprepa dessa uppgifter så många gånger som behövs för att skapa webbplatser.

## Steg 3: Skapa butiker

Så här skapar du en butik:

1. I _Administratör_ panel, klicka **Lager** > **Inställningar** > **Alla butiker**.
1. På _Lager_ sida, klicka **Skapa butik**.

   - **Webbplats**—Klicka på namnet på den webbplats som du vill associera den här butiken med.
   - **Namn**—Ange ett namn som identifierar butiken.
   - **Code**—Ange en unik kod som identifierar butiken.
   - **Rotkategori**—Klicka på namnet på rotkategorin för det här arkivet.

   I bilden nedan visas ett exempel.

   ![Lägg till en butik](../../assets/configuration/multi-site-store.png)

1. Klicka **Spara butik**.
1. Upprepa dessa uppgifter så många gånger som behövs för att skapa butiker.

## Steg 4: Skapa butiksvyer

Så här skapar du en butiksvy:

1. I _Administratör_ panel, klicka **Lager** > **Inställningar** > **Alla butiker**.
1. På sidan Store klickar du på **Skapa butiksvy**.

   - **Butik**—Klicka på namnet på den butik som butiksvyn ska associeras med.
   - **Namn**—Ange ett namn som identifierar den här butiksvyn.
   - **Code**—Ange ett unikt namn för att identifiera butiksvyn.
   - **Status**—Select **Aktiverad**.

   I bilden nedan visas ett exempel.

   ![Lägg till en butik](../../assets/configuration/multi-site-storeview.png)

1. Klicka **Spara butiksvy**.
1. Upprepa dessa uppgifter så många gånger som behövs för att skapa butiksvyer.

## Steg 5: Ändra webbplatsens bas-URL

Använda en unik URL som `http://french.magento.mg`måste du ändra bas-URL:en för varje plats i Admin.

Så här ändrar du webbplatsens bas-URL:

1. I _Administratör_ panel, klicka **Lager** > **Inställningar** > **Konfiguration** > **Allmänt** > **Webb**.
1. Från **Butiksvy** överst på sidan klickar du på namnet på en av dina webbplatser som på bilden nedan.

   ![Välj ett omfång](../../assets/configuration/multi-site-scope.png)

1. Expandera i den högra rutan **Bas-URL**.
1. I _Bas-URL_ sektion, klar **Använd systemvärde**.
1. Ange `http://french.magento.mg` URL i **Bas-URL** och **Bas länk-URL** fält.

1. Upprepa föregående steg i dialogrutan _Bas-URL:er (säkra)_ -avsnitt.

   >[!INFO]
   >
   >Om du konfigurerar en bas-URL för distribution av Adobe Commerce i molninfrastruktur måste du ersätta den första perioden med tre streck. Om bas-URL:en till exempel är `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`, ange `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`. Om du konfigurerar en bas-URL för lokal testning ska du använda en punkt.

1. Klicka **Spara konfiguration**.

1. Upprepa dessa uppgifter för andra webbplatser.

## Steg 6: Lägg till butikskoden i bas-URL:en

Med Commerce kan du lägga till butikskoden i webbplatsens bas-URL, vilket förenklar processen att konfigurera flera butiker. Med det här alternativet behöver du inte skapa kataloger i Commerce-filsystemet för att kunna lagra `index.php` och `.htaccess`.

Detta förhindrar `index.php` och `.htaccess` från att komma ur synk med Commerce-kodbasen i framtida uppgraderingar.

Se [Handbok för Commerce](https://docs.magento.com/user-guide/stores/store-urls.html).

Så här lägger du till butikskoden i bas-URL:en:

1. I _Administratör_ panel, klicka **Lager** > **Inställningar** > **Konfiguration** > **Allmänt** > **Webb**.
1. Från **Butiksvy** överst på sidan klickar du på **Standardkonfiguration** som bilden nedan visar.

   ![Välj standardkonfigurationsomfång](../../assets/configuration/multi-site-default.png)

1. Expandera i den högra rutan **URL-alternativ**.
1. Rensa **Använd systemvärde** kryssruta intill _Lägg till butikskod i URL:er_.
1. Från _Lägg till butikskod i URL:er_ lista, klicka på **Ja**.

   ![Lägg till butikskoden i butikens bas-URL](../../assets/configuration/multi-site-add-store-url.png)

1. Klicka **Spara konfiguration**.
1. Rensa cachen om du uppmanas till det. (**System** > **Cachehantering**).

## Steg 7: Ändra standardbas-URL för butiksvyn

Du måste utföra det här steget sist eftersom du inte längre har tillgång till Admin. Åtkomsten returneras när du har konfigurerat virtuella värddatorer enligt beskrivningen i de webbserverspecifika avsnitten.

Så här ändrar du bas-URL:en för butiksvyn:

1. I _Administratör_ panel, klicka **Lager** > **Inställningar** > **Konfiguration** > **Allmänt** > **Webb**.

1. Från _Butiksvy_ överst på sidan klickar du på **Standardkonfiguration**.

   ![Välj standardkonfigurationsomfång](../../assets/configuration/multi-site-default.png)

1. Expandera i den högra rutan **Bas-URL**.
1. I _Bas-URL_ sektion, klar **Använd systemvärde**.
1. Ange `http://magento.mg` URL i **Bas-URL** och **Bas länk-URL** fält.

1. Upprepa föregående steg i dialogrutan **Bas-URL:er (säkra)** -avsnitt.

   >[!INFO]
   >
   >Om du skapar en bas-URL för Adobe Commerce i molninfrastrukturen måste du ersätta den första perioden med tre streck. Om bas-URL:en till exempel är `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`, ange `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`

1. Klicka **Spara konfiguration**.

>[!INFO]
>
>Koden för webbplatsvyn, butiken och butiksvyn kan endast innehålla bokstäver (a-z eller A-Z), siffror (0-9) och understreck (_). Dessutom måste det första tecknet vara en bokstav. Om versaler eller kameravärden används är matchningen internt skiftlägeskänslig för att ge plats åt åsidosättning av konfigurationsinställningar via systemvariabler. Se [Använd miljövariabler för att åsidosätta konfigurationsinställningar](../reference/override-config-settings.md#environment-variables).