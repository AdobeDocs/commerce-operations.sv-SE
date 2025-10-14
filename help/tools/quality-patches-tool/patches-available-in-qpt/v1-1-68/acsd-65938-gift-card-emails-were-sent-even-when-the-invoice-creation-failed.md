---
title: 'ACSD-65938: E-post med presentkort skickas även när det inte gick att skapa fakturan'
description: Använd patchen ACSD-65938 för att åtgärda Adobe Commerce-problemet där presentkortsms skickades innan fakturan sparades och verkställdes, och se till att e-postmeddelanden utlöses när fakturan har sparats på rätt sätt.
feature: Orders, Checkout
role: Admin, Developer
type: Troubleshooting
source-git-commit: b688875cd0a7bfc07dba77254605e7055ae7cca4
workflow-type: tm+mt
source-wordcount: '385'
ht-degree: 0%

---


# ACSD-65938: E-post med presentkort skickas även när det inte gick att skapa fakturan

Korrigeringen för ACSD-65938 löser ett problem där presentkortsmeddelanden skickades innan fakturan sparades och verkställdes. Med den här korrigeringen aktiveras e-postmeddelanden först när fakturan har sparats. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.68 har installerats. Korrigerings-ID är ACSD-65938. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.8-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

E-postmeddelanden med presentkort skickades innan fakturan kunde skapas och sparas, vilket resulterar i att e-postmeddelanden skickas även när det inte gick att skapa fakturan.

<u>Steg som ska återskapas</u>:

1. Logga in på panelen **[!UICONTROL Admin]**.
2. Navigera till **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL Sales]** > **[!UICONTROL Gift Cards]** > **[!UICONTROL Gift Card General Settings]** och ställ in **[!UICONTROL Generate Gift Card Account when Order Item is]** på *Fakturerad*.
3. Skapa en ny presentkortsprodukt.
4. Lägg till presentkortsprodukten i kundvagnen och fortsätt till **[!UICONTROL checkout]**. Du kan använda **[!UICONTROL Check/Money Order]** som betalningsmetod.
5. Beställ.
6. Ändra `OrderRepository` för att simulera ett undantag under orderplacering.
7. Skicka en POST-begäran till `rest/default/V1/order/<ORDER_ID>/invoice` med följande nyttolast:

   ```
   {
     "capture": true,
     "notify": true
   }
   ```


<u>Förväntade resultat</u>:

Ingen e-postadress för presentkort ska skickas om det inte går att skapa fakturan.

<u>Faktiska resultat</u>:

Presentkortets e-post skickas trots att det inte gick att skapa fakturan.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
