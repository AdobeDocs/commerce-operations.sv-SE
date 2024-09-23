---
title: 'ACSD-52287: Status för arkiverade order ändras inte'
description: Använd patchen ACSD-52287 för att åtgärda Adobe Commerce-problemet där status för arkiverade order inte ändras från *slutförd* till *stängd* på rutnätet när kreditnotan har skickats.
feature: Orders, Checkout
role: Admin, Developer
source-git-commit: 49ac8ad1f174546fcc0454645b2480a40ead2924
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 1%

---

# ACSD-52287: Status för arkiverade order ändras inte

Korrigeringen ACSD-52287 åtgärdar ett problem där status för arkiverade order inte ändras från *slutförd* till *stängd* i rutnätet efter att kreditnotan har skickats. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.38 har installerats. Korrigerings-ID är ACSD-52287. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Status för arkiverade order ändras inte från *slutförd* till *stängd* i rutnätet efter att kreditnotan har skickats.

<u>Steg som ska återskapas</u>:

1. Konfigurera *[!UICONTROL Asynchronous Indexing]*.
   * Gå till **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** på sidlisten Admin.
   * Expandera avsnittet **[!UICONTROL Advanced]** i den vänstra panelen och välj **[!UICONTROL Developer]** under.
   * Expandera avsnittet **[!UICONTROL Grid Settings]**.
   * Ange *[!UICONTROL Asynchronous indexing]* som *Ja*.
   * Klicka på **[!UICONTROL Save Config]**.
1. Konfigurera *[!UICONTROL Order Archive]*.
   * Gå till **[!UICONTROL Stores]** > **[!UICONTROL Settings]** > **[!UICONTROL Configuration]** på sidlisten Admin.
   * Expandera avsnittet **[!UICONTROL Sales]** i den vänstra panelen och välj **[!UICONTROL Sales]** under.
   * Expandera avsnittet **[!UICONTROL Orders, Invoices, Shipments, Credit Memos Archiving]**.
   * Ange *[!UICONTROL Enable Archiving]* till *Ja* (behåll resten av konfigurationerna som standard).
   * Klicka på **[!UICONTROL Save Config]**.
1. Placera en ordning i förgrunden.
1. Kör [!DNL cron] om du vill att ordningen ska visas i *[!UICONTROL Admin Order Grid]*.
1. Fakturera och skicka ordern för att uppdatera orderstatusen till *Fullständig*.
1. Kör [!DNL cron] för att uppdatera *[!UICONTROL Sales Order Grid]* med den senaste orderstatusen.
1. Arkivera ordern.
1. Gå till *[!UICONTROL Archived order grid]*.
1. Öppna den arkiverade ordern och återbetala ordern offline genom att skapa en [!UICONTROL Credit Memo] som gör [!UICONTROL Order status]: *Stängd*.
1. Kör [!DNL cron] några gånger.
1. Kontrollera *[!UICONTROL Archived order grid]* för den nya orderstatusen.

<u>Förväntade resultat</u>:

Ordningen visas som *Stängd*.

<u>Faktiska resultat</u>:

Ordningen visas som *Fullständig*.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](https://experienceleague.adobe.com/docs/commerce-operations/tools/quality-patches-tool/usage.html) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
