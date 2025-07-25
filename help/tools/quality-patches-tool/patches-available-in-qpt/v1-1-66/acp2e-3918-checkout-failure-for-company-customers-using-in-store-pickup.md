---
title: 'ACP2E-3918: Utcheckningsfel för företagskunder som använder upphämtning i butik'
description: Använd korrigeringsfilen ACP2E-3918 för att åtgärda Adobe Commerce-problemet där utcheckningen misslyckas för inloggade företagskunder som använder en butiksupphämtning utan standardfaktureringsadress.
feature: B2B, Companies, Purchase Orders
role: Admin, Developer
type: Troubleshooting
source-git-commit: 1295af44422ffbd67a3666f1a96a75af0a4e3c81
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# ACP2E-3918: Utcheckningsfel för företagskunder som använder upphämtning i butik

Programfixen ACP2E-3918 åtgärdar ett problem där utcheckningen misslyckas för inloggade företagskunder som använder en butiksupphämtning utan standardfaktureringsadress. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.66 har installerats. Korrigerings-ID är ACP2E-3918. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.9.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p4

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.8

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Utcheckningen misslyckas när en inloggad företagskund utan standardadress försöker lägga en inköpsorder med hjälp av en butiksupphämtning.

<u>Steg som ska återskapas</u>:

1. Aktivera **[!UICONTROL Purchase Orders]**.
1. Skapa en **[!UICONTROL Company]** och aktivera **[!UICONTROL Purchase Orders]** för den.
1. Skapa en **[!UICONTROL Company User]** utan sparade adresser.
1. Aktivera leveransmetoden **[!UICONTROL In-Store Delivery]**.
1. Lägg till en lagerkälla.
1. Lägg till ett lagerlager.
1. Tilldela lager till en produkt.
1. Logga in som företagsanvändare i förgrunden.
1. Lägg till produkter i **[!UICONTROL Cart]**.
1. Gå till kassan.
1. Välj **[!UICONTROL In-Store Pick Up]** i leveranssteget.
1. Fortsätt med betalningen.

<u>Förväntade resultat</u>:

Betalningssteget ska läsas in korrekt under utcheckningen och inga fel ska visas i webbläsarkonsolen.

<u>Faktiska resultat</u>:

Betalningssteget läses inte in och följande JavaScript-fel visas i webbläsarkonsolen:

```
        Uncaught TypeError: Unable to process binding "text: function(){return currentBillingAddress().street.join(', ') }"
        Message: Cannot read properties of undefined (reading 'join')
```

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
