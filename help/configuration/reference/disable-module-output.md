---
title: Inaktivera modulutdata
description: Lär dig hur du inaktiverar modulutdata.
exl-id: af556bf5-8454-4d65-8ac8-4a64c108f092
source-git-commit: 95ffff39d82cc9027fa633dffedf15193040802d
workflow-type: tm+mt
source-wordcount: '386'
ht-degree: 0%

---

# Inaktivera modulutdata

Som standard konfigureras alla moduler så att modulutdata kan skrivas till en vy. Om du stänger av utdata kan du inaktivera en modul som inte kan inaktiveras på grund av allvarliga beroenden.

Till exempel `Customer` är beroende av `Review` så att `Review` kan inte inaktiveras. Om du inte vill att kunderna ska kunna tillhandahålla granskningar kan du stänga av utdata från `Review` -modul.

>[!INFO]
>
>Om en handlare använde administratören för att inaktivera modulutdata i en tidigare version måste du konfigurera systemet manuellt för att migrera dessa inställningar.

Inaktiveringen av utdata utförs i följande klasser:

- [\Magento\Framework\View\Element\AbstractBlock::toHtml](https://github.com/magento/magento2/blob/36097739bbb0b8939ad9a2a0dadee64318153dca/lib/internal/Magento/Framework/View/Element/AbstractBlock.php#L651)
- [\Magento\Backend\Block\Template::isOutputEnabled](https://github.com/magento/magento2/blob/0c786907ffe03d0e2990612eec16ee58b00379c5/app/code/Magento/Backend/Block/Template.php#L96)

>[!WARNING]
>
>Modulen inaktiveras inte om du inaktiverar modulutdata. Modulen är fortfarande aktiverad och fungerar, men inget block, ingen sida eller inget fält återges på framänden eller bakänden.

## Inaktivera modulutdata i en pipeline-distribution

Så här inaktiverar du modulutdata i pipeline-distributionen eller någon annan distribution, med flera instanser av Commerce-programmet:

1. Redigera `Backend` modulens `config.xml` -fil.
1. Exportera konfigurationsändringarna.

### Redigera `Backend` modul `config.xml` fil

1. Arkivera originalet `config.xml` -fil.
1. Lägg till rader som liknar följande i `<Magento_install_dir>/vendor/magento/module-backend/etc/config.xml` fil, direkt under `<default>` element:

   ```xml
   <advanced>
       <modules_disable_output>
           <Magento_Newsletter>1</Magento_Newsletter>
       </modules_disable_output>
   </advanced>
   ```

   Här:

   - `<modules_disable_output>` innehåller en lista med moduler.
   - `<Magento_Newsletter></Magento_Newsletter>` anger vilken modul som utdata ska inaktiveras för.
   - `1` är flaggan som inaktiverar utdata för `Magento_Newsletter` -modul.

Som ett exempelresultat av den här konfigurationen kan kunderna inte längre registrera sig för att få nyhetsbrev.

### Exportera konfigurationsändringarna

Kör följande kommando för att exportera konfigurationsändringarna:

```bash
bin/magento app:config:dump
```

Resultatet skrivs till `<Magento_install_dir>/app/etc/config.php` -fil.

Rensa sedan cacheminnet för att aktivera den nya inställningen:

```bash
bin/magento cache:clean config
```

Se [Exportera konfigurationen](../cli/export-configuration.md).

## Inaktivera modulutdata i en enkel distribution

Det är enklare att inaktivera modulutdata i en enda instans av Commerce eftersom ändringarna inte behöver distribueras.

1. Arkivera originalet `<Magento_install_dir>/app/etc/config.php` -fil.
1. Lägg till `advanced` och `modules_disable_output` avsnitt till `config.php` fil (om de inte finns):

   ```php
   'system' =>
     array (
       'websites' =>
       array (
         'base' =>
         array (
           'advanced' =>
           array (
             'modules_disable_output' =>
             array (
               'Magento_Review' => '1',
             ),
           ),
         ),
       ),
     ),
   ```

I det här exemplet används utdata för `Magento_Review` har inaktiverats och kunderna kan inte längre granska produkter.
Om du vill återaktivera utdata anger du värdet till `0`.
