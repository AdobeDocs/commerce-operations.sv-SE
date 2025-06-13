---
title: 'ACSD-60303: Problem med att lägga till administratörsorder har åtgärdats med HTML-minification aktiverat'
description: Använd patchen ACSD-60303 för att åtgärda Adobe Commerce-problemet där det inte går att beställa från Admin om HTML minification är aktiverat.
feature: Orders
role: Admin, Developer
exl-id: 85b987e7-9d65-4d15-8099-985dc227b66c
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '331'
ht-degree: 0%

---

# ACSD-60303: Problem med att lägga till administratörsorder har åtgärdats med HTML-minification aktiverat

Korrigeringen ACSD-60303 åtgärdar ett problem där en beställning från Admin inte kan göras om HTML-minification är aktiverat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.50 är installerad. Korrigerings-ID är ACSD-60303. Observera att problemet är planerat att åtgärdas i 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p8

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p9 - 2.4.4-p10, 2.4.5-p8 - 2.4.5-p9, 2.4.6-p6 - 2.4.6-p7

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Det går inte att lägga order från administrationspanelen när HTML minification är aktiverat.

<u>Steg som ska återskapas</u>:

1. Aktivera HTML minification.
1. Ange **[!UICONTROL Application Mode]** som *[!UICONTROL Production]*.
1. Skapa en beställning från panelen Admin.

<u>Förväntade resultat</u>:

Ordern har placerats ut.

<u>Faktiska resultat</u>:

Ordern skapas inte och följande fel loggas:

`report.CRITICAL: ParseError: syntax error, unexpected token "<<" in var/view_preprocessed/pub/static/vendor/magento/module-gift-wrapping/view/adminhtml/templates/order/create/info.phtml:1`

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
