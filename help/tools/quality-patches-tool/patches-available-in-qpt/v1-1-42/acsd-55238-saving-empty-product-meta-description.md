---
title: 'ACSD-55238: Sparar den tomma metabeskrivningen för produkten'
description: Använd patchen ACSD-55238 för att åtgärda problemet med Adobe Commerce där en produktbeskrivning som innehåller HTML-kod som genererats av  [!DNL Page Builder]  eller en annan HTML-redigerare alltid visas i metabeskrivningen och det inte finns något sätt att ange den som tom.
feature: Products, Page Builder, Page Content
role: Admin, Developer
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '405'
ht-degree: 0%

---

# ACSD-55238: Sparar den tomma produktmetabeskrivningen

Korrigeringen ACSD-55238 åtgärdar ett problem där en produktbeskrivning som innehåller HTML-kod som har genererats av en HTML-redigerare alltid visas i metabeskrivningen. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.42 är installerad. Korrigerings-ID är ACSD-55238. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

En produktbeskrivning som innehåller HTML-kod som har genererats av [!DNL Page Builder] eller en annan HTML-redigerare visas alltid i metabeskrivningen och det går inte att ange den som tom.

<u>Steg som ska återskapas</u>:

1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Content]** > **[!UICONTROL Block]** och skapa ett nytt block med valfritt innehåll.
1. Gå till **[!UICONTROL Admin]** > **[!UICONTROL Catalog]** > **[!UICONTROL Product]** och skapa en ny produkt. Ange metabeskrivningen som tom.
1. Lägg till blocket som skapats ovan med *[!DNL Page Builder]* på fliken *[!UICONTROL Content]* och spara produkten.
1. Öppna produkten i butiken och kontrollera dokumentelementet `meta name = "description"`.

<u>Förväntade resultat</u>:

Metabeskrivningen är tom.

<u>Faktiska resultat</u>:

När en produkt har ett block i beskrivningen används den för produktmetabeskrivningen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
