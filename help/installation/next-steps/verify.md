---
title: Verifiera installationen
description: Följ de här stegen för att bekräfta att din lokala Adobe Commerce-installation lyckades.
exl-id: 0bd7ec01-c616-4384-ae26-db2ce3668caf
source-git-commit: ddf988826c29b4ebf054a4d4fb5f4c285662ef4e
workflow-type: tm+mt
source-wordcount: '245'
ht-degree: 0%

---

# Verifiera installationen

Gå till butiken i en webbläsare. Om t.ex. din installationsbas-URL är `http://www.example.com` anger du den i webbläsarens adress- eller platsfält.

I bilden nedan visas ett exempel på en butikssida. Om den visas på följande sätt har installationen lyckats!

![Storefront med Luma-temat](../../assets/installation/install-success_store-luma.png)

## Verifiera butiken (inga exempeldata)

Gå till butiken i en webbläsare. Om t.ex. din installationsbas-URL är `http://www.example.com` anger du den i webbläsarens adress- eller platsfält.

I bilden nedan visas ett exempel på en butikssida. Om den visas på följande sätt har installationen lyckats!

![Storefront som verifierar en lyckad installation](../../assets/installation/install-success_store.png)

Om sidan visar ett `404 (Not Found)`-fel eller inte visar format, se [felsökning](https://support.magento.com/hc/en-us/articles/360032994352).

## Verifiera administratören

Gå till administratören i en webbläsare. Om t.ex. din installationsbas-URL är `http://www.example.com` och Admin-URI är `admin_au1nT` anger du `http://www.example.com/admin_au1nT` i webbläsarens adress- eller platsfält.

(Admin-URI anges av värdet för installationsparametern `backend-frontname`.)

Logga in som administratör när du uppmanas till detta.

I bilden nedan visas ett exempel på en admin-sida. Om den visas på följande sätt har installationen lyckats!

![Admin som verifierar en lyckad installation](../../assets/installation/install_success_admin.png)

Om sidan inte visar format kan du läsa [felsökning](https://support.magento.com/hc/en-us/articles/360032994352).

Om du får ett 404-fel (Hittades inte) som det nedan kan du läsa [PHP-versionsfel eller 404 när du använder Adobe Commerce i webbläsaren](https://support.magento.com/hc/en-us/articles/360033117152).

`The requested URL /magento2index.php/admin/admin/dashboard/index/key/0c81957145a968b697c32a846598dc2e/ was not found on this server.`
