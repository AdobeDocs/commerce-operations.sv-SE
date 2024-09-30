---
title: 'ACSD-52219: Löser problem med administratörsstödraster vid växling av bokmärkesvy'
description: Använd korrigeringsfilen ACSD-52219 för att åtgärda Adobe Commerce-problemet där administratörsrutnätets sparade filter inte fungerar som förväntat när du ofta växlar mellan olika bokmärkesvyer.
feature: Admin Workspace
role: Admin
source-git-commit: fe11599dbef283326db029b0312ad290cde0ba0a
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# ACSD-52219: Löser problem med administratörsstödrasterfilter vid växling av bokmärkesvy

Korrigeringen ACSD-52219 åtgärdar ett problem där administratörsrutnätets sparade filter inte fungerar som väntat när du ofta växlar mellan olika bokmärkesvyer. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) 1.1.39 är installerad. Korrigerings-ID är ACSD-52219. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.6

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6-p3

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

När du ofta växlar mellan olika bokmärkesvyer fungerar inte de sparade filtren i administratörsrutnät som de ska.

<u>Steg som ska återskapas</u>:

1. Gå till rutnätet [!DNL Sales Order] i Admin.
1. Skapa två till tre filter.
1. Kontrollera filterinställningarna genom att växla vyer för att säkerställa att de sparas korrekt.
1. Gå till Filter1 eller Filter2.
1. Uppdatera sidan för att uppdatera de data som visas.
1. Växla till en annan vy och lägg märke till att filtren inte ändras.
1. Observera att standardvyn nu visar filtrerade resultat, även om inget specifikt filter har angetts för den.

<u>Förväntade resultat</u>:

Filtren ändras inte och deras ursprungliga läge bevaras inte.

<u>Faktiska resultat</u>:

När du ändrar en vy blandas filtren ihop och rätt vy sparas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-knowledge-base/kb/announcements/commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
