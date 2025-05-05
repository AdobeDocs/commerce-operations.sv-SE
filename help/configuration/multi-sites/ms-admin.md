---
title: Konfigurera flera webbplatser, butiker och butiksvyer i administratören
description: Konfigurera ytterligare webbplatser, butiker och butiksvyer i Commerce Admin.
exl-id: e6b4d14d-7504-48f9-a2e1-7e9a1bc76ab9
source-git-commit: 987d65b52437fbd21f41600bb5741b3cc43d01f3
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 0%

---

# Konfigurera flera vyer i administratören

Den här aktiviteten kräver att du skapar en rotkategori (och ytterligare kategorier om så önskas) för varje butik. De uppgifter som behandlas i det här avsnittet är ett sätt att konfigurera flera butiker. Mer information finns i följande resurser i användarhandboken för Commerce:

- [Kategorier](https://experienceleague.adobe.com/sv/docs/commerce-admin/catalog/categories/categories)
- [Lägger till webbplatser](https://experienceleague.adobe.com/sv/docs/commerce-admin/stores-sales/site-store/stores#add-websites)
- [Lagra URL:er](https://experienceleague.adobe.com/sv/docs/commerce-admin/stores-sales/site-store/store-urls)
- [Innehåll](https://experienceleague.adobe.com/sv/docs/commerce-admin/content-design/content-menu)

>[!INFO]
>
>Vi använder till exempel bara en fransk webbplats med webbplatskoden `french` i det här avsnittet. Stegvisa självstudiekurser finns i [Självstudiekurs: Konfigurera flera webbplatser med Apache](ms-apache.md) och [Självstudiekurs: Konfigurera flera webbplatser med Nginx](ms-nginx.md)

## Steg 1: Skapa rotkategorier

Det är valfritt att skapa en rotkategori, men vi visar hur du gör det i den här självstudiekursen om du vill att varje webbplats ska ha en unik rotkategori. Om du vill kan du skapa ytterligare kategorier.

Så här skapar du en rotkategori:

1. Logga in på administratören som en användare som har behörighet att skapa kategorier.
1. Klicka på **Katalog** > **Kategorier**.
1. Klicka på **Lägg till rotkategori**.
1. I fältet **Kategorinamn** anger du ett unikt namn som identifierar den här kategorin.
1. Kontrollera att Aktivera kategori är inställt på **Ja**.

   Mer information om de andra alternativen på den här sidan finns i [Rotkategorier](https://experienceleague.adobe.com/sv/docs/commerce-admin/catalog/categories/category-root).

   I bilden nedan visas ett exempel.

   ![Skapa och aktivera en rotkategori](../../assets/configuration/add-root-category.png)

1. Klicka på **Spara**.
1. Upprepa dessa uppgifter så många gånger som behövs för att skapa rotkategorier för butikerna.

## Steg 2: Skapa webbplatser

Så här skapar du en webbplats:

1. Logga in på administratören som en användare som har behörighet att skapa webbplatser, butiker och butiksvyer.
1. Klicka på **Lagrar** > **Inställningar** > **Alla butiker**.
1. Klicka på **Skapa webbplats** på sidan _Lagrar_.

   - **Namn** - Ange ett namn som identifierar webbplatsen.
   - **Kod** - Ange en unik kod. Om du till exempel har en fransk butik kan du ange `french`
   - **Sorteringsordning** - Ange en numerisk sorteringsordning (valfritt).

   I bilden nedan visas ett exempel.

   ![Lägg till en webbplats](../../assets/configuration/multi-site-website.png)

1. Klicka på **Spara webbplats**.
1. Upprepa dessa uppgifter så många gånger som behövs för att skapa webbplatser.

## Steg 3: Skapa butiker

Så här skapar du en butik:

1. Klicka på **Lagrar** > **Inställningar** > **Alla butiker** på panelen _Admin_.
1. Klicka på **Skapa butik** på sidan _Lager_.

   - **Webbplats** - Klicka på namnet på webbplatsen som du vill associera den här butiken med.
   - **Namn** - Ange ett namn som identifierar arkivet.
   - **Kod** - Ange en unik kod för att identifiera butiken.
   - **Rotkategori** - Klicka på namnet på rotkategorin för det här arkivet.

   I bilden nedan visas ett exempel.

   ![Lägg till en butik](../../assets/configuration/multi-site-store.png)

1. Klicka på **Spara butik**.
1. Upprepa dessa uppgifter så många gånger som behövs för att skapa butiker.

## Steg 4: Skapa butiksvyer

Så här skapar du en butiksvy:

1. Klicka på **Lagrar** > **Inställningar** > **Alla butiker** på panelen _Admin_.
1. Klicka på **Skapa butiksvy** på sidan Lager.

   - **Butik** - Klicka på namnet på den butik som butiksvyn ska associeras med.
   - **Namn** - Ange ett namn som identifierar den här butiksvyn.
   - **Kod** - Ange ett unikt namn för att identifiera den här butiksvyn.
   - **Status** - Välj **Aktiverad**.

   I bilden nedan visas ett exempel.

   ![Lägg till en butik](../../assets/configuration/multi-site-storeview.png)

1. Klicka på **Spara butiksvy**.
1. Upprepa dessa uppgifter så många gånger som behövs för att skapa butiksvyer.

## Steg 5: Ändra webbplatsens bas-URL

Om du vill komma åt en webbplats med en unik URL som `http://french.magento.mg` måste du ändra bas-URL:en för varje webbplats i Admin.

Så här ändrar du webbplatsens bas-URL:

1. Klicka på **Lagrar** > **Inställningar** > **Konfiguration** > **Allmänt** > **Webb** på panelen _Admin_.
1. I listan **Butiksvy** högst upp på sidan klickar du på namnet på en av dina webbplatser som på bilden nedan.

   ![Välj ett scope](../../assets/configuration/multi-site-scope.png)

1. Expandera **Bas-URL:er** i den högra rutan.
1. I avsnittet _Bas-URL:er_ rensar du **Använd systemvärde**.
1. Ange `http://french.magento.mg`-URL:en i fälten **Bas-URL** och **Bas länk-URL**.

1. Upprepa föregående steg i avsnittet _Bas-URL:er (säkra)_.

   >[!INFO]
   >
   >Om du konfigurerar en bas-URL för distribution av Adobe Commerce i molninfrastruktur måste du ersätta den första perioden med tre streck. Om bas-URL:en till exempel är `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud` anger du `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`. Om du konfigurerar en bas-URL för lokal testning ska du använda en punkt.

1. Klicka på **Spara konfiguration**.

1. Upprepa dessa uppgifter för andra webbplatser.

## Steg 6: Lägg till butikskoden i bas-URL:en

Commerce ger dig möjlighet att lägga till butikskoden i webbplatsens bas-URL, vilket förenklar processen att konfigurera flera butiker. Med det här alternativet behöver du inte skapa kataloger i Commerce filsystem för att lagra `index.php` och `.htaccess`.

Detta förhindrar att `index.php` och `.htaccess` kommer ur synk med Commerce-kodbasen vid framtida uppgraderingar.

Se [Commerce användarhandbok](https://experienceleague.adobe.com/sv/docs/commerce-admin/stores-sales/site-store/store-urls).

Så här lägger du till butikskoden i bas-URL:en:

1. Klicka på **Lagrar** > **Inställningar** > **Konfiguration** > **Allmänt** > **Webb** på panelen _Admin_.
1. I listan **Butiksvy** överst på sidan klickar du på **Standardkonfiguration** enligt bilden nedan.

   ![Välj standardkonfigurationsomfånget](../../assets/configuration/multi-site-default.png)

1. Expandera **URL-alternativ** i den högra rutan.
1. Avmarkera kryssrutan **Använd systemvärde** intill _Lägg till lagringskod till URL:er_.
1. Klicka på **Ja** i listan _Lägg till butikskod i URL_.

   ![Lägg till butikskoden i butiksbas-URL:en](../../assets/configuration/multi-site-add-store-url.png)

1. Klicka på **Spara konfiguration**.
1. Rensa cachen om du uppmanas till det. (**System** > **Cache Management**).

## Steg 7: Ändra standardbas-URL för butiksvyn

Du måste utföra det här steget sist eftersom du inte längre har tillgång till Admin. Åtkomsten returneras när du har konfigurerat virtuella värddatorer enligt beskrivningen i de webbserverspecifika avsnitten.

Så här ändrar du bas-URL:en för butiksvyn:

1. Klicka på **Lagrar** > **Inställningar** > **Konfiguration** > **Allmänt** > **Webb** på panelen _Admin_.

1. Klicka på **Standardkonfiguration** i listan _Butiksvy_ överst på sidan.

   ![Välj standardkonfigurationsomfånget](../../assets/configuration/multi-site-default.png)

1. Expandera **Bas-URL:er** i den högra rutan.
1. I avsnittet _Bas-URL:er_ rensar du **Använd systemvärde**.
1. Ange `http://magento.mg`-URL:en i fälten **Bas-URL** och **Bas länk-URL**.

1. Upprepa föregående steg i avsnittet **Bas-URL:er (säkra)**.

   >[!INFO]
   >
   >Om du skapar en bas-URL för Adobe Commerce i molninfrastrukturen måste du ersätta den första perioden med tre streck. Om bas-URL:en till exempel är `french.branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud` anger du `http://french---branch-sbg7pPa-f3dueAiM03tpy.us.magentosite.cloud`

1. Klicka på **Spara konfiguration**.

>[!INFO]
>
>Koden för webbplatsvyn, butiken och butiksvyn kan endast innehålla bokstäver (a-z eller A-Z), siffror (0-9) och understreck (_). Dessutom måste det första tecknet vara en bokstav. Om versaler eller kameravärden används är matchningen internt skiftlägeskänslig för att ge plats åt åsidosättning av konfigurationsinställningar via systemvariabler. Se [Använd miljövariabler för att åsidosätta konfigurationsinställningar](../reference/override-config-settings.md#environment-variables).