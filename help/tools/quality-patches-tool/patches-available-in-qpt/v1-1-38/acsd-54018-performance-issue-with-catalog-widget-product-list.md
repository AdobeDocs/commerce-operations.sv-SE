---
title: 'ACSD-54018: Prestandaproblem med katalogwidgetens produktlista'
description: Använd patchen ACSD-54018 för att åtgärda Adobe Commerce-problemet där sidan läses in långsamt när du lägger till en katalogwidget-produktlista med villkor och attributtyp boolesk.
feature: Attributes, Catalog Management, Page Builder, Page Content, Storefront
role: Admin, Developer
exl-id: 2fb7ca37-78cc-45f4-86a3-d922cf4d1457
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '440'
ht-degree: 0%

---

# ACSD-54018: Prestandaproblem med katalogwidgetens produktlista

Korrigeringen ACSD-54018 åtgärdar ett problem där sidan läses in långsamt när en katalogwidget-produktlista läggs till med villkor och attributtyp boolesk. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.38 har installerats. Korrigerings-ID är ACSD-54018. Observera att problemet har åtgärdats i Adobe Commerce 2.4.6.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.5-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Sidan läses in långsamt när en katalogwidget-produktlista med villkor och attributtyp läggs till booleskt.

<u>Steg som ska återskapas</u>:

1. Generera 100 kB-produkter.
1. Skapa ett bool-attribut med scopet [!UICONTROL Store View].
1. Tilldela attribut till alla attributuppsättningar.
   * Tilldela attributvärdet *Yes* till alla produkter.
1. Gå nu till **[!UICONTROL Catalog]** > **[!UICONTROL Products]** och välj alla 100 kB-produkter.
   * Välj **[!UICONTROL Actions]** > **[!UICONTROL Update Attribute]**.
   * Ställ in bool-attributet på *Yes* och spara det.
   * Om du loggade ut i det här steget kontrollerar du *anteckningarna*.
1. Gå till CLI och kör `php bin/magento queue:con:start product_action_attribute.update`.
   * Se till att attributen för alla produkter uppdateras.
1. Gå nu till **[!UICONTROL Content]** > **[!UICONTROL Pages]** och skapa en ny sida.
1. Öppna **[!UICONTROL Page Builder]** > **[!UICONTROL Add row]** > **[!UICONTROL Add Content]** > **[!UICONTROL Products]**.
1. Välj *[!UICONTROL Select Products By]* = *[!UICONTROL Condition]*.
1. Ange villkoret *[!UICONTROL Created attribute]* till *[!UICONTROL Yes]* och spara det.
1. Gå till förgrunden och öppna den skapade sidan.
1. Inaktivera helsidescache och blockera HTML-cache.
1. Kontrollera sidans inläsningshastighet.
1. Läs in sidan igen några gånger och beräkna den genomsnittliga inläsningstiden.

<u>Förväntade resultat</u>:

Sidan läses in snabbt.

<u>Faktiska resultat</u>:

Det tar 5-10 sekunder att läsa in sidan.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning &#x200B;](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler &#x200B;](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
