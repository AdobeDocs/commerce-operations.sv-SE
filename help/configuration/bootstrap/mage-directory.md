---
title: Anpassa sökvägar för baskatalog
description: Använd variabeln MAGE_DIRS för att ange en array med absoluta sökvägar.
exl-id: ee8e1a3a-f1d4-412c-8767-16447113f0cd
source-git-commit: 6896d31a202957d7354c3dd5eb6459eda426e8d7
workflow-type: tm+mt
source-wordcount: '116'
ht-degree: 0%

---

# Sökvägar till baskatalog

Miljövariabeln `MAGE_DIRS` gör att du kan ange anpassade baskatalogsökvägar och fragment av bas-URL:er som används av Commerce-programmet för att skapa absoluta sökvägar till olika filer eller för att generera URL:er.

## Ange MAGE_DIRS

Ange en associativ array där nycklarna är konstanter från [\\Magento\\App\\Filesystem\\DirectoryList](https://github.com/magento/magento2/blob/2.4/lib/internal/Magento/Framework/App/Filesystem/DirectoryList.php) och värdena är absoluta sökvägar för kataloger eller deras URL-sökvägar.

Du kan ange `MAGE_DIRS` på något av följande sätt:

- [Ange värdet för bootstrap-parametrar](../bootstrap/set-parameters.md)
- Använd ett anpassat startpunktsskript som följande:

  ```php
  <?php
  /**
   * Copyright [first year code created] Adobe
   * All Rights Reserved.
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

I det föregående exemplet ställs sökvägarna för katalogerna `[cache]` och `[media]` in på `/mnt/nfs/cache` respektive `/mnt/nfs/media`.

