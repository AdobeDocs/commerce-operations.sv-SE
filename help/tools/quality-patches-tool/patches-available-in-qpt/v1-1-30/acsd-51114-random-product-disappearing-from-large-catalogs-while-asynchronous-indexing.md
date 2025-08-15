---
title: 'ACSD-51114: Slumpmässiga produkter försvinner från stora kataloger när asynkron indexering är aktiverat'
description: Använd patchen ACSD-51114 för att åtgärda problemet med slumpmässiga Adobe Commerce-produkter som försvinner från stora kataloger när asynkron indexering är aktiverat.
feature: Catalog Management, Categories, Products
role: Admin
exl-id: ab1816ef-fb09-46e7-8102-32865f806874
type: Troubleshooting
source-git-commit: 7fdb02a6d89d50ea593c5fd99d78101f89198424
workflow-type: tm+mt
source-wordcount: '375'
ht-degree: 0%

---

# ACSD-51114: Slumpmässiga produkter försvinner från stora kataloger när asynkron indexering är aktiverat

>[!NOTE]
>
>Den här korrigeringen är föråldrad.

Korrigeringen ACSD-51114 åtgärdar problemet att Slumpmässiga produkter försvinner från stora kataloger när asynkron indexering är aktiverat. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.30 är installerad. Korrigerings-ID är ACSD-5114. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.4.3 - 2.4.6

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]:Search för korrigeringssidan]. Använd patch-ID som söknyckelord för att hitta korrigeringen.

## Problem

Slumpmässiga produkter försvinner från stora kataloger när asynkron indexering är aktiverat.

<u>Steg som ska återskapas</u>:

1. Skapa en uppsättning med tio produkter.
1. Ställ in alla indexerare till läget **[!UICONTROL Update on Save]**.
1. Skapa en kategori och tilldela alla produkter till den.
1. Inaktivera alla produkter.
1. Öppna kategorin och kontrollera att det inte finns några produkter där.
1. Ställ in alla indexerare till läget **[!UICONTROL Update on Schedule]**.
1. Ange `DEFAULT_BATCH_SIZE` till 2 i `lib/internal/Magento/Framework/Mview/View.php#L31`.
1. Aktivera produkter i följande ordning: 1, 9, 2, 5, 10, 3.
1. Kör cron, kommando.
1. Öppna kategorin igen.

<u>Förväntade resultat</u>:

Alla aktiverade produkter visas.

<u>Faktiska resultat</u>:

Alla aktiverade produkter visas inte.

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html?lang=sv-SE) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/sv/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html?lang=sv-SE) i [!DNL Quality Patches Tool]-handboken.
