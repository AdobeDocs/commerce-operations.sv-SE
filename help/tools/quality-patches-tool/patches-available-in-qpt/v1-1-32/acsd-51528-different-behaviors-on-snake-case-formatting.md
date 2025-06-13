---
title: 'ACSD-51528: Olika beteenden för formatering med orm_case'
description: Använd korrigeringsfilen ACSD-51528 för att åtgärda Adobe Commerce-problemet där det finns olika beteenden för formatering med orm_case.
feature: Variables
role: Admin
exl-id: 5f2add4b-8209-47a7-bfbd-cc434a050f0f
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# ACSD-51528: Olika beteenden för formatering med orm_case

Korrigeringen ACSD-51528 korrigerar olika beteenden för formatering med orm_case. Den här korrigeringen är tillgänglig när [!DNL Quality Patches Tool (QPT)] 1.1.32 har installerats. Korrigerings-ID är ACSD-51528. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5-p1

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.5 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Olika beteenden för formatering av orm_case.

<u>Steg som ska återskapas</u>:

1. Testa funktionen `\Magento\Framework\Api\DataObjectHelper::populateWithArray` med olika egenskapsnamn.
1. Egenskaperna med namn som *NewPName* ska omformas till *new_p_name*, i stället omformas de till *new_pname*.
1. När funktionen *getNewPName* används i objektet returneras *null* eftersom *Abstrakt modell* korrekt omformar anropet till *new_p_name* vilket gör båda funktionerna inkompatibla med varandra.

<u>Förväntade resultat</u>

Funktionen **[!UICONTROL populateWithArray]** ska omforma objektegenskaperna till snake_case korrekt, så att den blir kompatibel med **[!DNL AbstractModel's]** `Getters` och `Setters`.

<u>Faktiska resultat</u>

När du använder funktionen **[!UICONTROL populateWithArray]** kommer objektegenskaper som innehåller två eller flera versala bokstäver i en rad i namnet att göra så att ormen_case-omformningen blir felaktig i den slutliga datarrayen.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
