---
title: 'ACSD-49877: Automatisk uppspelning av video fungerar inte på mobilen  [!DNL Safari]'
description: Använd korrigeringsfilen ACSD-49877 för att åtgärda Adobe Commerce-problemet där alternativet för automatisk uppspelning av video inte fungerar på mobilen [!DNL Safari] när videon är länkad direkt till en fjärrvideofil.
feature: CMS
role: Admin
exl-id: aa2557e2-4bed-4004-b9bc-36c59f1e9cdc
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 0%

---

# ACSD-49877: Automatisk uppspelning av video fungerar inte på mobilen [!DNL Safari]

ACSD-49877 åtgärdar ett problem där alternativet för automatisk uppspelning på mobilen [!DNL Safari] inte fungerar när videon är länkad direkt till en fjärrvideofil. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30 är installerad. Korrigerings-ID är ACSD-49877. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du paketet [!magento/quality-patches] till den senaste versionen och kontrollerar kompatibiliteten för [[!DNL Quality Patches Tool]: Sök efter korrigeringar]. Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Automatisk uppspelning av video fungerar inte på mobilen [!DNL Safari] när videon är länkad direkt till en fjärrvideofil och inte en direktuppspelningstjänst.

<u>Förutsättningar</u>:
[!DNL Page Builder] -moduler är installerade.

<u>Steg som ska återskapas</u>:

1. Skapa en ny CMS-sida och redigera **[!UICONTROL Content Value]** med [!DNL Page Builder].
1. Lägg till ett *Tab*-element i innehållet och lägg till ett *Video-element* i *fliken*.
1. Klicka nu på kugghjulsknappen för att redigera *videoelementet*.
1. Lägg till en länk till en mp4-videofil i fältet [!UICONTROL Video URL].
1. Markera fältet **[!UICONTROL Autoplay]** som *Ja*.
1. Klicka på **[!UICONTROL Save]**.
1. Öppna den nyligen skapade sidan på [!DNL Safari] med en iPhone.

<u>Förväntade resultat</u>

Alternativet för automatisk uppspelning fungerar på [!DNL Safari] med en iPhone.

<u>Faktiska resultat</u>

Alternativet för automatisk uppspelning fungerar inte på [!DNL Safari] med en iPhone.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
