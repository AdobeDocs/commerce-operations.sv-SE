---
title: 'ACSD-64467: WYSIWYG-redigeraren är tom efter att kategoribeskrivningen sparats på butiksvynivå'
description: Använd patchen ACSD-64467 för att åtgärda Adobe Commerce-problemet där WYSIWYG-redigeraren ser tom ut när du har sparat en kategoribeskrivning på butiksvynivå.
feature: Page Content
role: Admin, Developer
exl-id: 8bc1794f-ace1-4719-9fff-194dbd701ab6
source-git-commit: b71447d5dac3208e537b29204dc8d47e8838f584
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# ACSD-64467: WYSIWYG-redigeraren är tom efter att kategoribeskrivningen sparats på butiksvynivå

Korrigeringen ACSD-64467 åtgärdar ett problem där WYSIWYG-redigeraren ser tom ut när en kategoribeskrivning har sparats på butiksvynivå. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) 1.1.61 har installerats. Korrigerings-ID är ACSD-64467. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.8.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7-p3

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.7 - 2.4.7-p4

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

WYSIWYG-redigeraren visas tom när du har sparat en kategoribeskrivning på butiksvynivå.

<u>Steg som ska återskapas</u>:

1. Redigera en kategori på butiksvynivå i Commerce Admin.
1. Avmarkera kryssrutan *[!UICONTROL Use default value]* bredvid kategoribeskrivningen.
1. Ange en beskrivning i WYSIWYG Editor.
1. Klicka på **[!UICONTROL Save]**.

<u>Förväntade resultat</u>:

Beskrivningen sparas och visas korrekt.

<u>Faktiska resultat</u>:

Beskrivningen är tom efter att sidan har lästs in igen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool]: Ett självbetjäningsverktyg för kvalitetspatchar](/help/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches.md) i verktygshandboken.
