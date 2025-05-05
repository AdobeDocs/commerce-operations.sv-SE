---
title: 'ACSD-62951: Korrigerar saknade objekt och summor i [!UICONTROL Credit Memo] e-postmeddelanden som skickas via REST API'
description: Använd patchen ACSD-62951 för att åtgärda Adobe Commerce-problemet där e-postmeddelandet [!UICONTROL Credit Memo] skickas utan att inkludera orderartiklarna och summorna.
feature: REST
role: Admin, Developer
source-git-commit: bfefe2bbe2046bda967b0a14f238919452935400
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# ACSD-62951: Korrigerar saknade objekt och summor i *[!UICONTROL Credit Memo]* e-postmeddelanden som skickas via REST API

Korrigeringen ACSD-62951 åtgärdar ett problem där e-postmeddelandet [!UICONTROL Credit Memo] skickas utan att några orderposter eller summor inkluderas. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 är installerad. Korrigerings-ID är ACSD-62951. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.5-p10

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

E-postmeddelandet *[!UICONTROL Credit Memo]* som skickas när en kreditnota skapas via REST API `POST V1/order/:orderId/refund` innehåller inte orderartiklarna och summorna.

<u>Steg som ska återskapas</u>:

1. Skapa en beställning med valfri produkt.
1. Leverera och fakturera ordern. Kontrollera att fakturameddelandet skickas och att det innehåller produktinformationen.
1. Generera en Admin Token med API-klienten.
1. Använd token för att skapa en kreditnota via REST API.
   1. Slutpunkt: `POST V1/order/:orderId/refund`
   1. Begär nyttolast:

      ```
      {  
          "notify": true,  
          "items": [  
              {  
                  "order_item_id": 1,  
                  "qty": 1  
              }  
          ]  
      }  
      ```

<u>Förväntade resultat</u>:

E-postmeddelandet *[!UICONTROL Credit Memo]* ska innehålla de återbetalade artiklarna och summorna

<u>Faktiska resultat</u>:

E-postmeddelandet *[!UICONTROL Credit Memo]* innehåller inga objekt eller summor, vilket resulterar i ofullständig information.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
