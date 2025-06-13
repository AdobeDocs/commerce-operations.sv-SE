---
title: 'ACSD-48070: Undantag vid redigering av schemalagd uppdatering'
description: Använd patchen ACSD-48070 för att åtgärda Adobe Commerce-problemet där ett undantag utlöses när en schemalagd uppdatering redigeras.
feature: Catalog Management, Categories
role: Admin
exl-id: cebed18d-d213-4a5e-bc3b-8abcb52d45d0
source-git-commit: 011a6f46f76029eaf67f172b576e58dac9710a3d
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 0%

---

# ACSD-48070: Undantag vid redigering av schemalagd uppdatering

Korrigeringen ACSD-48070 åtgärdar ett problem där ett undantag utlöses när en schemalagd uppdatering redigeras. Den här korrigeringen är tillgänglig när [[!DNL Quality Patches Tool (QPT)]](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) 1.1.35 är installerad. Korrigerings-ID är ACSD-48070. Observera att problemet är planerat att åtgärdas i Adobe Commerce 2.4.7.

## Berörda produkter och versioner

**Korrigeringen har skapats för Adobe Commerce-version:**

* Adobe Commerce (alla distributionsmetoder) 2.4.4-p2

**Kompatibel med Adobe Commerce-versioner:**

* Adobe Commerce (alla distributionsmetoder) 2.3.7 - 2.4.6-p1

>[!NOTE]
>
>Korrigeringen kan bli tillämplig för andra versioner med nya [!DNL Quality Patches Tool]-versioner. Om du vill kontrollera om korrigeringen är kompatibel med din Adobe Commerce-version uppdaterar du `magento/quality-patches`-paketet till den senaste versionen och kontrollerar kompatibiliteten på [[!DNL Quality Patches Tool]: Sök efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html). Använd patch-ID:t som söknyckelord för att hitta patchen.

## Problem

Ett undantag utlöses när en schemalagd uppdatering redigeras.

<u>Steg som ska återskapas</u>:

1. Öppna en kategori.
2. Skapa en ny **[!UICONTROL Scheduled Update]** och spara den.
3. Klicka på **[!UICONTROL View/Edit]** i den skapade **[!UICONTROL Scheduled Update]**.
4. Spara den igen.

<u>Förväntade resultat</u>

**[!UICONTROL Scheduled Update]** sparas.

<u>Faktiska resultat</u>

Ett fel inträffar: *fel: : Ett fel uppstod när Magento\Catalog\Api\Data\CategoryInterface skulle sparas.*

## Tillämpa korrigeringen

Använd följande länkar beroende på distributionsmetod för att tillämpa enskilda korrigeringsfiler:

* Lokal användning för Adobe Commerce eller Magento Open Source: [[!DNL Quality Patches Tool] > Användning ](/help/tools/quality-patches-tool/usage.md) i guiden [!DNL Quality Patches Tool].
* Adobe Commerce om molninfrastruktur: [Uppgraderingar och korrigeringar > Tillämpa korrigeringar](https://experienceleague.adobe.com/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html) i Commerce om molninfrastruktur.

## Relaterad läsning

Mer information om [!DNL Quality Patches Tool] finns i:

* [[!DNL Quality Patches Tool] släppt: ett nytt verktyg för självbetjäning av kvalitetspatchar](https://experienceleague.adobe.com/en/docs/commerce-operations/tools/quality-patches-tool/quality-patches-tool-to-self-serve-quality-patches) i kunskapsbasen för support.
* [Kontrollera om det finns en korrigeringsfil för ditt Adobe Commerce-problem med  [!DNL Quality Patches Tool]](/help/tools/quality-patches-tool/patches-available-in-qpt/check-patch-for-magento-issue-with-magento-quality-patches.md) i guiden [!UICONTROL Quality Patches Tool].


Mer information om andra tillgängliga korrigeringsfiler i QPT finns i [[!DNL Quality Patches Tool]: Söka efter korrigeringsfiler ](https://experienceleague.adobe.com/tools/commerce-quality-patches/index.html) i [!DNL Quality Patches Tool]-handboken.
