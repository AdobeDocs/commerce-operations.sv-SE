---
title: 'ACSD-49013: E-postbekräftelse har inte översatts till webbplatsens nationella inställningar'
description: Använd korrigeringsfilen ACSD-49013 för att åtgärda Adobe Commerce-problemet där e-postbekräftelse inte översätts till webbplatsens språkområde när du skapar kunder som använder satsvis-API.
feature: Admin Workspace, Communications
role: Admin
exl-id: 1b0dc6aa-d5ee-4adf-882d-88f29a7eab34
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# ACSD-49013: E-postbekräftelse har inte översatts till webbplatsens nationella inställningar

Korrigeringen ACSD-49013 åtgärdar ett problem där e-postbekräftelse inte översätts till webbplatsens språkområde när kunder skapas med hjälp av bulk-API. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.27 är installerad. Korrigerings-ID är ACSD-49013. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

E-postbekräftelse översätts inte till webbplatsens språkområde när du skapar kunder som använder bulk-API.

<u>Steg som ska återskapas</u>:

1. Installera en annan språkinställning som `de_DE`.
1. Konfigurera *RabbitMQ*.
1. Kör `bin/magento setup:upgrade` för att installera köerna i RabbitMQ och konfigurera språkpaketet.
1. Skapa ytterligare en webbplats i [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL All Stores]**.
1. Ange språkinställningen för den nya webbplatsen till `de_DE` i [!UICONTROL Admin] > **[!UICONTROL Stores]** > **[!UICONTROL Configuration]** > **[!UICONTROL General]** > **[!UICONTROL Locale Options]**.
1. Utför ett API-anrop för att skapa ett kundkonto med hjälp av bulk-API. Använd motsvarande `website_id`.

   `Endpoint: /rest/async/bulk/V1/customers`

   ```
   [{
       "customer": {
       "email": "test@example.com",
       "firstname": "test",
       "lastname": "test",
       "website_id": 2
       },
       "password": "Passw0rd!"
   }]
   ```

1. Kör `bin/magento queue:consumers:start async.operations.all --single-thread --max-messages=10`.
1. Du kan se att kundkontot skapas korrekt på den angivna webbplatsen.
1. Kontrollera e-postmeddelandet som tagits emot för kundregistrering.

<u>Förväntade resultat</u>:

Eftersom kunden skapas på en viss webbplats skickas e-postmeddelandet med den webbplatsens språkinställning.

<u>Faktiska resultat</u>:

Kunden skapas på rätt sätt på den angivna webbplatsen, men registreringens e-post skickas med standardspråket när bulk-API används.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
