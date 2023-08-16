---
title: Anpassa sökvägar för baskatalog
description: Använd variabeln MAGE_DIRS för att ange en array med absoluta sökvägar.
exl-id: ee8e1a3a-f1d4-412c-8767-16447113f0cd
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '129'
ht-degree: 0%

---

# Sökvägar till baskatalog

The `MAGE_DIRS` miljövariabeln gör att du kan ange anpassade baskatalogsökvägar och fragment av bas-URL:er som används av Commerce-programmet för att skapa absoluta sökvägar till olika filer eller för att generera URL:er.

## Ange MAGE_DIRS

Ange en associativ array där nycklarna är konstanter från [\\Magento\\App\\Filesystem\\DirectoryList][directory-list] och -värden är absoluta sökvägar för kataloger respektive deras URL-sökvägar.

Du kan ange `MAGE_DIRS` på något av följande sätt:

- [Ange värdet för bootstrap-parametrar](../bootstrap/set-parameters.md)
- Använd ett anpassat startpunktsskript som följande:

  ```php
  <?php
  /**
   * Copyright © Magento, Inc. All rights reserved.
   * See COPYING.txt for license details.
   */
  
  use Magento\Framework\App\Bootstrap;
  use Magento\Framework\App\Filesystem\DirectoryList;
  use Magento\Framework\App\Http;
  
  require __DIR__ . '/app/bootstrap.php';
  $params = $_SERVER;
  $params[Bootstrap::INIT_PARAM_FILESYSTEM_DIR_PATHS] = [
       DirectoryList::PUB => [DirectoryList::URL_PATH => ''],
       DirectoryList::MEDIA => [DirectoryList::PATH => '/mnt/nfs/media', DirectoryList::URL_PATH => ''],
       DirectoryList::STATIC_VIEW => [DirectoryList::URL_PATH => 'static'],
       DirectoryList::UPLOAD => [DirectoryList::URL_PATH => '/mnt/nfs/media/upload'],
       DirectoryList::CACHE => [DirectoryList::PATH => '/mnt/nfs/cache'],
  ];
  $bootstrap = Bootstrap::create(BP, $params);
  /** @var Http $app */
  $app = $bootstrap->createApplication(Http::class);
  $bootstrap->run($app);
  ```

I det föregående exemplet anges sökvägar för `[cache]` och `[media]` kataloger till `/mnt/nfs/cache` och `/mnt/nfs/media`, respektive

<!-- link definitions -->

[directory-list]: https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php
