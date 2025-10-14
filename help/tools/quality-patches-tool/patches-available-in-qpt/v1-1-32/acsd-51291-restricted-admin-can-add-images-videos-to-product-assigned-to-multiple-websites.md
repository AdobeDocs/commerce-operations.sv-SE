---
title: 'ACSD-51291: Begränsad administratör kan lägga till bilder/videor till produkter som tilldelats flera webbplatser'
description: Använd patchen ACSD-51291 för att åtgärda Adobe Commerce-problemet där en begränsad administratör med tillgång till en webbplats kan lägga till bilder/videor till en produkt som tilldelats flera webbplatser.
feature: Admin Workspace, Products, Page Content
role: Admin
exl-id: a4edd034-f718-4559-9993-11609f0d0efa
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# ACSD-51291: Begränsad administratör kan lägga till bilder/videor till produkter som tilldelats flera webbplatser

Korrigeringen ACSD-51291 åtgärdar ett problem där en begränsad administratör med tillgång till en webbplats kan lägga till bilder/videor till en produkt som tilldelats flera webbplatser. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.32 är installerad. Korrigerings-ID är ACSD-51291. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.4-p3, 2.4.5 - 2.4.5-p2

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En begränsad administratör med tillgång till en webbplats kan lägga till bilder/videor till en produkt som tilldelats flera webbplatser.

<u>Steg som ska återskapas</u>

1. Logga in som administratör.
1. Skapa en andra webbplats-, butiks- och butiksvy.
1. Skapa en andra administratörsroll med resurser endast för den andra webbplatsen, butiken och butiksvyn.
1. Skapa en andra administratör och tilldela den till den nya begränsade administratörsrollen.
1. Skapa en ny produkt och tilldela den till både standardwebbplatsen och de nya webbplatserna.
1. Logga ut från huvudadministratörsprofilen.
1. Logga in som ny begränsad administratör.
1. Redigera den skapade produkten som har tilldelats båda webbplatserna.
1. Öppna fliken **[!UICONTROL Images and Videos]**.

<u>Förväntade resultat</u>:

* Följande meddelande visas:

  *Begränsad administratör får endast utföra åtgärder med bilder eller videoklipp när administratören har behörighet till alla webbplatser som produkten är tilldelad till.*

* Knappen **[!UICONTROL Add Video]** är inte aktiv.

<u>Faktiska resultat</u>:

Den begränsade administratören kan lägga till bilder och videoklipp även när produkten har tilldelats en webbplats som den inte har tillgång till.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
