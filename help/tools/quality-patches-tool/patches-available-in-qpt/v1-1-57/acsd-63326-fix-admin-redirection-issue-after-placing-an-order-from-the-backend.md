---
title: 'ACSD-63326: Korrigera problem med administratörsomdirigering efter att en order har lagts från serverdelen'
description: Använd patchen ACSD-63326 för att åtgärda Adobe Commerce-problemet där administratören omdirigeras till en skadad sida efter att ha gjort en beställning från backend-enheten.
feature: Orders, Admin Workspace
role: Admin, Developer
exl-id: 8fffc3ad-11a4-4e62-b747-1c4c7b493ada
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# ACSD-63326: Korrigera problem med administratörsomdirigering efter att en order har lagts från serverdelen

Korrigeringen ACSD-63326 åtgärdar ett problem där administratören omdirigeras till en skadad sida efter att en beställning har gjorts från serverdelen. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.57 är installerad. Korrigerings-ID är ACSD-63326. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

Adobe Commerce (alla distributionsmetoder) 2.4.7-p2

**Kompatibel med Adobe Commerce-versioner:**

Adobe Commerce (alla distributionsmetoder) 2.4.2 - 2.4.7-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Administratörer dirigeras om till en sida med en trasig layout efter att en beställning för en kund har gjorts från bakgrunden.

<u>Steg som ska återskapas</u>:

1. Navigera till avsnittet **[!UICONTROL Customers]** på Admin-panelen.
1. Välj en kund och klicka på **[!UICONTROL Edit]**.
1. Klicka på **[!UICONTROL Create Order]** på den översta menyn på kundinformationssidan.
1. Välj butiken [!UICONTROL FR French] och lägg till en tillgänglig produkt i ordern.
1. Fyll i de obligatoriska uppgifterna i kassan och klicka på **[!UICONTROL Get shipping methods and rates]**.
1. Klicka på **[Skicka beställning]** för att montera beställningen.

<u>Förväntade resultat</u>:

Administratören dirigeras om till sidan med orderbekräftelsen eller tack för att den har rätt layout.

<u>Faktiska resultat</u>:

Administratören omdirigeras till en sida med en bruten layout. Layouten korrigeras först när sidan har uppdaterats.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.


## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
