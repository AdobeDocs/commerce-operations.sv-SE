---
title: 'ACSD-64532: Variabeln ENV inställd på *false* behandlas som en sträng *false* i stället för BOOLEAN *FALSE*'
description: Använd patchen ACSD-64532 för att åtgärda Adobe Commerce-problemet där variabeln "ENV" som är inställd på *false* behandlas som en sträng *false* i stället för som "BOOLEAN" *FALSE*.
feature: Variables
role: Admin, Developer
exl-id: 7940df1f-d527-4b57-bde7-7a0216b12436
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 0%

---

# ACSD-64532: ENV-variabeln som är inställd på &quot;false&quot; behandlas som strängen &quot;false&quot; i stället för BOOLEAN FALSE

Korrigeringen ACSD-64532 åtgärdar ett problem där variabeln `ENV` som är inställd på *false* behandlas som en sträng *false* i stället för som en `BOOLEAN` *FALSE* . Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.62 har installerats. Korrigerings-ID är ACSD-64532. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**
Adobe Commerce (alla distributionsmetoder) 2.4.6-p8

**Kompatibel med Adobe Commerce-versioner:**
Adobe Commerce (alla distributionsmetoder) 2.4.6-p2 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

`ENV`-variabeln som är inställd på *false* behandlas som en sträng *false* i stället för som en `BOOLEAN` *FALSE* .

<u>Steg som ska återskapas</u>:
1. Lägg till `env:MAGENTO_DC_INDEXER__USE_APPLICATION_LOCK` med värdet *false* i miljövariabler i Adobe Commerce i molninfrastrukturen.
1. Vänta på omdistribution.
1. Kör skriptet och kontrollera värdet:

   ```php
   <?php
   require '../app/bootstrap.php';
   $bootstrap = \Magento\Framework\App\Bootstrap::create(BP, $_SERVER);
   $objectManager = $bootstrap->getObjectManager();
   $deploymentConfig = $objectManager->get('Magento\Framework\App\DeploymentConfig');
   $useAppLock = $deploymentConfig->get('indexer/use_application_lock');
   
   var_dump($useAppLock);
   
   $configParsedValue = $deploymentConfig->get('indexer/use_application_lock') ?: false;
   
   var_dump($configParsedValue); 
   ```

<u>Förväntade resultat</u>:
`$configParsedValue` , som är resultatet av metoden `isUseApplicationLock()` , måste returnera ett negativt värde för att kunna tolkas korrekt inuti metoden `\Magento\Indexer\Model\Mview\View\State::getStatus()` .

<u>Faktiska resultat</u>:
`$configParsedValue` har värdet *`string(5) false`* .

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:
* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
