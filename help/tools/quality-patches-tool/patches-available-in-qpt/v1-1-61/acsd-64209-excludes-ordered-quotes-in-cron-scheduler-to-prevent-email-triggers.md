---
title: 'ACSD-64209: Kronschemaläggaren hämtar överlåtbara offerter utan att utesluta [!UICONTROL Ordered] citattecken'
description: Använd korrigeringsfilen ACSD-64209 för att åtgärda Adobe Commerce-problemet där cron Scheduler hämtar alla överlåtbara offerter utan att utesluta dem med statusen [!UICONTROL Ordered], vilket medför att ett e-postmeddelande eller e-postmeddelande utlöses.
feature:  B2B, Communications
role: Admin, Developer
exl-id: 51ba0edc-ad0c-4e32-acd7-2337a62bff53
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '415'
ht-degree: 0%

---

# ACSD-64209: Kronschemaläggaren hämtar överlåtbara offerter utan att utesluta [!UICONTROL Ordered] citattecken

Korrigeringen ACSD-64209 åtgärdar ett problem där cron Scheduler hämtar alla överlåtbara offerter utan att utesluta dem med statusen **[!UICONTROL Ordered]**, vilket medför att ett e-postmeddelande eller e-postmeddelande utlöses. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 har installerats. Korrigerings-ID är ACSD-64209. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Kronschemaläggaren hämtar alla överlåtbara offerter utan att utesluta dem med statusen **[!UICONTROL Ordered]**, vilket medför att ett e-postmeddelande eller e-postmeddelanden utlöses.

<u>Steg som ska återskapas</u>:


1. På sidofältet *Admin* går du till **[!UICONTROL Stores]** > *[!UICONTROL Settings]* > **[!UICONTROL Configuration]** > **[!UICONTROL B2B Features]** och aktiverar Company och B2B Quote.
1. Ange **[!UICONTROL Default Expiration Period]** till **&#x200B; i *Admin* > &#x200B;** [!UICONTROL Stores] **&#x200B; > *[!UICONTROL Settings]* > &#x200B;** [!UICONTROL Configuration] **&#x200B; > &#x200B;** [!UICONTROL Sales] **&#x200B; > &#x200B;** [!UICONTROL Quotes] **&#x200B; > &#x200B;** [!UICONTROL General]**.
1. Skapa ett företag, aktivera det och logga in som företagsadministratör.
1. Lägg en produkt i kundvagnen.
1. Begär en offert.
1. Gå till **[!UICONTROL Sales]** > **[!UICONTROL Quotes]** på sidofältet *Admin*.
1. Markera den skapade offerten och klicka på **[!UICONTROL Send]** för att skicka tillbaka offerten till köparen.
1. Logga in som företagsadministratör i butiken.
1. Markera offerten och klicka på **[!UICONTROL Proceed to checkout]** för att slutföra köpet.
1. Kontrollera att offertens status är **[!UICONTROL Ordered]** och att inga fler åtgärder är möjliga i butiken.
1. Utlös cron-jobbet `negotiable_quote_send_emails`.


<u>Förväntade resultat</u>:

Eftersom offerten har beställts och inga ytterligare åtgärder kan vidtas, bör inga e-postmeddelanden om att offerten har gått ut skickas.

<u>Faktiska resultat</u>:

Ett e-postmeddelande, *offerten, upphör snart*, skickas.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
