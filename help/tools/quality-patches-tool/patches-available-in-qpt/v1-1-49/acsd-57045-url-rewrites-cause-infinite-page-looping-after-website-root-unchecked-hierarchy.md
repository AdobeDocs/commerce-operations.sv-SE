---
title: 'ACSD-57045: URL-omskrivningar orsakar oändliga sidloopar efter [!UICONTROL Website Root] avmarkerat från [!UICONTROL Hierarchy]'
description: Använd korrigeringen ACSD-57045 för att åtgärda Adobe Commerce-problemet där URL-omskrivningar orsakar oändliga sidupprepningar efter att [!UICONTROL Website Root] har avmarkerats från [!UICONTROL Hierarchy].
feature: CMS
role: Admin, Developer
exl-id: 7beaee40-a392-4644-917e-c507e79bddcc
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# ACSD-57045: URL-omskrivningar orsakar oändliga sidloopar efter [!UICONTROL Website Root] avmarkerat från [!UICONTROL Hierarchy]

Korrigeringen ACSD-57045 åtgärdar ett problem där URL-omskrivningar orsakar oändliga sidupprepningar efter att **[!UICONTROL Website Root]** har avmarkerats från **[!UICONTROL Hierarchy]**. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.49 är installerad. Korrigerings-ID är ACSD-57045. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.5.0.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p7

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

URL-omskrivningar orsakar oändliga sidupprepningar efter att **[!UICONTROL Website Root]** har avmarkerats från **[!UICONTROL Hierarchy]**.

<u>Steg som ska återskapas</u>:

1. Skapa en CMS-sida med namnet *Test-Parent*.
1. Skapa en sida med namnet *Test-Child*. I avsnittet **[!UICONTROL Hierarchy]** väljer du **[!UICONTROL Website Root]** > **[!UICONTROL Parent]** och sparar.
1. Gå till **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]**.
1. Observera att det finns två nya omskrivningar:
   * Begär sökväg till *Test-Parent* som pekar på *cms/page/view/page_id/ID_NUMBER_FOR_PAGE*
   * Begär sökväg till *Test-Child* som pekar på *cms/page/view/page_id/ID_NUMBER_FOR_PAGE*
1. Gå till butiken och lägg till *test-child* i URL:en. Du bör se den underordnade sidan.
1. Gör samma sak, men lägg till *test-parent/test-child/* i URL:en och se samma sida.
1. Gå till **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]** och välj **[!UICONTROL Add URL Rewrite]**. Välj följande inställningar:
   * Typ: *Egen*
   * Sökväg till begäran: *test-parent/test-child*
   * Målsökväg: *test-child*
   * Omdirigeringstyp: *Permanent (301)*
1. Gå till sökvägen *test-parent/test-child* och omdirigera dig till *test-child*.
1. Redigera den underordnade sidan (**[!UICONTROL Content]** > **[!UICONTROL Elements]** > **[!UICONTROL Pages]** > Välj underordnad och välj **[!UICONTROL Edit]**).
1. Under avsnittet **[!UICONTROL Hierarchy]** låter du *Test-Parent* vara markerat men avmarkerar **[!UICONTROL Website Root]** och sparar.
1. Gå till **[!UICONTROL Marketing]** > **[!UICONTROL URL Rewrites]** och observera att den ursprungliga omdirigeringen *test-child* till *cms/page/view/page_id* saknas, och att den då ersätts med en sökväg som pekar på *test-child* till *test-parent/test-child*.
1. Besök butiken och försök att besöka sidan *Test-Child*.

<u>Förväntade resultat</u>:

Sidan *Test-Child* öppnas.

<u>Faktiska resultat</u>:

Sidan *Test-Child* är inte öppen. Webbläsaren försöker öppna sidan *test-parent/test-child* i en oändlig slinga.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
